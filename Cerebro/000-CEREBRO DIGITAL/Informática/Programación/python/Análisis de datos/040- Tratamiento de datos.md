---
ID:: 040
tags::  #programación #paganálisis_de_datos #python  #análisis_de_datos #valores_nulos #null #nulos #valores_faltantes #eliminar_filas #rellenar #reemplazar_nombres_columna #interpolar_valores #duplicados #eliminar_duplicados #renombrar #visualizar_nueva_columna
nombre:: "Tratamiento de datos"
---
___
# Tratamiento de datos
___
![](https://www.youtube.com/watch?v=Id2ZC7YxQZk&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=6)

___
## Usaremos numpy para importar los valores nulos

```python
import pandas as pd
import numpy as np
```

___
## Creamos un DataFrame con algunos valores nulos

```python
data = {
    "Nombre":["Ana","Juan","Pedro","Maria","Luis"],
    "Edad":[22,25,np.nan,23,20],
    "Ciudad":["Barcelona","Madrid","Valencia",None,"Bilbao"]
}

df = pd.DataFrame(data)
df
```
$$Consola$$
![[Pasted image 20230823160517.png]]

___
## Rellenar los valores faltantes

**df.fillna** es un método que se encargará de saber que hacer con cada uno de los casos null
**mean()** es un método de pandas  que se encarga de sacar el promedio

```python
df_fill = df.fillna(
    {
        "Edad" : df["Edad"].mean(),
        "Ciudad" : "Desconocido"
    }
)

df_fill
```
$$Consola$$
![[Pasted image 20230823160612.png]]

___
## Eliminar filas con valores faltantes

```python
df_sin_nan = df.dropna()
df_sin_nan
```
$$Consola$$
![[Pasted image 20230823160642.png]]

___
## Reemplazar valores específicos de alguna columna

```python
df_reem = df.replace(
    {
        "Ciudad" : {
            None:"Desconocido",
            "Barcelona":"Andalucia"
            }
    }
)

df_reem
```
$$Consola$$
![[Pasted image 20230823160729.png]]

___
## Interpolar Valores

```python
df_interpolado = df.copy()
df_interpolado["Edad"] = df["Edad"].interpolate()
df_interpolado
```
$$Consola$$
![[Pasted image 20230823160759.png]]

___
## Generamos nuevo diccionario para trabajar con datos duplicados

```python
data_duplicada = {
    "Nombre":["Ana","Juan","Pedro","Maria","Luis","Ana","Juan"],
    "Edad":[22,25,np.nan,23,20,22,25,],
    "Ciudad":["Barcelona","Madrid","Valencia",None,"Bilbao","Barcelona","Madrid"]
}

df_duplicado = pd.DataFrame(data_duplicada)
df_duplicado
```
$$Consola$$
![[Pasted image 20230823160833.png]]

___
## Eliminar duplicados

```python
df_sin_duplicados = df_duplicado.drop_duplicates(
df_sin_duplicados
```
$$Consola$$
![[Pasted image 20230823160859.png]]

___
## Renombrar columnas de nuestro DataFrame

```python
df_renombrado = df.rename(columns={"Nombre":"Name","Edad":"Age","Ciudad":"City"})
df_renombrado
```
$$Consola$$
![[Pasted image 20230823160928.png]]

___
## Ordenar el orden de las columnas

```python
columnas_ordenadas = ["Ciudad","Edad","Nombre"]
df_ordenado = df[columnas_ordenadas]
df_ordenado
```
$$Consola$$
![[Pasted image 20230823160959.png]]

___
## Visualizar nueva columna con una transformación de datos (ver edades al cuadrado)

```python
def cuadrado(x):
    return x**2

df["Edad_Cuadrado"] = df["Edad"].apply(cuadrado)
df
```
$$Consola$$
![[Pasted image 20230823161025.png]]


___
%%
tags: #programación #paganálisis_de_datos #python #análisis_de_datos #valores_nulos #null #nulos #valores_faltantes #eliminar_filas #rellenar #reemplazar_nombres_columna #interpolar_valores #duplicados #eliminar_duplicados #renombrar #visualizar_nueva_columna

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%