---
ID:: 060
tags::  #programación #paganálisis_de_datos #python  #análisis_de_datos #agregación #agg #sum #mean #combinar_múltiples_filas
nombre:: "Agregación de datos"
---
___
# Agregación de datos
___
![](https://www.youtube.com/watch?v=dE_mETQKGTc&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=8)

___
___

![[050- Agrupación de datos#Importamos las librerias necesarias]]

![[050- Agrupación de datos#Generamos un nuevo DataFrame]]

![[050- Agrupación de datos#Agrupamos las personas por ciudad]]

___
___
## Agregación de datos
Agregación es el proceso de combinar múltiples filas de datos en una sola fila aplicando una función de agregación como la suma , promedio, mínimo, máximo, etc

___
## Calcular la suma de las edades y puntuaciones por ciudad

```python
aggregated_data = grouped.agg(
    {
        "Edad":"mean",      #Hará el promedio de la edad
        "Puntuación":"sum"  #Hará una suma de las puntuaciones
    }
)

aggregated_data
```
$$Consola$$
![[Pasted image 20230823164752.png]]

___
## Definir una función de agregación personalizada

```python
def rango(series):
    return series.max() - series.min()
```

### Aplicamos la función agg al grupo
```python
aggregated_data_custom = grouped.agg(
    {
        "Edad":rango,
        "Puntuación":rango
    }
)

aggregated_data_custom
```
$$Consola$$
![[Pasted image 20230823164941.png]]

___
%%
tags: #programación #paganálisis_de_datos #python #análisis_de_datos #agregación #agg #sum #mean #combinar_múltiples_filas

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%