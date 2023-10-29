---
ID: 152
"tags:": 
"nombre:": Clase 3 humai - Agrupación y Agregación
---
___
# Clase 3 humai - Agrupación y Agregación
___
![](https://www.youtube.com/watch?v=NFERQ_bCfHw&list=PLon--J7mANNWbXbGraiiMNWcv5T69kkAL&index=3)

___
## 1- Introducción
En esta clase vamos a ver cómo agrupar datos a partir de una clave para trabajar sobre distintos grupos. El primer dataset que vamos a utilizar es del portal de datos abiertos de España. Los datos se pueden encontrar [aquí](https://colab.research.google.com/corgiredirector?site=http%3A%2F%2Fopendata.esri.es%2Fdatasets%2Fparo-por-municipio-espa%25C3%25B1a%2Fgeoservice) y la única modificación que se les hizo fue reemplazar el código de provincia por la descripción de la misma

```python
! pip install plotly
```

```python
import pandas as pd
import plotly.express as px
```

```python
df = pd.read_csv('https://datasets-humai.s3.amazonaws.com/datasets/parodesprov.csv')
```

```python
df.sort_values('Codigo').head(6)
```
![[Pasted image 20230914201658.png]]

Noten que en este conjunto de datos, al parecer la base está duplicada. Los municipios figuran dos veces, una vez con el código de provincia en NaN y otra vez con el código de provincia informado. Los valores de paro y población son muy cercanos en todos los casos, así que podemos considerarlas cercanas en el tiempo.

```python
df = df[df['PAD_1_COD_PROV'].notnull()].copy()

df.sort_values('Codigo').head(6)
```
$$Consola$$
![[Pasted image 20230914201943.png]]

## 2- Niveles de Agregación
Además de los municipios (identificados por la variable Código), tenemos dos niveles de agregación geográfica, la provincia (Cod_Prov) y la comunidad autónoma (Cod_CAA).

Veamos qué valores toman y cómo se combinan.

```python
# ¿Cuántos municipios tiene cada comunidad? ¿Hay alguno que no tenga CCAA asociada?
df['Cod_CCAA'].value_counts(dropna=False)
```
$$Consola$$
![[Pasted image 20230914202123.png]]

```python
# ¿Cuántas CCAA hay?
len(df['Cod_CCAA'].unique())
```
$$Consola$$
![[Pasted image 20230914202227.png]]


```python
# ¿Cuántos municipios tiene cada provincia? ¿Hay alguno que no tenga provincia asociada?
df['Cod_Prov'].value_counts(dropna=False)
```
$$Consola$$
![[Pasted image 20230914202411.png]]


```python
# ¿Cuántas provincias hay?
len(df['Cod_Prov'].unique())
```
$$Consola$$
![[Pasted image 20230914202454.png]]


```python
# ¿Hay alguna provincia que tenga más de una CCAA asociada?
df[['Cod_CCAA','Cod_Prov']].drop_duplicates().sort_values('Cod_Prov')
```
$$Consola$$
![[Pasted image 20230914202607.png]]


## 3- Buscando valores nulos

Ahora queremos filtrar todas las filas del DataFrame que contengan algún valor nulo, para analizar en detalle por qué existe ese valor faltante y si vamos a querer completarlo o descartarlo.

El método ``df.isnull()`` devuelve un DataFrame del mismo tamaño que el original, pero en lugar de los valores devuelve True si había un NaN y False si no lo había.

```python
df.isnull().head(3)
```
$$Consola$$
![[Pasted image 20230914202758.png]]

#### Entendiendo el parámetro axis

A continuación vamos a reducir el DataFrame de más arriba a una serie, compuesta por Booleans que indican True si hay algún valor nulo en la fila y False si no hay ninguno. La forma de reducir una serie de Booleanos es ``any()`` y el parámetro ``axis = 1`` indica que queremos reducir el DataFrame aplicando la función de manera horizontal, probando todos los valores del eje y.

```python
df[df.isnull().any(axis=1)]
```
$$Consola$$
![[Pasted image 20230914203030.png]]

Otro posible método para reucir es all así que una forma equivalente de lograr lo mismo es:

```python
df[~(df.notnull().all(axis=1))]
```
$$Consola$$
![[Pasted image 20230914203143.png]]

¿Qué significará un TotalParoRegistrado nulo? :thinking: ¿Será equivalente a un paro de 0, algo que es posible que se de?

```python
df[df['TotalParoRegistrado'] == 0].sample(3)
```
$$Consola$$
![[Pasted image 20230914203304.png]]

Podríamos concluir que no, porque los municipios con paro igual a 0, informan 0. Entonces deberíamos descartar el dato.

#### Entendiendo el parámetro inplace

Noten que la mayor parte de los métodos que trabajan sobre DataFrames devuelven objetos nuevos que si no los almacenamos en una variable se pierden. Cuando queremos que el DataFrame cambie a partir de una determinada acción usamos el parámetro ``inplace=True``.

```python
df.dropna(inplace=True)
```

```python
df[~(df.notnull().all(axis=1))]
```
$$Consola$$
![[Pasted image 20230914203528.png]]

### Crear columnas

Contamos con los cambios de población de cada municipio ('PAD_1C02') y también con el área ('Shape__Area'). Con estas columnas podemos formar la densidad.

```python
# ¡Operación vectorizada!
df['Densidad'] = df['PAD_1C02'] / df['Shape__Area']
```

También sabemos la cantidad de personas desempleadas y con eso podemos formar la proporción de paro.

```python
df['Proporcion_Paro'] =  df['TotalParoRegistrado'] / df['PAD_1C02']
```

```python
df.head(6)
```
$$Consola$$
![[Pasted image 20230914203853.png]]

## 4- Funciones de Agregación simple

![[Pasted image 20230914203921.png]]

Vamos a comprobar que la población total coincida (aproximadamente) con la [población de España.](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fwww.google.com%2Fsearch%3Fclient%3Dfirefox-b-e%26q%3Dpoblacion%2Bespana)

```python
df['PAD_1C02'].sum()
```
$$Consola$$
![[Pasted image 20230915221637.png]]

¿Cuál es el promedio de proporción de paro en las autonomías de España?

```python
df['Proporcion_Paro'].mean()
```
$$Consola$$
![[Pasted image 20230915221741.png]]

Ejercicio: ¿Cuántas autonomías están por encima de la media y cuántas están por debajo?

```python
proporcion_paro_media = df["Proporcion_Paro"].mean()
df[df['Proporcion_Paro'] > proporcion_paro_media]
```
$$Consola$$
![[Pasted image 20230915223559.png]]

```python
df[df['Proporcion_Paro'] < proporcion_paro_media]
```
$$Consola$$
![[Pasted image 20230915223632.png]]

¿Cuál es la mediana?
```python
df['Proporcion_Paro'].median()
```
$$Consola$$
![[Pasted image 20230915223738.png]]


Que la mediana sea menor a la media, significa que hay algunos valores llamativamente altos. Veamos un gráfico para ver la distribución de esta variable.

```python
fig = px.histogram(df, x="Proporcion_Paro")
fig.show()
```
$$Consola$$
![[Pasted image 20230915224506.png]]

Y en cuanto al tamaño, ¿Cuál es la mediana de tamaño en las autonomías?

```python
mediana_area = df['Shape__Area'].median()
mediana_area
```
$$Consola$$
![[Pasted image 20230915224619.png]]

Si dividimos a las autonomías entre "grandes" (con un área mayor que la mediana) y "chicas" (con un área menor), ¿Cuál grupo tiene mayor proporción de paro?

```python
df.query('Shape__Area > @mediana_area')['Proporcion_Paro'].mean()
```
$$Consola$$
![[Pasted image 20230915224803.png]]

```python
df.query('Shape__Area < @mediana_area')['Proporcion_Paro'].mean()
```
$$Consola$$
![[Pasted image 20230915224827.png]]

Entonces, mientras que en autonomías más grandes la proporción de paro es 6.5%, en las más chicas es de 5.4%.

Ejercicio: calculen cómo es esta relación con respecto a la densidad.

```python
mediana_densidad = df["Densidad"].median()
mediana_densidad
```
$$Consola$$
![[Pasted image 20230915225758.png]]

```python
df.query("Densidad < @mediana_densidad")["Proporcion_Paro"].mean()
```
$$Consola$$
![[Pasted image 20230915225808.png]]

```python
df.query("Densidad > @mediana_densidad")["Proporcion_Paro"].mean()
```
$$Consola$$
![[Pasted image 20230915225819.png]]


## 5- Group By: Trabajando sobre grupos
Muchas veces necesitamos analizar métricas, pero sobre agrupamientos de los datos. Por ejemplo, las autonomías se agrupan en provincias y podemos querer ver el desempeño de cada provincia. O en lugar de analizar la densidad separando únicamente por la mediana, podemos querer ver qué pasa en cada percentil.

En Pandas las ope![[splitapplycombine.png]]raciones sobre grupos se pueden ver como una combinación de las operaciones Split Apply Combine.

![[splitapplycombine.png|900]]

En algunos casos la operación que aplicamos sobre el dataframe original reduce el tamaño del mismo, por ejemplo cuando devolvemos la media de cada grupo y otras veces no, por ejemplo cuando comparamos cada elemento del grupo contra un benchmark del mismo, por ejemplo si quisiéramos hacer un ranking por juego para grupos de jugadores.

## 6- Clases que se encargan de la Agregación en Pandas

### DataSetGroupBy

Veamos qué devuelve pandas cuando agrupamos un dataset por una columna:

```python
df.groupby('PAD_1_COD_PROV')
```
$$Conosla$$
![[Pasted image 20230915230153.png]]

```python
df.groupby('PAD_1_COD_PROV')['Shape__Area']
```
$$Conosla$$
![[Pasted image 20230915230234.png]]

En lugar de recibir una lista o numpy array de grupos, recibimos un objeto del tipo DataFrameGroupBy. Ahora veamos cuánto tarda en ejecutarse este método.

### Lazy Evaluation

```python
%%timeit
df.groupby('PAD_1_COD_PROV')
```
$$Consola$$
![[Pasted image 20230915230535.png]]

```python
%%timeit
a = list(df.groupby('PAD_1_COD_PROV'))
```
$$Consola$$
![[Pasted image 20230915230542.png]]

Hacer únicamente la agrupación por código de provincia lleva 50 microsegundos pero si convertimos el resultado a una lista, forzamos a que efectivamente se separen los grupos y eso tarda 10.9 ms.

Este comportamiento se llama "lazy evaluation" y es muy importante en todos los motores de procesamiento de datos. Ejecutar las operaciones computacionalmente pesadas, sólo cuando se necesita permite hacer los procesos más eficientes.

```python
a = list(df.groupby('PAD_1_COD_PROV'))
type(a[0])
```
$$Consola$$
![[Pasted image 20230915230723.png]]


```python
type(a[0][0])
```
$$Consola$$
![[Pasted image 20230915230727.png]]


```python
type(a[0][1])
```
$$Consola$$
![[Pasted image 20230915230733.png]]

### Iterar sobre los grupos

Podemos recorrer los grupos en un loop for, desempaquetando la tupla que contiene el nombre del grupo y el DataFrame correspondiente.

Veamos a ver cuántas autonomías tiene cada provincia.

```python
for (cod_prov, group) in df.groupby('PAD_1_COD_PROV'):
    print("provincia={0}, tamaño={1}".format(cod_prov, group.shape[0]))
```
$$Consola$$
![[Pasted image 20230915230932.png]]


## 7- SeriesGroupBy
Veamos el tipo de objeto que se forma cuando tomamos una serie del DataFrame.

```python
type(df.groupby('PAD_1_COD_PROV')['Proporcion_Paro'])
```
$$Consola$$
![[Pasted image 20230915231156.png]]

Es un objeto de tipo SeriesGroupBy. A estos objetos, podemos aplicarles cualquier función de agregación.

```python
%%time
df.groupby('PAD_1_COD_PROV')['Proporcion_Paro'].mean()
```
$$Consola$$
![[Pasted image 20230915231311.png]]

Noten que en este caso, la operación sobre el objeto SeriesGroupBy tarda (en este caso, va a depender del hardware) casi 15 veces que el loop for sobre el GroupBy. Esto es gracias a la vectorización que vimos en la clase 1.

```python
a = df.groupby('PAD_1_COD_PROV')['Proporcion_Paro'].mean()
```


```python
# El resultado de una función de agregación sobre una SeriesGroupBy, es otra serie
type(a)
```
$$Consola$$
![[Pasted image 20230915231456.png]]

```python
# El índice de la serie son todas las provincias.
a.index
```
$$Consola$$
![[Pasted image 20230915231521.png]]

Ahora podemos probar otras funciones de agregación, por ejemplo calculemos el área por provincia:

```python
df.groupby('PAD_1_COD_PROV')['Shape__Area'].sum()
```
$$Consola$$
![[Pasted image 20230915231639.png]]

## 8- Agregaciones múltiples

Veamos ahora quiero combinar para cada provincia, cuál es el área, cuál es la población, cuál es la media y la mediana de paro y cuántas autonomías la componen. Para esto existe la función aggregate. Aplicada sobre un DataFrameGroupBy recibe como parámetro un diccionario con las nombres de columnas como claves y el tipo de agregación a realizar como valores. Pueden ser valores únicos o listas con varios valores.

```python
df.groupby('PAD_1_COD_PROV').aggregate({'Shape__Area':'sum',
                                        'PAD_1C02':'sum',
                                        'Proporcion_Paro':['mean','median','size']}).head()
```
$$Consola$$
![[Pasted image 20230915231754.png]]

## 9- MultiIndex
 
```python
df_agregado.columns
```
$$Consola$$


#### Entendiendo la función pd.qcut

También podemos agrupar por más de una columna, usando una lista en lugar de un único valor como parámetro del groupby.

Calculemos los deciles de paro registrado en los distintos municipios. Para eso vamos a construir una columna que contenga el decil que ocupa el municipio en el ranking de proporción de paro. El decil 1 va a representar las autonomías que mejor se desempeñan y el decil 10 las que peor lo hacen.

```python
df['Decil_Paro'] = pd.qcut(df['Proporcion_Paro'], 10, labels=range(1,11))
```


Ahora podemos agrupar por provincia y decil para ver cuántos municipios de cada decil hay en cada provincia.

```python
serie_prov_decil = df.groupby(['PAD_1_COD_PROV','Decil_Paro']).size()
```

```python
type(serie_prov_decil)
```
$$Consola$$
![[Pasted image 20230915232221.png]]

```python
serie_prov_decil.index
```
$$Consola$$
![[Pasted image 20230915232252.png]]

```python
serie_prov_decil.head(10)
```
$$Consola$$
![[Pasted image 20230915232321.png]]

El objeto MultiIndex puede ser complicado para trabajar. Por eso conviene utilizar el método reset_index() para volver a un DataFrame común.

```python
df_prov = serie_prov_decil.reset_index()
```

```python
df_prov.head()
```
$$Consola$$
![[Pasted image 20230915232440.png]]

### Ejercicios

Ahora vamos a querer trabajar a nivel de provincia. Calculen la densidad, la proporción de paro y la cantidad de municipios para cada provincia ¿Cuál es la provincia con mayor proporción de paro? ¿Cuál es la que tiene menos?

```python
df.groupby('PAD_1_COD_PROV').aggregate({
    'Densidad':'mean',
    'Codigo':'count',
    'Proporcion_Paro':"mean"
    }).head()
```
$$Consola$$
![[Pasted image 20230916203750.png]]





























___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%