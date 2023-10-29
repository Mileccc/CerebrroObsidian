---
ID: 150
"tags:": 
"nombre:": Clase 1 humai - Introducción Pandas
---
___
# Clase 1 humai - Introducción Pandas
![](https://youtu.be/grBT_YZXHwU?t=600)

___
![](https://youtu.be/9cdoAWr8Lzs?si=pze62O777QxCPjvB&t=3218)
___
## Exploración

Vamos a analizar datos de una fuente real. Los ingresos de los funcionarios son información pública que se libera anualmente en el [portal de datos abiertos](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fdata.buenosaires.gob.ar%2Fdataset%2Fsueldo-funcionarios) de GCBA.

En general los 4 primeros pasos para analizar un data set son:

1. Leerlo
2. Consultar cuáles son las columnas
3. Extraer una muestra
4. Verificar cuántos registros tiene

## 1- Para leer el data set usamos la función de pandas read_csv

Con esta función podemos leer archivos que estén en una url pública o en una ubicación del disco accesible desde la Jupyter Notebook.

```python
df = pd.read_csv('http://cdn.buenosaires.gob.ar/datosabiertos/datasets/sueldo-funcionarios/sueldo_funcionarios_2019.csv')
```

## 2- Consultamos las columnas
```python
df.columns
```
$$Consola$$
![[Pasted image 20230903222501.png]]

## 3- Extraemos una muestra
```python
df.sample(3)
```
$$Consola$$
![[Pasted image 20230903222617.png]]

## 4- Consultamos la cantidad de filas y de columnas
```python
df.shape
```
$$Consola$$
![[Pasted image 20230903222724.png]]

___
## 5- Vectorización con Pandas
Pandas es una de las librerías de Python más usadas para análisis de datos. El nombre pandas viene de "Panel Data Analysis" y su funcionalidad permite hacer operaciones sobre datos que se encuentran en memoria de manera eficiente.

Pandas es útil para trabajar sobre datos tabulares, con dos condiciones importantes:

I. Los datos se encuentran enteramente en la memoria RAM. Con lo cual, el tamaño de los datos que podemos manipular está limitado por el hardware. Como regla de pulgar, es una buena práctica no ocupar más de 1/3 de la memoria RAM de nuestro dispositivo con el dataset. Así, si estamos trabajando localmente en una notebook con 8GB de memoria RAM no es recomendable procesar datasets de más de 2.33GB.

II. En pandas, las operaciones sobre filas y columnas son, en general, eficientes porque se hacen de forma "vectorizada". En realidad esta optimización, se hace desde numpy, una librería para realizar operaciones matemáticas que se utilizó a su vez para escribir pandas.

Las operaciones vectorizadas son las que se realizan en bloque en vez de caso por caso. Las computadoras de hoy tienen la capacidad de recibir muchas instrucciones juntas y procesar varias de ellas a la vez. Por ejemplo, si nuestro hardware tiene la capacidad de procesar 4 operaciones juntas, el resultado de vectorizar una operación matemática es el siguiente:

![[vectorizacion.png]]

En el primer caso hay que hacer 5 operaciones y en el segundo caso sólo dos.

Es importante entender, entonces, que Pandas trabaja de esta manera y que por eso es una de las herramientas más elegidas para manipular datos en memoria.

```python
df["aguinaldo_porcentaje"] = df["aguinaldo_ii"]*100/df["asignacion_por_cargo_i"]
df.tail() # Alternativa a head() , en vez de mostrar los primeros registros muestra los ultimos
```
$$Consola$$
![[Pasted image 20230910182911.png]]

___
## 6- Los objetos fundamentales de Pandas

### Series

Las series son "columnas"  de una tabla que están asociadas a un índice y a un nombre. Igual que una lista común de Python es una secuencia de elementos ordenados, pero a diferencia de la lista está asociada a más información.

```python
# Las series se pueden crear a partir de una lista
serie = pd.Series(['a','b','c'], name="nombre de la columna")
```

```python
serie
```
$$Consola$$
![[Pasted image 20230903224005.png]]

```python
# Propiedades importantes de las series
print('Tipo de objetos que tiene ', serie.dtype)
print('Nombre ', serie.name)
print('Index ',serie.index)
print('Valores ',serie.values)
```
$$Consola$$
![[Pasted image 20230903224104.png]]

## DataFrames

Los DataFrames son "tablas", compuestas por varias "columnas" o series que comparten todas un mismo índice. En general los DataFrames se crean a partir de leer tablas de archivos (pueden ser en formato json o csv) pero a veces también se crean a partir de listas de diccionarios o de otras maneras.

Los DataFrames tienen un objeto Index que describe los nombres de columnas y otro objeto Index que describen los nombres de las filas.

```python
# Leemos un dataset público
df = pd.read_csv('http://cdn.buenosaires.gob.ar/datosabiertos/datasets/sueldo-funcionarios/sueldo_funcionarios_2019.csv')
```

Si importamos un DataFrame y no se están bien separados los datos podemos usar un separador para forzar la separación

```python
df = pd.read_csv('http://cdn.buenosaires.gob.ar/datosabiertos/datasets/sueldo-funcionarios/sueldo_funcionarios_2019.csv', sep="|")
```


```python
# Propiedades importantes de los dataframes
print('Columnas ', df.columns)
print('Index ', df.index)
print('Dimensiones ',df.shape)
```
$$Consola$$
![[Pasted image 20230903223202.png]]

```python
# Consultar las primeras filas
df.head()
```
$$Consola$$
![[Pasted image 20230903223308.png]]

Si queremos extraer una serie del DataFrame, podemos hacerlo de la misma forma en que extraemos un valor de un diccionario.

```python
serie_mes = df['mes']
```

```python
type(serie_mes)
```
$$Consola$$
![[Pasted image 20230903223420.png]]

## Índices
Los índices acompañan a las series y a los Data Frames. Son conjuntos ordenados e inmutables de elementos

```python
df.index
```
$$Consola$$
![[Pasted image 20230903223541.png]]

```python
df.columns
```
$$Consola$$
![[Pasted image 20230903223620.png]]

```python
ind = pd.Index([2, 3, 5, 7, 11])
ind
```
$$Consola$$
![[Pasted image 20230903223706.png]]


___
## 7- Filtrando un DataFrame (Indexing)
Hay muchas técnicas para filtrar un DataFrame. Podemos querer filtrar por columnas o por filas, por posición o por nombre. También podemos querer filtrar por condiciones que se cumplen o no. Cuando no queremos filtrar sobre una dimensión (filas o columnas) usamos ":" para seleccionar todo.

![[indexing.png]]

### .iloc
Selección basada en la posición
```python
df.iloc[0,0]
```
$$Consola$$
![[Pasted image 20230903225414.png]]

```python
df.iloc[0,:]
```
$$Consola$$
![[Pasted image 20230903225447.png]]

```python
df.iloc[:,0]
```
$$Consola$$
![[Pasted image 20230903225514.png]]

### .loc
Selección basado en el nombre de las columnas

```python
df.loc[:,["funcionario_nombre"]]
```
$$Consola$$
![[Pasted image 20230903225943.png]]

___
## Boolean Indexing
Supongamos que queremos tomar el dataset de funcionarios y quedarnos únicamente con los que pertenecen al Ministerio de Cultura. Para eso lo que hacemos es indexar al DataFrame por una condición booleana. Eso implica que debemos crear una serie compuesta por valores True y False para aplicarla como índice a las filas.

  
Los operadores que sirven para evaluar condiciones sobre las series son:

![[Pasted image 20230903230126.png|600]]

#### Máscara booleana

Veamos lo que pasa cuando le aplicamos a una serie una condición que devuelve un booleano

```PYTHON
df['reparticion'] == "Jefe de Gobierno"
```
$$Consola$$
![[Pasted image 20230903231024.png]]

```python
df[df["reparticion"] == "Jefe de Gobierno"]
```
$$Consola$$
![[Pasted image 20230903231137.png]]

```python
mascara_booleana = df['reparticion'] == "Jefe de Gobierno"
```

Nos devuelve una serie de la misma longitud que la original y que contiene sólo valores True o False.

```python
type(mascara_booleana)
```
$$Consola$$
![[Pasted image 20230903230514.png]]

```python
mascara_booleana.shape
```
$$Consola$$
![[Pasted image 20230903231415.png]]

```python
mascara_booleana.dtype
```
$$Consola$$
![[Pasted image 20230903231456.png]]

Ahora seleccionemos entonces, los registros que corresponden al Ministerio de Cultura.

```python
df_min_cul = df.loc[df['reparticion'] == 'Ministerio de Cultura',:]
```

```python
# Veamos la cantidad de casos
df_min_cul.shape
```
$$Consola$$
![[Pasted image 20230903231552.png]]

Algo que puede llegar a confundir sobre el Indexing en Pandas es que en algunos casos se puede ser menos explícito a la hora de filtrar. Por ejemplo si ponemos una condición Booleana, pandas asume que el tipo de indexing es loc y que el filtro es sobre las filas y no sobre las columnas:

```python
df_min_cul = df[df['reparticion'] == 'Ministerio de Cultura']
```

```python
df_min_cul.shape
```
$$Consola$$
![[Pasted image 20230903231732.png]]


___
#### Máscara booleana con muchas condiciones
Ahora tratemos de filtrar el dataset por dos condiciones: por ejemplo tomar los sueldos de abril de la secretaria de innovación. Para eso tenemos que combinar dos máscaras booleanas con una condición.

![[Pasted image 20230905072934.png|500]]

***Ejemplo***: seleccionemos los casos donde o bien se haya cobrado aguinaldo o bien el salario total haya sido mayor que 240.000, pero no las dos cosas.

```python
df[(df['total_salario_bruto_i_+_ii'] > 240000) ^ (df['aguinaldo_ii'] > 0)]
```
$$Consola$$
![[Pasted image 20230905073550.png]]

***Ejemplo:*** Ahora veamos los sueldos de febrero de la SECR Ciencia, Tecnología e Innovación.

```python
df[(df['mes'] == 2) & (df['reparticion'] == 'SECR Ciencia, Tecnologia e Innovacion')]
```
$$Consola$$
![[Pasted image 20230905074302.png]]


#### Boolean indexing con query()
La sintaxis que se utiliza para hacer Boolean indexing es un poco repetitiva. Noten que filtrar (aún en su expresión más corta sin loc ni especificar filas o columnas) implica ESCRIBIR DOS VECES el nombre del dataset. Para crear un shortcut, Pandas ofrece la función .query()

```python
df_cult = df.query('reparticion == "Ministerio de Cultura"')
df_cult
```
$$Consola$$
![[Pasted image 20230905074640.png]]

También se puede hacer query sobre múltiples condiciones.

```python
df2 = df.query('asignacion_por_cargo_i > 240000 & aguinaldo_ii > 0')
```
$$Consola$$
![[Pasted image 20230905074949.png]]


```python
df2.shape
```
$$Consola$$
![[Pasted image 20230905075007.png]]

#### Ejercicio: Piensen cómo traducir a la sintaxis de query, estas consultas que ya hicimos:

```python
# df_sem2 = df[df['mes'] > 6]
df_sem2 = df.query("mes > 6")
df_sem2
```
$$Consola$$
![[Pasted image 20230905080059.png]]

```python
# df[(df['mes'] == 2) & (df['reparticion'] == 'SECR Ciencia, Tecnologia e Innovacion')]
df.query("mes == 2 & reparticion == 'SECR Ciencia, Tecnologia e Innovacion'")
```
$$Consola$$
![[Pasted image 20230905080146.png]]

#### Fancy Indexing
Ahora vamos a quedarnos con un subconjunto de columnas del DataFrame.

```python
df_view = df.loc[:,['anio','mes']]
df_view
```
$$Consola$$
![[Pasted image 20230905080326.png]]

```python
df_view.shape
```
$$onsola$$
![[Pasted image 20230905080409.png]]

Fíjense lo que pasa si tratamos de acceder a filas utilizando una lista de nombres, en este caso [0,1].

```python
# Incorrecto
df_view = df[[3,8]]
```
$$Consola$$
![[Pasted image 20230905080512.png]]

Nos da un error porque cuando pasamos únicamente una lista al indexing, pandas asume que queremos un set de columnas y si los nombres no existen, da error. La forma correcta de hacerlo es pasar una lista de índices y explicitar que vamos a indizar con loc y que seleccionamos todas las columnas.

```python
# Correcto
df_view = df.loc[[3,8],:]
df_view
```
$$Consola$$
![[Pasted image 20230905080633.png]]


## 8- Funciones de Agregación
Utilizando Pandas podemos aplicar funciones a nivel de columna. Algunas funciones predefinidas son la media, el desvío estándar y la sumatoria, el valor máximo y el mínimo.

Algunas de las funciones de agregación más comunes son:

- min
- max
- count
- sum
- prod
- mean
- median
- mode
- std
- var

```python
df['mes'].max()
```
$$Consola$$
![[Pasted image 20230905081039.png]]


```python
df['asignacion_por_cargo_i'].mean()
```
$$Consola$$
![[Pasted image 20230905081047.png]]

```python
df['asignacion_por_cargo_i'].std()
```
$$Consola$$
![[Pasted image 20230905081056.png]]


```python
df['total_salario_bruto_i_+_ii'].sum()
```
$$Consola$$
![[Pasted image 20230905081104.png]]

Podemos combinar los filtros que vimos antes con las funciones de agregación para responder preguntas cómo _¿Cuál fue en gasto en asignaciones de funcionarios para la Secretaría de Medios 2019? ¿Y para la de Justicia y Seguridad?_


```python
df[df['reparticion'] == 'SECR de Medios']['total_salario_bruto_i_+_ii'].sum()
```
$$Consola$$
![[Pasted image 20230905081316.png]]


```python
df[df['reparticion'] == 'SECR Justicia y Seguridad']['total_salario_bruto_i_+_ii'].sum()
```
$$Consola$$
![[Pasted image 20230905081325.png]]


Ahora respondamos algunas preguntas: _¿Quién o quiénes del dataset cobran el salario más alto? ¿Y el más bajo?_

```python
df[df['total_salario_bruto_i_+_ii'] == df['total_salario_bruto_i_+_ii'].max()]
```
$$Consola$$
![[Pasted image 20230905081443.png]]



```python
df[df['total_salario_bruto_i_+_ii'] == df['total_salario_bruto_i_+_ii'].min()]
```
$$Consola$$
![[Pasted image 20230905081457.png]]


## 9- Otros análisis descriptivos

Pandas viene con algunas funciones built-in para ayudar al análisis descriptivo.

#### Para las variables numéricas

```python
df.describe()
```
$$Consola$$
![[Pasted image 20230905081620.png]]



#### Para las variables categóricas

```python
df['reparticion'].value_counts()
```
$$Consola$$
![[Pasted image 20230905081833.png]]

## 10- Ordenar por columnas y limitar la cantidad de resultados

Otra forma de resolver el problema de encontrar el mayor y el menor es con el método _sort_values_. Este método puede recibir un valor único (nombre de columna) o una lista (con varias columnas) y un orden _asc_ o _desc_. Por default el orden es asc.

Si combinamos el ordenamiento con el método _head()_ para limitar la cantidad de resultados, podemos encontrar los N primeros.

```python
# Recordemos cómo abrir la documentación de un método
df.sort_values?
```
$$Consola$$
![[Pasted image 20230905082247.png]]



```python
# Ordenamos la cabecera de mayor a menor y seleccionamos solo el primero
df.sort_values('total_salario_bruto_i_+_ii',ascending=False).head(1)
```
$$Consola$$
![[Pasted image 20230905082336.png]]



```python
# Calculamos el mínimo
df.sort_values('total_salario_bruto_i_+_ii').head(1)
```
$$Consola$$
![[Pasted image 20230905082459.png]]


## Anexo: volviendo al tema de la vectorización

¿Por qué es tan importante trabajar con Pandas y no con funciones escritas por nosotros en Python nativo y que procesen los datos dentro de un for loop?

Por un lado está la comodidad. Hay mucha funcionalidad que ya está desarrollada en Pandas. Existen funciones que resuelven muchos de los problemas clásicos de manipular datos: agrupar, sumarizar, sacar estadísticas, filtrar, etc. Pero además hay una razón de performance.

Veamos una demostración de que vectorizar es más eficiente. Vamos a crear dos listas de 1.000.000 de números aleatorios cada una y vamos a tratar de multiplicar elemento por elemento con pandas y sin pandas:


```python
lista1 = list(np.random.randint(1, 100, 1000000))
lista2 = list(np.random.randint(1, 100, 1000000))
```
$$Consola$$




```python
%%timeit
for x,y in zip(lista1,lista2):
    x * y
```
$$Consola$$
![[Pasted image 20230905082614.png]]




```python
serie1 = pd.Series(lista1)
serie2 = pd.Series(lista2)
```
$$Consola$$

Ahora probemos hacer lo mismo con dos series de Pandas

```python
%%timeit
resultado = serie1 * serie2
```
$$Consola$$
![[Pasted image 20230905082621.png]]

Conclusión: la operación vectorizada es **más de 70 veces más rápida.**

```
%%timeit  ---> más precisa
%%time    ---> Aporta más información
```














___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:  [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%