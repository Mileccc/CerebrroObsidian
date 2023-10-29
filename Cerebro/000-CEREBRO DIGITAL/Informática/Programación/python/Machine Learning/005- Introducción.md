---
ID: 5
tags:
  - "#pagmachine_learning"
  - "#python"
nombre: Introducción
---
___
# 1- Introducción a Machine Learning I
![](https://www.youtube.com/watch?v=p38YNZ2WYZE&list=PLon--J7mANNV6lQd3fWkpJXdiWosN4fF-&index=6)
¿Cómo haríamos una serie de instrucciones para clasificar  imágenes de gatos y perros? ¿O qué número aparece?

![[Pasted image 20230906074940.png]]

![[Pasted image 20230906075059.png]]

Decimos que un programa "aprende" si para cierta tarea, su performance mejora cuando crece la experiencia. T.Michel

![[Pasted image 20230906075315.png]]

Todo este repertorio de estimadores va a usar la misma interfaz, que se ve algo así:

```python
from sklearn.familia_de_modelos import Modelo
  
mi_modelo = Modelo(hiperparametros)
mi_modelo.fit(x, y)

prediccion = mi_modelo.predict(nuevo_X)
```

Para ajustar nuestros modelos de machine learning, vamos a tener nuestra matriz de features $X$ y un vector $y$ (en el caso de ML supervisado) donde $X$ tiene la forma `n_obvservaciones, n_variables` e $Y$ `n_observaciones`

___
¿Cuáles son algunos ejemplos de IA que no son ML?
- Sistemas basados en reglas
- Demostración automática (proof solvers)
- Optimización convexa en investigación de operaciones

¿Y DS que no es ML?
- Visualización
- EDA
- Inferencia Estadística
- Análisis de audio
- Métodos econométricos
- Biometría
- ...?

___
Algunos ejemplos modernos

![[Pasted image 20230906080317.png|1000]]

![[Pasted image 20230906080418.png|1000]]

## Tipos de Machine Learning (ML)

![[Pasted image 20230906080600.png]]

### Aprendizaje Supervisado

![[Pasted image 20230906080749.png]]

___
#### Regresión lineal
En estadística, la regresión lineal es un modelo matemático usado para aproximar la relación de dependencia entre una variable dependiente $Y$ , y $x$. Este modelo puede ser expresado a grandes rasgos como:

$$Y = \beta_{0}+\beta_{1}x_{1}$$

Donde:
- $Y$ es la variable dependiente o variable de respuesta.
- $x$, es las variables explicativas, independiente o regresoras. Podemos tener cualquier número.
- $\beta_{0}$ ,$\beta_{1}$ son los parámetros del modelo, miden la influencia que las variables explicativas tienen sobre el regrediendo.

el termino $\beta_{0}$ es la intersección o término "constante", las $\beta_{1}$ son los parámetros respectivos a cada variable independiente.

![[Pasted image 20230906081514.png|800]]

___
#### Generalización y sobreajuste
Ya tengo un modelo que me permite estimar valores nuevos.
¿Cómo puedo saber cuán bien va a funcionar sobre datos nuevos?

![[Pasted image 20230906081745.png]]


___
### Aprendizaje no supervisado
**KMeans (clustering)**
- Asignar centroides al azar
- Calcular qué punto pertenece a cada cluster
- Promediar" todos los puntos en cada dimensión para recalcular el centroide
- Repetir hasta que los puntos dejen de cambiar de cluster

![[Pasted image 20230906223713.png]]


___
# 2- Introducción a Machine Learning II

- Conceptos básicos
- Tipos de ML
- Ejemplo NLP
- Ejemplo Completo Titanic


## 2.1-Conceptos básicos

La experiencia de la cual un modelo aprende es un conjunto de observaciones con atributos. En algunos casos, estas observaciones tienen una variable target que queremos predecir. El target es optativo. Para que los modelos de Machine Learning aprendan es necesario que la información esté organizada de manera matricial como a continuación:

![[Pasted image 20230906231612.png|1200]]

Los modelos de ML sólo son capaces de aprender de representaciones numéricas. ¿Cómo podremos entonces trabajar con texto, categorías o imágenes?

![[Pasted image 20230906231929.png]]

Categorías: One Hot Encoding o variables dummies

![[Pasted image 20230906232055.png|1100]]

Texto: Bag of Word

![[Pasted image 20230906232320.png|1400]]

```python
from sklearn.feature_extraction.text import CountVectorizer
  
textos = ["Cello de madera", "Dentrífico de Datos", "Historia de la Mesopotamia"]

vec = CountVectorizer()
X = vec.fit_transform(textos)
X
```
$$Consola$$
![[Pasted image 20230907181241.png]]


```python
from sklearn.feature_extraction.text import CountVectorizer`
```
1. En esta línea, importamos la clase `CountVectorizer` del módulo `sklearn.feature_extraction.text`. `CountVectorizer` es una herramienta en scikit-learn que se utiliza para convertir colecciones de documentos de texto en una matriz de recuento de términos/token.
```python
textos = ["Cello de madera", "Dentrífico de Datos", "Historia de la Mesopotamia"]
```

2. Aquí definimos una lista llamada `textos` que contiene tres cadenas de texto, cada una representando un documento o una frase.
```python
vec = CountVectorizer
```


3. Creamos una instancia de la clase `CountVectorizer` y la asignamos a la variable `vec`. Esta instancia se utilizará para transformar los textos en una representación numérica.
```python
X = vec.fit_transform(textos)
```


4. Usamos el método `fit_transform` del objeto `vec` para transformar la lista de textos en una matriz numérica `X`. En esta matriz, cada fila representa un documento (de la lista `textos`) y cada columna representa una palabra única encontrada en todos los documentos. Los valores en la matriz son el recuento de cuántas veces aparece cada palabra en cada documento.

Por ejemplo, si tienes un vocabulario de palabras únicas como ["Cello", "de", "madera", "Dentrífico", "Datos", "Historia", "la", "Mesopotamia"], la matriz resultante `X` podría ser algo como:

```python
[[1, 1, 1, 0, 0, 0, 1, 0],
 [0, 1, 0, 1, 1, 0, 0, 0],
 [0, 1, 0, 0, 0, 1, 1, 1]]
```
Cada fila representa un documento y cada columna representa una palabra en el vocabulario. Los números en la matriz indican cuántas veces aparece cada palabra en cada documento.

___

```python
X.todense()
```
$$Consola$$
![[Pasted image 20230907181947.png]]

Podemos volcar este resultado en un ``DataFrame``. Para obtener el encabezado de las columnas, vamos a utilizar el método `get_feature_names_out()`, propio del vectorizador.

```python
import pandas as pd
  
pd.DataFrame(data = X.todense(), columns = vec.get_feature_names_out())
```
$$Consola$$
![[Pasted image 20230907182528.png]]

Una vez que tenemos nuestros datos ordenados, podemos ajustar nuestro modelo de ML aproximadamente así:

```python
from sklearn.familia_de_modelos import ModuleNotFoundError
  
mi_modelo = Modelo(hiperparámetros) # modelo = b_0 + b_1 * x
mi_modelo.fit(X,y)                  # se calculan los b_0 y b_1 optimos de mejor ajuste
  
predicción = mi_modelo.predict(nuevo_X)
```

Para ajustar nuestros modelos de machine Learning, vamos a tener nuestra matriz de features $X$ y un vector $y$ (en el caso de ML supervisado), donde $X$ tiene la forma `n_observaciones, n_variables` e $y$ `n_observaciones`


# 3-Regregresión Lineal
En estadística, la regresión lineal es un modelo matemático usado para aproximar la relación de dependencia entre una variable dependiente $y$, y $X$. Este modelo puede ser expresado a grandes rasgos como:
$$y=\beta_{0}+\beta_{1}x_{1}$$
Donde:
- $y$ es la variable dependiente o variable de respuesta.
- $x$ son las variables explicativas, independiente o regresoras. Podemos tener cualquier número.
- $\beta_{0},\beta_{1}$ son los parámetros del modelo, miden la influencia que las variables explicativas tienen sobre la variable objetivo.
El termino $\beta_{0}$ es la intersección o término "constante", las $\beta_{i}$ son los parámetros respectivos a cada variable independiente.

***Métricas de evaluación en problemas supervisados***

**Regresión**

![[Pasted image 20230907190146.png]]

**Clasificación**

![[Pasted image 20230907190751.png]]
![[Pasted image 20230907190803.png]]
![[Pasted image 20230907191108.png]]

**Otros modelos supervisados**
- Regresión Lineal
- Regresión logística
- KNN (K nearest neighbours)
- Y muchos mas ...

**Modelos basados en árboles:** en general los mejores predictores.

![[Pasted image 20230907191349.png]]

Los modelos de Machine Learning más performantes, se basan en "ensamblar" muchos árboles simples. Sirven tanto para clasificación como para regresión. Tienen nombres como:
- Random Forest
- XGBoost
- LightGBM
- Tree Gradient Boosting

### Generalización y sobreajuste

![[Pasted image 20230907192205.png]]


### Evaluación
¡Cuidado! Es imposible usar el futuro para predecir el presente.


![[Pasted image 20230912075350.png]]


![[Pasted image 20230912075909.png]]


![[Pasted image 20230912080020.png]]

![[Pasted image 20230912080101.png]]
























___

%%
tags: #pagmachine_learning #python   

Vínculos: [[000-Menú Machine Learning 📃|Menú Machine Learning 📃]] 
%%