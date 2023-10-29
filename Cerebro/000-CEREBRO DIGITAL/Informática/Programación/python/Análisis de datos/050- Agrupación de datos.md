---
ID:: 050
tags::  #programación #paganálisis_de_datos #python  #análisis_de_datos #groupby #group_by #agrupar #groups
nombre:: "Agrupación de datos"
---
___
# Agrupación de datos
![](https://www.youtube.com/watch?v=hNGOxjpEoMw&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=7)

___
## Importamos las librerias necesarias
```python
import numpy as np
import pandas as pd
```

___
## Generamos un nuevo DataFrame

```python
data = {
    "Nombre":["Ana","Juan","Pedro","Maria","Luis","Carla",],
    "Edad":[22,25,23,20,22,25,],
    "Ciudad":["Barcelona","Madrid","Valencia","Bilbao","Barcelona","Madrid"],
    "Puntuación":[80,90,85,88,75,91]
}

df = pd.DataFrame(data)
df
```
$$Consola$$
![[Pasted image 20230823162607.png]]

___
## Agrupamos las personas por ciudad

```python
grouped = df.groupby("Ciudad")
grouped.groups
```
$$Consola$$
![[Pasted image 20230823162634.png]]

pandas generará un diccionario en el que cada key almacenara una lista con el índice de las coincidencias de cada ciudad



___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos #groupby #group_by #agrupar #groups

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%