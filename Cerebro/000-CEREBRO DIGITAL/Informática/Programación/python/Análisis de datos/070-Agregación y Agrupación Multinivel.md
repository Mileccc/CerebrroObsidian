---
ID:: 070
tags::  #programación #paganálisis_de_datos #python #análisis_de_datos #multinivel #agregación_multinivel #agrupación_multinivel #agg #agregar_nueva_columna
nombre:: "Agregación y Agrupación Multinivel"
---
___
# Agregación y Agrupación Multinivel
___
![](https://www.youtube.com/watch?v=sL5zhWuIDno&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=9)

___
## DataFrame inicial

```python
import numpy as np
import pandas as pd

data = {
    "Nombre":["Ana","Juan","Pedro","Maria","Luis","Carla",],
    "Edad":[22,25,23,20,29,37,],
    "Ciudad":["Barcelona","Madrid","Valencia","Bilbao","Barcelona","Madrid"],
    "Puntuación":[80,90,85,88,75,99]
}

df = pd.DataFrame(data)
df

grouped = df.groupby("Ciudad")
grouped.groups
```
$$Consola$$
![[Pasted image 20230823170930.png]]

___
## Agregar una nueva columna con datos a un DataFrame ya creado

```python
data["Categoria"] = ["A","B","A","B","B","B"]
df = pd.DataFrame(data)
df
```
$$Consola$$
![[Pasted image 20230823171017.png]]

___
## Agrupación multinivel
Agrupar datos por ciudad y categoría

```python
grouped_multi = df.groupby(["Ciudad","Categoria"])
grouped_multi.groups
```
$$Consola$$
![[Pasted image 20230823171131.png]]

Devuelve un diccionario donde las keys son la tupla de Ciudad y categoría y los valores son una lista de los índices que coinciden con la agrupación indicada en esa tupla
___

## Agregación multinivel

Calcular la suma de las edades y puntuación por Ciudad y por Categoría

```python
aggregated_data_multi = grouped_multi.agg(
    {
        "Edad":"sum",
        "Puntuación":"mean"
    }
)

aggregated_data_multi
```
$$Consola$$
![[Pasted image 20230823171232.png]]

___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos #multinivel #agregación_multinivel #agrupación_multinivel #agg #agregar_nueva_columna

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%