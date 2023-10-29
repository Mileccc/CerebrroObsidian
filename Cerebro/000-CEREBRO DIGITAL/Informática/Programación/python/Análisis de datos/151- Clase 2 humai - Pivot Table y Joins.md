---
ID: 151
"tags:": 
"nombre:": Clase 2 humai - Pivot Table y Joins
---
___
# Clase 2 humai - Pivot Table y Joins
___
![](https://www.youtube.com/watch?v=xr00OfQn0JU&list=PLon--J7mANNWbXbGraiiMNWcv5T69kkAL&index=3)

___
# Pivot tables y joins

```python
import pandas as pd
import numpy as np
import matplotlib
import matplotlib.pyplot as plt
  
from IPython.display import Image
from IPython.core.display import HTML
  
plt.style.use('ggplot')
%matplotlib inline
```


## 1- Parámetros y extracción de datos

```python
# input

CASOS_URL = "https://sisa.msal.gov.ar/datos/descargas/covid-19/files/Covid19Casos.csv"
DETERMINACIONES_URL = "https://sisa.msal.gov.ar/datos/descargas/covid-19/files/Covid19Determinaciones.csv"
  
CASOS_URL_S3 = "https://datasets-humai.s3.amazonaws.com/datasets/covid_casos.zip"
DETERMINACIONES_URL_S3 = "https://datasets-humai.s3.amazonaws.com/datasets/covid_determinaciones.csv"
  
CASOS_PATH = "data/covid_casos.csv"
DETERMINACIONES_PATH = "data/covid_determinaciones.csv"
  
# output
PANEL_CASOS_PATH = "data/covid19-casos-panel.csv"
```

Si los sacamos de internet, podemos usar directamente la URL de cualquier CSV. Siempre es buena práctica guardar una copia por si en algún momento una URL deja de estar disponible.

```python
converters = {
    "residencia_provincia_id": lambda x: str(x).zfill(2),
    "departamento_provincia_id": lambda x: str(x).zfill(3),
    "codigo_indec_provincia": lambda x: str(x).zfill(2),
    "codigo_indec_departamento": lambda x: str(x).zfill(3),
}
  
# lee los datos de internet (original)
casos = pd.read_csv(CASOS_URL, converters=converters)
determinaciones = pd.read_csv(DETERMINACIONES_URL, converters=converters)
  
# lee los datos de internet (S3 de humai)
#casos = pd.read_csv(CASOS_URL_S3, converters=converters)
#determinaciones = pd.read_csv(DETERMINACIONES_URL_S3, converters=converters)
  
# guarda los datos localmente
#casos.to_csv(CASOS_PATH, encoding="utf8", index=False)
#determinaciones.to_csv(DETERMINACIONES_PATH, encoding="utf8", index=False)
  
# lee la copia local
#casos = pd.read_csv(CASOS_PATH, converters=converters)
#determinaciones = pd.read_csv(DETERMINACIONES_PATH, converters=converters)
```

## 2- Pivot table
[https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.pivot_table.html](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fpandas.pydata.org%2Fpandas-docs%2Fstable%2Freference%2Fapi%2Fpandas.pivot_table.html)

La función de `DataFrame.pivot_table` permite crear una tabla dinámica (de la misma forma que se podría hacer en una planilla de cálculo como Excel) fácilmente, eligiendo qué columnas se quieren mostrar en:

- **índice (index)**: lo que se usa para abrir los datos en filas.
- **columnas (columns)**: lo que se usa para abrir los datos en columnas.
- **valores (values)**: las variables que se quieren abrir en filas y columnas.

Y se puede elegir una o más funciones de agregación para aplicar a los valores cuando son agregados.

### 3.1- Contar casos a partir de un registro
**Casos**
En el dataset de **casos** nos enfrentamos a un **registro**: el dataset es una lista de casos, donde cada fila es un "caso". No tenemos columnas con variables agregadas, tenemos la materia prima sobre la cual se construyen las estadísticas o las agregaciones de cualquier tipo.

Las tablas dinámicas son una buena forma de agregar! En este caso la primera agregación obvia es _contar casos_. Tratemos de **contar la cantidad de casos de Covid por provincia**.

```python
casos.columns
```
$$Consola$$
![[Pasted image 20230910192009.png]]

```python
# busquemos las columnas que vamos a necesitar usar primero
casos.head()
```
$$Consola$$
![[Pasted image 20230910192052.png]]

```python
casos.residencia_provincia_nombre.unique()
```
$$Consola$$
![[Pasted image 20230910192139.png]]

```python
for col in casos.columns:
    if col.startswith("fecha"):
        print(col)
```
$$Consola$$
![[Pasted image 20230910192259.png]]


```python
casos.clasificacion_resumen.value_counts()
```
$$Consola$$
![[Pasted image 20230910192428.png]]

```python
casos_provincias = casos[casos.clasificacion_resumen == "Confirmado"].pivot_table(
    index=["residencia_provincia_nombre"],
    values=["id_evento_caso"],
    aggfunc="count"
)
casos_provincias.sort_values("id_evento_caso", ascending=False)
```
$$Consola$$
![[Pasted image 20230910192639.png]]

Primer reflejo que siempre tienes que tener: controlar el resultado con algún parámetro conocido (en lo posible). En este caso, tratemos de ver si la suma de casos tiene sentido o no.

```python
casos_provincias.id_evento_caso.sum()
```
$$Consola$$
![[Pasted image 20230910192803.png]]


En Google se muestra siempre el último dato reportado a la OMS, es un buen control

[https://www.google.com/search?q=casos+coronavirus+argentina&oq=casos+coronavirus&aqs=chrome.1.69i57j0l6j69i60.3332j0j7&sourceid=chrome&ie=UTF-8](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fwww.google.com%2Fsearch%3Fq%3Dcasos%2Bcoronavirus%2Bargentina%26oq%3Dcasos%2Bcoronavirus%26aqs%3Dchrome.1.69i57j0l6j69i60.3332j0j7%26sourceid%3Dchrome%26ie%3DUTF-8)

**Ejercicio:** crear una tabla contando la cantidad de casos fallecidos y controlarla. Pista: tienes que agregar un filtro más a la tabla anterior, que use la columna "fecha_fallecimiento".

```python
casos_provincias = casos[~casos.fecha_fallecimiento.isnull()].pivot_table(
    index=["residencia_provincia_nombre"],
    values=["id_evento_caso"],
    aggfunc="count"
)
  
casos_provincias.sort_values("id_evento_caso", ascending=False)
```
$$Consola$$
![[Pasted image 20230911202347.png]]


### 3.2- Crear un panel a partir de un registro
Una estructura muy común de dataset de **panel** tiene:

- 1 o más variables (generalmente numéricas)
- 1 dimensión de apertura temporal
- 1 o más dimensiones de apertura _no temporales_

Convertir registros en paneles, es un paso lógico en el procesamiento de datos primarios hacia la construcción de productos estadísticos o analíticos. Encapsula una parte del esfuerzo que conviene hacer bien de una sola vez, y luego utilizar el panel fácilmente para la mayoría de nuestras necesidades.

En este caso vamos a elegir cuáles son nuestras variables de interés para **construir el panel de casos de Covid**:

- provincia
- sexo
- fecha (tiene que haber una dimensión temporal)

```python
casos_panel = casos[casos.clasificacion_resumen == "Confirmado"].pivot_table(
    index=[
        "residencia_provincia_id",
        "residencia_provincia_nombre",
        "sexo",
        "fecha_diagnostico"
    ],
    values=["id_evento_caso"],
    aggfunc="count"
).reset_index()
casos_panel
```
$$Consola$$
![[Pasted image 20230911200035.png]]


Ahora realizar distintos gráficos es muy fácil! Sólo hay que hacer una tabla dinámica sobre nuestro panel eligiendo las variables.

```python
casos_evolucion_genero = casos_panel.pivot_table(
    columns="sexo",
    index="fecha_diagnostico",
    values="id_evento_caso",
    aggfunc="sum"
)
casos_evolucion_genero
```
$$Consola$$
![[Pasted image 20230911200253.png]]

```python
casos_evolucion_genero.plot(figsize=(15, 10))
```
$$Consola$$
![[Pasted image 20230911200339.png]]

**Ejercicio:** graficar la evolución de casos por provincia.

```python
casos_evolucion_provincia = casos_panel.pivot_table(
    columns="residencia_provincia_nombre",
    index="fecha_diagnostico",
    values="id_evento_caso",
    aggfunc="sum"
)
casos_evolucion_provincia
```
$$Consola$$
![[Pasted image 20230911203156.png]]

```python
casos_evolucion_provincia.plot(figsize=(15, 10))
```
$$Consola$$
![[Pasted image 20230911203215.png]]

___

## 3- Concat
[https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.concat.html](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fpandas.pydata.org%2Fpandas-docs%2Fstable%2Freference%2Fapi%2Fpandas.concat.html)

---

Pero ahora queremos graficar las curvas de casos confirmados y fallecidos, y nos damos cuenta de que a nuestro panel construido para trabajar le falta una nueva dimensión de apertura de la variable **casos**: el **estado** del caso.

Tenemos que agregar la variable **estado** a nuestro panel, con por lo menos dos estados: **confirmados** y **fallecios**. Para esto vamos a construir paneles **idénticos** para cada una de las variables y concatenarlos.

```python
casos_panel_confirmados = casos[casos.clasificacion_resumen == "Confirmado"].pivot_table(
    index=[
        "residencia_provincia_id",
        "residencia_provincia_nombre",
        "sexo",
        "fecha_diagnostico"
    ],
    values=["id_evento_caso"],
    aggfunc="count"
).reset_index()
casos_panel_confirmados.head()
```
$$Consola$$
![[Pasted image 20230911203750.png]]

Ahora armemos el panel de casos fallecidos con la misma estructura.

```python
casos_panel_fallecidos = casos[casos.clasificacion_resumen == "Confirmado"].pivot_table(
    index=[
        "residencia_provincia_id",
        "residencia_provincia_nombre",
        "sexo",
        "fecha_fallecimiento"
    ],
    values=["id_evento_caso"],
    aggfunc="count"
).reset_index()
casos_panel_fallecidos.head()
```
$$Consola$$
![[Pasted image 20230911203853.png]]


Y ahora necesitamos modificar ambos paneles para que tengan la misma estructura, y así poder concatenarlos.

- Agregar una columna para la dimensión "estado"
- Renombrar las columnas para que sigan teniendo sentido cuando sumemos información

```python
casos_panel_confirmados["estado"] = "confirmados"
casos_panel_confirmados = casos_panel_confirmados.rename(columns={
    "fecha_diagnostico": "fecha",
    "id_evento_caso": "casos"
})
casos_panel_confirmados.head()
```
$$Consola$$
![[Pasted image 20230911203948.png]]


```python
casos_panel_fallecidos["estado"] = "fallecidos"
casos_panel_fallecidos = casos_panel_fallecidos.rename(columns={
    "fecha_fallecimiento": "fecha",
    "id_evento_caso": "casos"
})
casos_panel_fallecidos.head()
```
$$Consola$$
![[Pasted image 20230911204144.png]]

Y ahora el momento de la verdad! Generemos un solo panel con todos los datos.

```python
casos_panel2 = pd.concat([casos_panel_confirmados, casos_panel_fallecidos])
casos_panel2
```
$$Consola$$
![[Pasted image 20230911204301.png]]

Ya podemos graficar fallecidos

```python
casos_evolucion_genero2 = casos_panel2[
    casos_panel2.estado == "fallecidos"
].pivot_table(
    columns="sexo",
    index="fecha",
    values="casos",
    aggfunc="sum"
)
casos_evolucion_genero2
```
$$Consola$$
![[Pasted image 20230911204349.png]]

```python
casos_evolucion_genero2.plot(figsize=(15,10))
```
$$Consola$$
![[Pasted image 20230911204500.png]]


**Ejercicio:** crear el panel `casos_panel_descartados` y concatenarlo a los otros dos generando un `casos_panel3`.

```python
casos_panel_descartados = casos[casos.clasificacion_resumen == "Descartado"].pivot_table(
    index=[
        "residencia_provincia_id",
        "residencia_provincia_nombre",
        "sexo",
        "fecha_inicio_sintomas"
    ],
    values=["id_evento_caso"],
    aggfunc="count"
).reset_index()
  
casos_panel_descartados.head()
```
$$Consola$$
![[Pasted image 20230913165503.png]]

```python
casos_panel_descartados["estado"] = "descartados"
casos_panel_descartados = casos_panel_descartados.rename(columns={
    "fecha_inicio_sintomas":"fecha",
    "id_evento_caso":"casos"
})
casos_panel_descartados.head()
```
$$Consola$$
![[Pasted image 20230913165539.png]]

```python
casos_panel3 = pd.concat([casos_panel_fallecidos,casos_panel_confirmados,casos_panel_descartados])

casos_panel3
```
$$Consola$$
![[Pasted image 20230913165613.png]]



____
## 4- STR
___
---

[https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.str.html](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fpandas.pydata.org%2Fpandas-docs%2Fstable%2Freference%2Fapi%2Fpandas.Series.str.html)

---

Todas las columnas (Series) de un data frame tienen diferentes métodos asociados que se pueden utilzar para hacer transformaciones rápidamente.

Hay un grupo de ellos accesible a través del atributo `str` (`Series.str`) que implementa las funciones usuales de Python sobre strings, para una columna de valores de texto.

### 5.1- .str.replace()

---

Si queremos graficar la evolución de casos por sexo, pero queremos una leyenda con la palabra completa, tal vez necesitemos reemplazar los valores usados en el dataset por otros.


```python
casos_panel2.head()
```
$$Consola$$
![[Pasted image 20230913154657.png]]


```python
casos_panel2["sexo"] = casos_panel2.sexo.str.replace(
    "F", "Femenino"
).replace(
    "M", "Masculino"
).replace(
    "NR", "No responde"
)
```

```python
casos_panel2.sexo.value_counts()
```
$$Consola$$
![[Pasted image 20230913154827.png]]


**Ejercicio:** modificar la columna `residencia_provincia_nombre` reemplazando "CABA" por "Ciudad Autónoma de Buenos Aires".

```python
casos_panel2["residencia_provincia_nombre"] = casos_panel2.residencia_provincia_nombre.str.replace(
    "CABA","Ciudad Autónoma de Buenos Aires")

casos_panel2.head()
```
$$Consola$$
![[Pasted image 20230913165927.png]]

### 5.2- .str.split()

Si queremos agrupar por mes, tal vez necesitamos partir la fecha en tres partes.

```python
casos_panel2.fecha.str.split("-")
```
$$Consola$$
![[Pasted image 20230913155442.png]]

Para poder asignar esas 3 partes a 3 columnas diferentes a la vez, debe agregarse otro `.str` al final.

```python
casos_panel2[["anio", "mes", "dia"]] = casos_panel2.fecha.str.split("-", expand=True)
```

```python
casos_panel2
```
$$Console$$
![[Pasted image 20230913160124.png]]


___
## 5- .map

Tal vez notaron lo impráctico que puede resultar el método `.str.replace()` cuando la lista de reemplazos sea larga. Para este caso existe el método `.map()`, al que se le puede pasar un diccionario con los reemplazos.

```python
casos_panel2["sexo"] = casos_panel2.sexo.map({
    "Masculino": "Masc",
    "Femenino": "Fem",
    "No responde": "Sin especificar"
})

casos_panel2.sexo.value_counts()
```
$$Consola$$
![[Pasted image 20230913160656.png]]

**Ejercicio:** modificar las categorías de la columna "estado" por "positivos" (en lugar de "confirmados"), "decesos" (en lugar de "fallecidos") y "negativos" (en lugar de "descartados").

```python
casos_panel2["estado"] = casos_panel2.estado.map({
    "confirmados":"positivos",
    "fallecidos":"decesos",
    "descartados":"negativos"
})
  
casos_panel2.estado.value_counts()
```
$$Consola$$
![[Pasted image 20230913161122.png]]

___
## 6- Merge
___
[https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.merge.html](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fpandas.pydata.org%2Fpandas-docs%2Fstable%2Freference%2Fapi%2Fpandas.DataFrame.merge.html)

---

"Mergear", "joinear" o cruzar dos datasets, implica elegir una o más columnas que estos tengan en común y utilizarlas para cruzar ambas tablas en base a la coincidencia de valores entre ambas. Existen varios tipos de _joins_ según cuál es el resultado que nos interesa obtener al final con el cruce:

- **left join**: preserva el 100% de las filas que tiene la tabla _de la izquierda_ del merge, y agrega las columnas del dataset _de la derecha_ con los valores (cuando hay una coincidencia) o las llena con valores nulos (cuando no hay coincidencia). Si el dataset de la derecha tiene valores para filas que no están presentes en el dataset de la izquierda, simplemente no se utilizan. El dataset resultado tiene la misma cantidad de filas que el dataset de la izquierda.
- **right join**: es igual que el anterior, pero se preservan las filas del dataset de la derecha en lugar de las del de la izquierda.
- **inner join**: sólo se mantienen aquellas filas que coinciden _en ambos datasets_. Si alguna fila no tiene coincidencia en uno de los dos, se descarta. El dataset final tiene igual cantidad o menos filas que el dataset más grande.
- **outer join**: se preservan todas las filas. Si hay coincidencia, se cruzan, y si no hay coincidencia se apilan llenando con valores nulos.

El tipo de join más común que van a utilizar la mayoría de las veces es el **left join**, cuyo caso de uso es "tengo una tabla, y quiero enriquecerla con nuevas columnas".

```python
Image(url= "https://datasets-humai.s3.amazonaws.com/datasets/joins.png")
```
$$Consola$$
![[Pasted image 20230913161438.png]]

Ahora, queremos calcular y graficar un indicador utilizado en algunos análisis que es la cantidad de testeos sobre la cantidad de casos confirmados.

Este indicador nos dice cuántos tests están siendo necesarios para identificar cada caso positivo de Covid. Para esto vamos a necesitar cruzar los datos de **determinaciones** con los de **casos**.

Hasta ahora nuestro panel tenía una sola variable! Pero ya es hora de que le agreguemos otra: `tests`.

```python
casos_panel2
```
$$Conasola$$
![[Pasted image 20230913171527.png]]


¿Cómo hacemos esto? Para cruzar (o "joinear") un dataset con otro, necesitamos definir un conjunto de columnas común por el cual hacerlo, esto a veces se llama **clave primaria** (o "primary key").

La clave primaria de una tabla es el conjunto de columnas necesarias para identificar a una sola fila de la tabla. Si miramos nuestro último panel, vemos que necesitamos las columnas **provincia**, **sexo**, **fecha** y **estado**

```python
determinaciones
```
$$Consola$$
![[Pasted image 20230913171552.png]]

Sin embargo el panel de "determinaciones" sólo comparte las columnas **fecha** y **provincia**, así que necesitamos generar dos paneles con esa clave primaria para poder cruzarlos.

```python
casos_confirmados_provincias = casos_panel2[
    casos_panel2.estado == "confirmados"
].pivot_table(
    index=["residencia_provincia_id", "fecha"],
    values="casos",
    aggfunc="sum"
).reset_index()
  
casos_confirmados_provincias
```
$$Consoala$$
![[Pasted image 20230913171730.png]]


Siempre recuerden controlar el resultado!

```python
casos_confirmados_provincias.casos.sum()
```
$$Consola$$
![[Pasted image 20230913172037.png]]

Ahora hacemos un panel de determinaciones con la misma estructura.

```python
determinaciones_panel = determinaciones.pivot_table(
    index=["codigo_indec_provincia", "fecha"],
    values="total",
    aggfunc="sum"
).reset_index()

determinaciones_panel
```

```python
determinaciones_panel.total.sum()
```
$$Consola$$
![[Pasted image 20230914194659.png]]

Llegó el momento del join! Recordemos que el objetivo es terminar con un solo panel, donde haya ahora dos variables: **casos** y **tests** ; con apertura por las dos dimensiones que comparten los datasets: **provincia** y **fecha**.

Para esto vamos a usar la función `DataFrame.merge()`.

```python
casos_tests = casos_confirmados_provincias.merge(
    determinaciones_panel,
    left_on=["residencia_provincia_id", "fecha"],
    right_on=["codigo_indec_provincia", "fecha"]
)
  
casos_tests
```
$$Consola$$
![[Pasted image 20230914195005.png]]

Bien! Noten que si la columna coincide en nombre, quedará una sola columna, pero si los nombres son diferentes tendremos una columna duplicada (que no queremos). Además deberíamos clarificar el nombre de la segunda variable.

```python
casos_tests = casos_tests.drop(
    columns=["codigo_indec_provincia"]
)
casos_tests
```
$$Consola$$
![[Pasted image 20230914195225.png]]

```python
casos_tests = casos_tests.rename(
    columns={"total": "tests"}
)
casos_tests
```
$$Consola$$
![[Pasted image 20230914195335.png]]

¿Por qué no usamos concat en lugar de merge, y agregamos una columna que se llame `variable` y tenga los valores "casos" y "tests"?

Esto también hubiera sido una estructura de panel posible, con sus ventajas y desventajas. Si tuviéramos una _gran cantidad_ de variables tal vez es mejor elegir esa estructura de dataset **más vertical**, pero si tenemos pocas, tal vez es mejor que cada variable sea una columna.

¿No son casos confirmados y casos fallecidos variables distintas también? Sí, podría pensarse así. Pero en este caso sí es más claro que se puede modelar como una variable **casos** con una dimensión de apertura que es el **estado** del caso.

---

Ahora queremos calcular una nueva variable: tests x caso confirmado.

```python
casos_tests["tests_por_confirmado"] = casos_tests.tests / casos_tests.casos

casos_tests
```
$$Consola$$
![[Pasted image 20230914195553.png]]

```python
casos_tests[
    casos_tests.residencia_provincia_id == "02"
].set_index(
    "fecha"
).tests_por_confirmado.plot(figsize=(15, 10))
```
$$Consola$$
![[Pasted image 20230914195823.png|1000]]

Esta variable puede tener variadas interpretaciones. ¿Qué significa si baja? ¿Se están haciendo los testeos focalizados en zonas con brotes? ¿Se necesitan hacer más tests para estar seguro de que se detecta la cantidad de casos necesarios para localizar los brotes?

Hay muchas interpretaciones posibles, y probablemente requieran de una interpretación más sofisticada. Se lo dejamos a los expertos!








___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%