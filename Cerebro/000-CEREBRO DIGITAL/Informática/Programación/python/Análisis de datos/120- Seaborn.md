---
ID: 120
"tags:": 
"nombre:": Seaborn
---
___
# Seaborn
![](https://www.youtube.com/watch?v=MNajb2I7XzE&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=18)
___
```python
import pandas as pn
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

## Importamos un DataSet para trabajar con los datos con seaborn
El DataSet iris es un DataSet de flores que se suele usar a menudo para practicar con seaborn

```python
data = sns.load_dataset("iris")
data
```
$$Consola$$
![[Pasted image 20230903201637.png]]

Podemos hacer un set para ver las distintas especies del DataSet

```python
set(data["species"])
```
$$Consola$$
![[Pasted image 20230903201708.png]]

___
## Gráfica de dispersión
Las _gráficas de dispersión_ se utilizan para representar la relación entre dos variables numéricas. Estas gráficas muestran puntos en un plano cartesiano, donde cada punto representa un par de valores ($x$, $y$), donde "x" y "y" son las dos variables que se están comparando. Las gráficas de dispersión son útiles para identificar patrones, tendencias, correlaciones o relaciones entre las variables, lo que puede ayudar a comprender mejor el conjunto de datos y tomar decisiones informadas.

***hue=*** se usa para que los puntos de la grafica se pinten según la columna que añadamos como target, en este caso "species".

```python
sns.scatterplot(x="sepal_length", y="sepal_width", hue="species", data=data)
plt.xlabel("Longitud del sepalo")
plt.ylabel("Ancho del sepalo")
plt.title("Gráficod e dispersión")
plt.show()
```
$$Consola$$
![[Pasted image 20230903201834.png]]

### Generamos otra gráfica de dispersión modificando opciones de visualización

```python
sns.set_style("whitegrid")
palette = sns.color_palette("husl", 3)
  
sns.scatterplot(x="sepal_length", y="sepal_width", hue="species", data=data, palette=palette)
plt.xlabel("Longitud del sepalo")
plt.ylabel("Ancho del petalo")
plt.title("Gráfico personalizado")
plt.show()
```
$$Consola$$
![[Pasted image 20230903201925.png]]

___
## Gráfica de Ridgeplot
Se utilizan para visualizar la distribución de una variable numérica en función de una variable categórica o para comparar la distribución de múltiples variables numéricas. Estas gráficas son especialmente útiles cuando se desea representar la distribución de datos de manera más informativa que un simple histograma o cuando se tienen múltiples categorías para comparar.

```python
setosa = data[data["species"] == "setosa"]
versicolor = data[data["species"] == "versicolor"]
virginica = data[data["species"] == "virginica"]
  
#Generamos el lienzo y los ejes
fig, ax = plt.subplots(figsize=(8,6))
plt.xlabel("Longitud del petalo")
  
#Crear el ridge plot usando kdeplot
sns.kdeplot(data=setosa["petal_length"], label="setosa", ax = ax, fill = True)
sns.kdeplot(data=versicolor["petal_length"], label="versicolor", ax = ax, fill = True)
sns.kdeplot(data=virginica["petal_length"], label="virginica", ax = ax, fill = True)
  
#Ajustamos la posición de las leyendas
ax.legend(loc="upper right")
  
plt.title("Ridge plot - Iris dataset")
plt.show()
```
$$Consola$$
![[Pasted image 20230903202041.png]]

#### Código desgranado 
1. **Separación de Datos**: En este bloque de código, se están separando los datos del conjunto de datos en tres subconjuntos según la especie de iris. Los subconjuntos se llaman `setosa`, `versicolor` y `virginica`. Esto se logra utilizando la indexación booleana para filtrar las filas del DataFrame `data` basándose en el valor de la columna "species". Cada subconjunto contendrá las filas correspondientes a una especie particular de iris.

```python
setosa = data[data["species"] == "setosa"]
versicolor = data[data["species"] == "versicolor"]
virginica = data[data["species"] == "virginica"]
```

2. **Creación del Lienzo y los Ejes**: En este bloque, se crea la figura (`fig`) y los ejes (`ax`) en los que se dibujará el gráfico. La función `plt.subplots(figsize=(8, 6))` crea un objeto de figura (`fig`) y ejes (`ax`) con un tamaño de 8 pulgadas de ancho por 6 pulgadas de alto. Luego, se establece la etiqueta del eje x utilizando `plt.xlabel` para indicar "Longitud del pétalo".

```python
fig, ax = plt.subplots(figsize=(8, 6))
plt.xlabel("Longitud del pétalo")
```

3. **Creación del Ridge Plot**: En esta parte, se utiliza Seaborn para crear el ridge plot utilizando `sns.kdeplot`. Se generan las distribuciones de densidad de kernel (Kernel Density Estimation) para la longitud del pétalo de cada especie y se llenan para que el gráfico sea un ridge plot. Cada especie se representa con una línea en el gráfico, y se les asigna una etiqueta ("setosa", "versicolor" o "virginica") para la leyenda.

```python
sns.kdeplot(data=setosa["petal_length"], label="setosa", ax=ax, fill=True)
sns.kdeplot(data=versicolor["petal_length"], label="versicolor", ax=ax, fill=True)
sns.kdeplot(data=virginica["petal_length"], label="virginica", ax=ax, fill=True)
```

4. **Ajuste de la Leyenda**: Se ajusta la posición de la leyenda utilizando `ax.legend(loc="upper right")`, colocándola en la esquina superior derecha del gráfico.

```python
ax.legend(loc="upper right")
```

5. **Título del Gráfico**: Finalmente, se agrega un título al gráfico utilizando `plt.title`.

```python
plt.title("Ridge plot - Iris dataset")
```

6. **Mostrar el Gráfico**: Se utiliza `plt.show()` para mostrar el gráfico generado.

___
# Gráfico avanzado
![](https://www.youtube.com/watch?v=ARUYAIU3ULo&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=19)
___
## Generar datos de ejemplo

```python
np.random.seed(42)
edad_autos = np.random.randint(0,20, size=200)
edad_autos
```
$$Consola$$
![[Pasted image 20230904203805.png]]

```python
precio_autos = 30 - edad_autos + np.random.normal(-3,3, size=200)
precio_autos
```
$$Consola$$
![[Pasted image 20230904203835.png]]

```python
data = pd.DataFrame({
    "edad":edad_autos,
    "precio":precio_autos
})
data
```
$$Consola$$
![[Pasted image 20230904203911.png]]

## Creación del gráfico

```python
fig, ax = plt.subplots(2,2, figsize=(12,10))

#Gráfico de dispersión
ax[0,0].scatter(data["edad"], data["precio"], alpha=0.5)
ax[0,0].set_xlabel("Edad del automovil (años)")
ax[0,0].set_ylabel("Precio (miles de dolares)")
ax[0,0].set_title("Edad vs Precio")
  
#Histograma de la edad
sns.histplot(data["edad"], ax=ax[0,1], kde=True, color="g")
ax[0,1].set_xlabel("Edad del automovil (años)")
ax[0,1].set_ylabel("Frecuencia")
ax[0,1].set_title("Histograma: Edad")
  
#Histograma del precio
sns.histplot(data["precio"], ax=ax[1,0], kde=True, color="b")
ax[1,0].set_xlabel("Precio (miles de dolares)")
ax[1,0].set_ylabel("Frecuencia")
ax[1,0].set_title("Histograma: Precio")
  
#Eliminar cuarto subplot
ax[1,1].axis("off")
  
plt.subplots_adjust(wspace=0.3, hspace=0.3)
```
$$Consola$$
![[Pasted image 20230904204013.png]]

___









































___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%