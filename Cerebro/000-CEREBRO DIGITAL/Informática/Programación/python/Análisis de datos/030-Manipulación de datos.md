---
ID:: 030
tags::  #programación #paganálisis_de_datos #python  #análisis_de_datos #manipulación #filtrar #seleccionar_columna #seleccionar_índice
nombre:: "Manipulación de datos"
---
___
# Manipulación de datos
![](https://www.youtube.com/watch?v=r19cPgQtJMc&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=5)

___
### seleccionar una columna
```python
#seleccionar una columna
nombres = df["Nombre"]
print(nombres, type(nombres))
```
$$Consola$$
![[Pasted image 20230821200457.png]]
### Seleccionar una o mas columnas
```python
#Seleccionar una o mas columnas
df[["Nombre","Edad"]]
```
$$Consola$$
![[Pasted image 20230821200638.png]]
### Filtrar por índice
```python
#Filtrar por indice
fila = df.loc[2]
fila
```
$$Consola$$
![[Pasted image 20230821200901.png]]
### Filtrar pro condiciones
```python
#Filtrar pro condiciones
df[df["Edad"] > 23]
```
$$Consola$$
![[Pasted image 20230821201100.png]]
### Filtrar por edad mayor a 23 años y que su nombre empiece por P
```python
#Filtrar por edad mayor a 23 años y que su nombre empiece por P
filtro = (df["Edad"] > 23) & (df["Nombre"].str.startswith("P"))
df[filtro]
```
$$Consola$$
![[Pasted image 20230821201637.png]]

### Filtrar por query
```python
#Filtrar por query
df.query("Edad > 23")
```
$$Consola$$
![[Pasted image 20230821201845.png]]
### Filtrar trayendo los datos que coincidan con una lista dada de nombres
```python
#Filtrar trayendo los datos que coincidan con una lista dada de nombres
df[df["Nombre"].isin(["Ana","Carlos","Luis"])]
```
$$Consola$$
![[Pasted image 20230821202126.png]]
### Filtrar con una funcion . Nombre con cierta longitud
```python
#Filtrar con una funcion . Nombre con cierta longitud
def longitud_5(nombre):
    return len(nombre) == 5

df[df["Nombre"].apply(longitud_5)]
```
$$Consola$$
![[Pasted image 20230821202446.png]]
### Filtrar por edades entre 25 y 35 años( rango inclusivo)
```python
#Filtrar por edades entre 25 y 35 años( rango inclusivo)
df[df["Edad"].between(25,35)]
```
$$Consola$$
![[Pasted image 20230821202705.png]]

___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos #manipulación #filtrar #seleccionar_columna #seleccionar_índice

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%