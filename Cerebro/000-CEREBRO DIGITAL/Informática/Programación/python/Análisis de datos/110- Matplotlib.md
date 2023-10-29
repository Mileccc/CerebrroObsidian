---
ID:: 110
tags::  #programación #paganálisis_de_datos #python  #análisis_de_datos
nombre:: "Matplotlib"
---
___
# Matplotlib
___
![](https://www.youtube.com/watch?v=qxi9xbMirgE&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=16)

___

```python
import matplotlib.pyplot as plt
```



### Ejemplo de una Linea simple
```python
x = [0,1,2,3,4,5]
y = [0,1,2,3,4,5]
  
plt.plot(x,y)
```
$$Consola$$
![[Pasted image 20230831204225.png|600]]
Si estas desde un script debes añadir además para que se habra una ventana interactiva donde se visualizará la gráfica:
```python
plt.show()
```

### Ver puntos en vez de la Linea
```python
plt.scatter(x,y)
```
$$Consola$$
![[Pasted image 20230831204550.png|600]]

### Poner nombre a los Ejes y título

```python
plt.xlabel("Eje X")
plt.ylabel("Eje Y")
plt.title("Mi primera gráfica")
```
$$Consola$$
![[Pasted image 20230831205053.png|600]]


Ver todo a la vez:
```python
plt.plot(x,y)
plt.scatter(x,y)
plt.xlabel("Eje X")
plt.ylabel("Eje Y")
plt.title("Mi primera gráfica")
```
$$Consola$$
![[Pasted image 20230831205141.png|600]]


### Gráfico de barras

```python
categorias = ["A","B","C","D"]
valores = [10,20,25,30]
plt.bar(categorias,valores)
plt.title("Gráfico de barras")
plt.xlabel("Categorias")
plt.ylabel("Valores")
plt.show()
```
$$Consola$$
![[Pasted image 20230902195916.png]]
___
### Estilos

```python
plt.style.use("ggplot")
plt.style.available
```
$$Consola$$
![[Pasted image 20230902212921.png]]
___
#### Probando con grafica de una Linea estilos
```python
x = [0,1,2,3,4,5]
y = [0,1,4,9,16,25]
  
plt.plot(x,y, color="red", linestyle= "--", marker="o")
plt.ylabel("Valores medidos")
plt.xlabel("tiempo")
plt.show()
```
$$Consola$$
![[Pasted image 20230902213007.png]]

___































___
%%
tags: #programación #paganálisis_de_datos #python #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%