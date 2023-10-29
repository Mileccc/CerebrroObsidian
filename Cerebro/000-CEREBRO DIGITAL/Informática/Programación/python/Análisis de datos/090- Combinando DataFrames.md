---
"ID:": 90
"tags:": 
"nombre:": Combinando DataFrames
---
___
# Combinando DataFrames
![](https://www.youtube.com/watch?v=1jB0PX4Rd_c&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=11)

___
## Tipos de combinación de DataFrames:

1. **Concatenación (apilamiento):** Se utiliza para unir DataFrames en función de su índice. Se pueden apilar verticalmente (a lo largo de las filas) o horizontalmente (a lo largo de las columnas).
    
2. **Unión (merge):** Se utiliza para combinar DataFrames en función de columnas comunes. Esto es similar a la operación SQL "JOIN".
___
### Concatenación de DataFrames:
___
#### Crear un DataFrame de ejemplo

```python
import pandas as pd

data = {"Nombre": ["Juan","Ana","Luis","Laura"],
        "Edad": [25,33,30,28],
        "Ciudad": ["Barcelona","Madrid","Andalucia","Barcelona"]}
df1 = pd.DataFrame(data)
df1
```
$$Consola$$
![[Pasted image 20230824202308.png]]

#### Crear segundo DataFrame de ejemplo

```python
data2 = {"Nombre": ["Carla","Irene"],
         "Edad": [38,27],
         "Ciudad": ["Madrid","Bilbao"]}
df2 = pd.DataFrame(data2)
df2
```
$$Consola$$
![[Pasted image 20230824202402.png]]


#### Combinar los DataFrames

```python
df_combined = pd.concat([df1,df2], ignore_index=True)
df_combined
```
$$Consola$$
![[Pasted image 20230824202457.png]]

___

### Unión de DataFrames:
#### Crear un DataFrame de ejemplo

```python
data = {"Nombre": ["Juan","Ana","Luis","Laura"],
        "Edad": [25,33,30,28],
        "Ciudad": ["Barcelona","Madrid","Andalucia","Barcelona"]}
df1 = pd.DataFrame(data)
df1
```
$$Consola$$
![[Pasted image 20230824203207.png]]

#### Crear segundo DataFrame de ejemplo

```python
data2 = {"Nombre": ["Carla","Irene"],
         "Edad": [38,27],
         "Ciudad": ["Madrid","Bilbao"]}
df2 = pd.DataFrame(data2)
df2
```
$$Consola$$
![[Pasted image 20230824203255.png]]

#### Unir DataFrame con merge
- `on='Nombre'`: Indica que queremos unir los DataFrames basándonos en la columna "Nombre".
- - `Sin usar el campo how`: Unión interna (solo registros comunes)
- - `how='left'`: Unión izquierda (todos los registros de df1)
- - `how='right'`: Unión derecha (todos los registros de df2)
- - `how='outer'`: Unión externa (todos los registros)

```python
result = pd.merge(df1, df2, on='Nombre', how='outer')
result
```
$$Consola$$
![[Pasted image 20230824203343.png]]



___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos #merge #left #right #outer #externa #derecha #izquierda #unión #concat #concatenación #ignore_index

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%