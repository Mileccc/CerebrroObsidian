---
"ID:": 80
"tags:": 
"nombre:": Agregar nuevos datos a un DataFrame
---
___
# Agregar nuevos datos a un DataFrame
___
![](https://www.youtube.com/watch?v=TjfFO2WKF7k&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=10)

___
## Crear un DataFrame de ejemplo
```python
import pandas as pd
  
data = {"Nombre": ["Juan","Ana","Luis","Laura"],
        "Edad": [25,33,30,28]}
df = pd.DataFrame(data)
df
```
$$Consola$$
![[Pasted image 20230824200629.png]]

___
## Agregar una columna

```python
df["Ciudad"] = ["Madrid","Barcelona","Madrid","Valencia"]
df
```
$$Consola$$
![[Pasted image 20230824200726.png]]

___
## Generamos una nueva fila

```python
new_row = pd.Series({"Nombre":"Pedro","Edad":45,"Ciudad":"Barcelona"})
```

## Agregamos fila al DataFrame

Con _**to_frame**_ pasamos el objeto tipo Series anterior a uno tipo DataFrame, además como es un vector columna hay que hacerle una Transposición con T para que sea un vector fila y se pueda agregar.

  

_**ignore_index=True**_ se usa para que no tome el índice que obtuvo al generar la fila (que seria 0) si no que use el índice que le correspondería al insertarse en el DataFrame
```python
df = pd.concat([df, new_row.to_frame().T], ignore_index=True)
df
```
$$Consola$$
![[Pasted image 20230824200916.png]]

___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos #concat #agregar_fila #generar_nueva_fila #agregar_columna 

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%