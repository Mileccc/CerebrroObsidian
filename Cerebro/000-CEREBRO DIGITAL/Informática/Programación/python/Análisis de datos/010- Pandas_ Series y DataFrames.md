---
ID:: 010
tags::  #programación #paganálisis_de_datos #python  #análisis_de_datos
nombre:: "Pandas_ Series y DataFrames"
---
___
# Pandas_ Series y DataFrames
___
```python
import pandas as pd
```
Pandas es una biblioteca de Python ampliamente utilizada para el análisis y manipulación de datos. Esta herramienta es esencial para cualquier persona que trabaje con datos, ya sea para la limpieza, exploración, transformación o análisis de información tabular. Pandas proporciona estructuras de datos eficientes y flexibles, principalmente dos tipos: ``Series`` y ``DataFrames``.

## Series
Una Serie es una estructura de datos unidimensional que puede contener cualquier tipo de datos, como números, cadenas de texto, fechas, etc. Cada elemento en una Serie tiene una etiqueta única, llamada índice.

```python
numeros = [3, 4, 5, 6, 7]
serie = pd.Series(numeros)
serie, type(serie)
```
$$Consola$$
![[Pasted image 20230820185926.png|500]]


## DataFrames
Un DataFrame es una estructura de datos bidimensional similar a una tabla de base de datos o una hoja de cálculo de Excel. Se compone de múltiples columnas, donde cada columna puede ser una Serie. Los DataFrames son muy útiles para representar y manipular datos en formato tabular.

```python
data = {
    "Nombre":["Ana","Juan","Pedro","Maria","Luis"],
    "Edad":[22,25,28,23,20],
    "Ciudad":["Barcelona","Madrid","Valencia","Sevilla","Bilbao"]
}

data, type(data)
```
$$Consola$$
![[Pasted image 20230820190104.png|1100]]

```python
#Generar un dataframe a partir de un diccionario
df = pd.DataFrame(data=data)
df
```
$$Consola$$
![[Pasted image 20230820190210.png|500]]






___

Pandas ofrece una amplia gama de funciones para realizar tareas comunes de manipulación y análisis de datos, como filtrado, ordenamiento, agrupación, agregación, fusión y más. Además, Pandas está diseñado para funcionar en combinación con otras bibliotecas populares de análisis de datos en Python, como NumPy, Matplotlib y SciPy.

Aquí hay un ejemplo básico de cómo comenzar a usar Pandas para cargar datos desde un archivo CSV y realizar algunas operaciones:

```python
import pandas as pd

# Cargar datos desde un archivo CSV
data = pd.read_csv('archivo.csv')
# Mostrar las primeras filas del DataFrame
print(data.head())
# Filtrar datos
filtered_data = data[data['columna'] > 50]
# Realizar un cálculo de agregación
mean_value = data['columna'].mean()
# Agrupar y resumir datos
grouped_data = data.groupby('categoria')['columna'].sum()
# Guardar los resultados en un nuevo archivo CSV
filtered_data.to_csv('datos_filtrados.csv', index=False)

```


___
%%
tags: #programación #paganálisis_de_datos #python #análisis_de_datos #series #dataframe #pandas

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%