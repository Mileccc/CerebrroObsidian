---
ID: 100
tags: 
nombre: Maldición de la dimensionalidad
---
___
# Maldición de la dimensionalidad

![](https://www.youtube.com/watch?v=nhgCwWGNDiM&ab_channel=C%C3%B3digoM%C3%A1quina)

***Resumen***
La **maldición de la dimensionalidad** se refiere al problema que surge en machine learning cuando se agregan demasiadas variables o dimensiones a un modelo.  

Octavio Gutiérrez explica este concepto generando vectores aleatorios sintéticos de 3 variables (##x##, ##y##, ##z##) que representan características como edad, peso y altura. Luego grafica los vectores en 1, 2 y 3 dimensiones.  

***Puntos importantes:***

- (00:37) Se generan vectores aleatorios sintéticos de 3 variables que van de 0 a 9  
- (02:51) Se grafican los vectores en 1, 2 y 3 dimensiones con Matplotlib
- (05:39) En 1 dimensión, con 10 valores posibles, se ve una tendencia en los datos  
- (06:16) Al aumentar a 2 y 3 dimensiones, los datos se dispersan y pierden significancia estadística
- (07:36) El número de configuraciones posibles crece exponencialmente con más dimensiones  
- (08:55) Modelos de ML requieren más instancias de datos en alto dimensiones para ser sólidos
- (09:38) Existen técnicas para reducir dimensiones preservando información de los datos

En resumen, la maldición de la dimensionalidad señala que agregar demasiadas variables o dimensiones a un modelo de ML dispersa los datos, diluye su significancia estadística y dificulta encontrar patrones, requiriendo más instancias de datos. Se pueden usar técnicas de reducción de dimensionalidad para contrarrestar este problema.

***Mapa conceptual:***
![[Pasted image 20231002075342.png|4500]]

***Ejemplos***
### Generar datos aleatorios sintéticos de 3 variables

```python
import numpy as np
  
x = np.random.randint(10, size=10)
y = np.random.randint(10, size=10)
z = np.random.randint(10, size=10)
x, y, z
```



    (array([1, 0, 9, 2, 9, 9, 6, 8, 9, 5]),
     array([8, 6, 3, 9, 3, 8, 3, 0, 8, 3]),
     array([3, 8, 2, 4, 7, 7, 8, 3, 0, 1]))


### Graficar los datos para cada dimensión


```python
import matplotlib.pyplot as plt
  
#crear gráfica con tres subfiguras
fig = plt.figure(figsize=(18, 6))
  
#espacio unidimensional
ax = fig.add_subplot(1, 3, 1)
ax.plot(x, [0]*10, linewidth=0, marker="*",
        color="purple", markersize=20)
  
#espacio bidimensional
ax = fig.add_subplot(1, 3, 2)
ax.scatter(x, y, marker="*", c="purple", s=200)
  
#espacio tridimensional
ax = fig.add_subplot(1, 3, 3, projection="3d")
ax.scatter(x, y, z, marker="*", c="purple", s=200)
  
plt.show()
```

  
  

![[output_4_0 3.png|1000]]

  
  
### El número de Configuraciones incrementa

## Exponencialmente


```python
fig = plt.figure(figsize=(18, 6))
  
# Espacio unidimensional
ax = fig.add_subplot(1, 3, 1)
  
ax.set_title("10^1 = 10", fontsize=35)
  
ax.plot(range(0, 10), [0]*10,
        marker="o", linewidth=0,
        color="skyblue", markersize=20)
  
ax.plot(x, [0]*10, linewidth=0,
        marker="*", color="purple",
        markersize=20)
  
# Espacio bidimensional
ax = fig.add_subplot(1, 3, 2)
  
ax.set_title("10^2 = 100", fontsize=35)
  
for i in range(10):
    ax.scatter(range(0, 10), [i]*10,
               s=200, c="skyblue", marker="*")
ax.scatter(x, y, marker="*", c="purple", s=200)

# Espacio tridimensional
ax = fig.add_subplot(1, 3, 3, projection="3d")
  
ax.set_title("10^3 = 1000", fontsize=35)
  
for i in range(10):
    for j in range(10):
         ax.scatter(range(0, 10), [i]*10, j,
                    s=200, c="skyblue", marker="*",
                    alpha=0.25)
  
ax.scatter(x, y, z, marker="*", c="purple", s=200)
  
plt.show()
```

  
  
![[output_7_0 3.png|1000]]



___

%%
tags: #pagmachine_learning #python   

Vínculos: [[000-Menú Machine Learning 📃|Menú Machine Learning 📃]] 
%%