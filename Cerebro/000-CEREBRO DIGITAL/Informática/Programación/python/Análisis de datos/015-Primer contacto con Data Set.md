---
ID:: 015
tags::  #programación #paganálisis_de_datos #python  #análisis_de_datos #read_csv
nombre:: "Primer contacto con Data Set"
---
___
# Primer contacto con Data Set
Para el análisis de datos en python usaremos la librería de Pandas
```python
import pandas as pd
```
![](https://www.youtube.com/watch?v=grBT_YZXHwU&list=PLon--J7mANNWbXbGraiiMNWcv5T69kkAL)

___
Vamos a analizar datos de una fuente real. Los ingresos de los funcionarios son información pública que se libera anualmente en el [portal de datos abiertos](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fdata.buenosaires.gob.ar%2Fdataset%2Fsueldo-funcionarios) de GCBA.

En general los 4 primeros pasos para analizar un data set son:

1. Leerlo
2. Consultar cuáles son las columnas
3. Extraer una muestra
4. Verificar cuántos registros tiene

___
## 1- Para leer el data set usamos la función de pandas read_csv
Con esta función podemos leer archivos que estén en una url pública o en una ubicación del disco accesible desde la Jupyter Notebook.

```python
df = pd.read_csv('http://cdn.buenosaires.gob.ar/datosabiertos/datasets/sueldo-funcionarios/sueldo_funcionarios_2019.csv')
```

## 2- Consultamos las columnas
```python
df.columns
```
$$Resultado$$
![[Pasted image 20230817201257.png]]

## 3- Extraemos una muestra
```python
df.sample(5)
```
$$Resultado$$
![[Pasted image 20230817201743.png]]

"En Jupyter notebook y google colab se visualiza así, en visual Studio no "
## 4- Consultamos la cantidad de filas y de columnas
```python
# La propiedad shape nos devuelve una tupla (filas,columnas)
df.shape
```
$$Resultado$$
![[Pasted image 20230817202147.png]]




___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:  [[000-Menú Análisis de datos 📃]]
%%