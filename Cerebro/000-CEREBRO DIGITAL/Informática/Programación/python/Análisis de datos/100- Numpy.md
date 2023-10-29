---
ID:: 100
tags::  #programación #paganálisis_de_datos #python  #análisis_de_datos
nombre:: "Numpy"
---
___
# Numpy
![](https://www.youtube.com/watch?v=mKN63jxA8gI&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=12)

___
## 1- Introducción

___
### Importar la librería
```python
import numpy as np
```

### Crear arreglo de 1 dimensión con 5 elementos

```python
arr1 = np.array([1,2,3,4,5,6])
arr1
```
$$Consola$$
![[Pasted image 20230827182941.png]]

### Forma del array (shape)

```python
arr1.shape
```
$$Consola$$
![[Pasted image 20230827183031.png]]

### Tipo de datos (dtype)
```python
arr1.dtype
```
$$Consola$$
![[Pasted image 20230827183113.png]]

### Cambiar forma del arreglo a una matriz de 2x3
```python
arr2 = arr1.reshape(2,3)
print("Arreglo 2D: \n",arr2)
print("Forma (shape): ",arr2.shape)
print("Tipo de datos (dtype): ",arr2.dtype)
```
$$Consola$$
![[Pasted image 20230827183152.png]]

### Crear una matriz con forma (4,3) con números aleatorios entre 0 y 1. (random.rand())
```python
matrix = np.random.rand(4,3)
  
print("Arreglo 2D: \n",matrix)
print("Forma (shape): ",matrix.shape)
print("Tipo de datos (dtype): ",matrix.dtype)
```
$$Consola$$
![[Pasted image 20230827183237.png]]

___
## 2- Manipulación de datos
![](https://www.youtube.com/watch?v=eFugBO-YVzY&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=13)
___
### Crear un arreglo de 2 dimensiones a partir de una lista de listas
```python
arr = np.array([[1,2,3],[4,5,6],[7,8,9]])
print(arr,"\n", type(arr))
```
$$Consola$$
![[Pasted image 20230827185521.png]]

### Crear un arreglo de ceros con una forma (3,4)
```python
arr = np.zeros((3,4))
print(arr)
```
$$Consola$$
![[Pasted image 20230827185556.png]]

### Crear un arreglo de unos con una forma de (2,3)
```python
arr = np.ones((2,2))
arr
```
$$Consola$$
![[Pasted image 20230827185635.png]]

### Acceder a una posición del array y sustituir el valor de esa posición
```python
arr[1,1] = 10
arr
```
$$Consola$$
![[Pasted image 20230827185713.png]]

### Crear una matriz identidad
```python
arr = np.eye(4)
print(arr)
```
$$Consola$$
![[Pasted image 20230827185750.png]]

### Crear un arreglo 3D de ceros con forma (2,3,4)
```python
arr = np.zeros((3,4,5))
arr[0,1,2] = 5
print(arr)
```
$$Consola$$
![[Pasted image 20230827185822.png]]

### Transposición (alternar las filas x las columnas y viceversa)
```python
arr = np.random.rand(2,5)
arr
```
$$Consola$$
![[Pasted image 20230827185858.png]]

```python
arr.T
```
$$Consola$$
![[Pasted image 20230827185928.png]]

### Combinar arrays y hacer stacks
```python
arr1 = np.array([[1,2],[3,4]])
arr2 = np.array([[5,6],[7,8]])
arr1, arr2
```
$$Consola$$
![[Pasted image 20230827190022.png]]

#### Concatenar arreglos horizontalmente ([fila1confila1], [fila2confila2])
```python
arr_h = np.hstack((arr1,arr2))
arr_h
```
$$Consola$$
![[Pasted image 20230827190053.png]]

#### Concatenar arreglos verticalmente ([fila1+fila2] con [fila1+fila2])
```python
arr_v = np.vstack((arr1,arr2))
arr_v
```
$$Consola$$
![[Pasted image 20230827190140.png]]

___
## 3- Operaciones matemáticas y estadísticas
![](https://www.youtube.com/watch?v=DG7hvSfDE1U&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=14)

___
### Calcular la suma de elementos
```python
arr = np.array([1,2,3,4,5])
suma = np.sum(arr)
suma
```
$$Consola$$
![[Pasted image 20230827191757.png]]

### Calcular el promedio de los elementos
```python
promedio = np.mean(arr)
promedio
```
$$Consola$$
![[Pasted image 20230827191824.png]]

### Calcular la mediana
```python
mediana = np.median(arr)
mediana
```
$$Consola$$
![[Pasted image 20230827191844.png]]

### Calcular el producto los elementos (los multiplica entre si)
```python
producto = np.prod(arr)
producto
```
$$Consola$$
![[Pasted image 20230827191910.png]]

### Obtener la desviación estándar
```python
desv_est = np.std(arr)
desv_est
```
$$Consola$$
![[Pasted image 20230827191937.png]]

### Calcular la varianza
```python
var = np.var(arr)
var
```
$$Consola$$
![[Pasted image 20230827192000.png]]

### Obtener el mínimo o máximo de los elementos del array
```python
minimo = np.min(arr)
maximo = np.max(arr)
minimo,maximo
```
$$Consola$$
![[Pasted image 20230827192029.png]]

### Calcular la suma acumulativa
```python
cumsum = np.cumsum(arr)
cumsum
```
$$Consola$$
![[Pasted image 20230827192050.png]]

### Suma element-wise (sumar arrays)
```python
arr + arr
```
$$Consola$$
![[Pasted image 20230827192122.png]]

### Resta elemnt-wise (resta de arrays)
```python
arr - arr
```
$$Consola$$
![[Pasted image 20230827192209.png]]

### Multiplicación element-wise ( multiplicación de arrays)
```python
arr * arr
```
$$Consola$$
![[Pasted image 20230827192300.png]]


### División element-wise (división de arrays)
```python
arr / arr
```
$$Consola$$
![[Pasted image 20230827192334.png]]

### Producto element-wise (producto de arrays)
```python
arr % arr
```
$$Consola$$
![[Pasted image 20230827192359.png]]

___
## 4- Integración de Pandas y Numpy
___
![](https://www.youtube.com/watch?v=9OY18iRaQv8&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=15)
___

```python
import pandas as pd
import numpy as np
```



### Crear un arreglo e numpy
```python
data = np.array([[1,2,3],[4,5,6],[7,8,9]])
```


### Crear un DataFrame a partir del arreglo Numpy
```python
df = pd.DataFrame(data, columns=["A","B","C"])
df
```
$$Consola$$
![[Pasted image 20230831202048.png]]

### Obtener un DataFrame a partir de un diccionario 

```python
data = {
    "A" : [1,4,7],
    "B" : [2,5,8],
    "C" : [3,6,9]
}
  
df = pd.DataFrame(data)
df
```
$$Consola$$
![[Pasted image 20230831202048.png]]


### Convertir un DataFrame a un array de Numpy
```python
arr = df.to_numpy()
arr
```
$$Consola$$
![[Pasted image 20230831202657.png]]

Otra forma de hacerlo
```python
df.values
```
$$Consola$$
![[Pasted image 20230831202657.png]]


### Calcular el promedio de cada columna utilizando numpy
Si usas axis=0 lo hará para cada columna, si usas axis=1 lo hará para cada fila
```python
mean_columns = np.mean(df,axis=0)
mean_rows = np.mean(df,axis=1)
mean_columns,mean_rows
```
$$Consola$$
![[Pasted image 20230831203249.png]]

#axis #to_numpy
___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%