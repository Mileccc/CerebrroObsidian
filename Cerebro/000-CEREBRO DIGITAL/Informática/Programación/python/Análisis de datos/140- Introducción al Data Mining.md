---
ID: 140
"tags:": 
"nombre:": Introducción al Data Mining
---
___
# Introducción al Data Mining
___
![](https://www.youtube.com/watch?v=US6uMyYJjRg&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=24)

___
El Data Mining, también conocido como minería de datos, es el proceso de extracción de patrones, conocimientos y correlaciones útiles a partir de grandes volúmenes de datos. Esto se logra mediante la aplicación de técnicas de análisis de datos y algoritmos de aprendizaje automático.


## Conceptos básicos de Data Mining

- **Dataset:** Conjunto de datos recolectados y organizados para su análisis.
- **Atributos**: Características o variables que describen los objetos del dataset.
- **Registro**: Un conjunto de atributos que describen a un objeto en el dataset.
- **Clasificación**: Asignación de objetos a clases predefinidas en función de sus atributos.
- **Regresión**: Predicción de un valor numérico en función de los atributos de un objeto.
- **Agrupamiento**: División de los objetos en grupos según sus atributos, de manera que los objetos en un grupo sean similares entre sí y diferentes a los objetos en otros grupos.


## Proceso de Data Mining (CRISP-DM)

![[Pasted image 20230907203857.png]]

___
## 1- Técnica PCA

```python
pip install scikit-learn
```

La librería `sklearn` en Python es una poderosa herramienta para realizar tareas de aprendizaje automático y minería de datos. En particular, `sklearn.decomposition` es un módulo específico que se centra en técnicas de reducción de dimensionalidad, como el Análisis de Componentes Principales (PCA, por sus siglas en inglés).

El PCA es una técnica que se utiliza para transformar un conjunto de datos en un nuevo sistema de coordenadas, donde las variables están des correlacionadas y ordenadas por su varianza. Esto significa que el PCA toma un conjunto de datos con muchas variables (o dimensiones) y lo proyecta en un espacio de menor dimensión, manteniendo la mayor parte de la información.

El objetivo principal de PCA es simplificar la representación de datos, manteniendo la estructura esencial de la información. Esto puede ser útil para visualizar datos en dimensiones más bajas, reducir la complejidad computacional de los algoritmos de aprendizaje automático y eliminar la multicolinealidad entre variables.

```python
import seaborn as sns
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
  
from sklearn.decomposition import PCA
```

Primero, se importan las bibliotecas `seaborn` (que generalmente se usa para visualización de datos), `PCA` de `sklearn` (para realizar el Análisis de Componentes Principales) y `matplotlib.pyplot` (para crear gráficos).

```python
df = sns.load_dataset("iris")
df
```
$$Consola$$
![[Pasted image 20230908223551.png]]

Se carga el conjunto de datos "iris" utilizando la función `load_dataset` de `seaborn`. Este conjunto de datos es famoso y se utiliza comúnmente para tareas de clasificación en aprendizaje automático. Contiene información sobre tres especies diferentes de flores iris y las medidas de sus sépalos y pétalos.

```python
pca_model = PCA(n_components=2)
df_pca = pca_model.fit_transform(df.iloc[:,:-1])
df_pca
```
$$Consola$$
![[Pasted image 20230908224102.png]]


1. Se crea un modelo de Análisis de Componentes Principales (PCA) con `n_components=2`, lo que significa que queremos reducir la dimensionalidad del conjunto de datos original a solo 2 componentes principales. Esto simplificará los datos y permitirá una visualización más fácil.

2. Se aplica PCA al conjunto de datos original `df`. `df.iloc[:,:-1]` se utiliza para seleccionar todas las columnas excepto la última, que contiene la información de la especie de la flor. El resultado se almacena en `df_pca`, que ahora contiene las coordenadas de los datos en el espacio de los dos componentes principales.
   1. **Fit (Ajustar)**: En la primera parte de la operación, el algoritmo o modelo se "ajusta" a los datos de entrada. En el contexto de PCA, esto significa que el algoritmo analiza los datos para calcular los componentes principales y otras estadísticas necesarias. El ajuste implica encontrar patrones, relaciones y características importantes en los datos de entrada.
   2. **Transform (Transformar)**: En la segunda parte de la operación, los datos de entrada se transforman utilizando la información recopilada durante la fase de ajuste. En el caso de PCA, se realizan las transformaciones lineales necesarias para proyectar los datos originales en un nuevo espacio de características definido por los componentes principales.

```python
plt.scatter(df_pca[:,0], df_pca[:,1], c=df["species"].astype("category").cat.codes)
plt.xlabel("PCA1")
plt.ylabel("PCA2")
plt.show
```
$$Consola$$
![[Pasted image 20230908224142.png]]


1. Se crea un gráfico de dispersión (`scatter plot`) utilizando los valores de los componentes principales. `df_pca[:,0]` y `df_pca[:,1]` se utilizan como las coordenadas `x` e `y` respectivamente, y se utiliza el color `c` para codificar las especies de iris. Las especies se codifican como números enteros utilizando `cat.codes`.

2. Se añaden etiquetas a los ejes `x` e `y` del gráfico para indicar qué componentes principales representan.

3. Finalmente, se muestra el gráfico de dispersión que visualiza los datos en el espacio de los dos primeros componentes principales. Esto permitirá ver si las muestras de diferentes especies de iris se agrupan o separan en función de estos componentes principales.


## 2- Técnica Transformación de Variables
La técnica de "transformación de variables" se refiere al proceso de modificar las variables de un conjunto de datos para mejorar su distribución, escalado o relación con otras variables. Esto se hace con el objetivo de preparar los datos para su uso en modelos de aprendizaje automático o para análisis estadísticos más efectivos.

Aquí te explicaré algunas técnicas comunes de transformación de variables:

1. **Normalización o Escalado (Feature Scaling):** Esta técnica implica ajustar el rango de valores de las variables para que todos estén en una escala similar. La normalización es especialmente importante para algoritmos sensibles a la escala, como el descenso de gradiente en el aprendizaje de máquinas. Los métodos comunes incluyen la estandarización (restar la media y dividir por la desviación estándar) y la escala mín-máx (reescalar los valores al rango [0, 1]).
    
2. **Transformación Logarítmica:** Se aplica el logaritmo natural a los valores de una variable. Esto es útil cuando la distribución de la variable original es sesgada hacia la derecha, ya que la transformación logarítmica puede reducir este sesgo.
    
3. **Transformación de Raíz Cuadrada:** Se toma la raíz cuadrada de los valores de una variable. Al igual que la transformación logarítmica, esta técnica se utiliza para reducir el sesgo en una distribución sesgada hacia la derecha.
    
4. **Transformación de Box-Cox:** Es una familia de transformaciones que incluye tanto la transformación logarítmica como la raíz cuadrada como casos especiales. La transformación de Box-Cox es útil cuando no está claro cuál de las transformaciones anteriores sería la mejor.
    
5. **Discretización:** Convierte variables continuas en variables categóricas o discretas. Esto puede simplificar la interpretación o ser necesario para ciertos algoritmos de aprendizaje automático.
    
6. **One-Hot Encoding:** Convierte variables categóricas en una representación binaria. Esto es útil para modelos que requieren variables numéricas, como regresión lineal o redes neuronales.
    
7. **Binning o Agrupación:** Divide una variable continua en intervalos (bins) y asigna cada valor a uno de esos intervalos. Esto puede simplificar la relación entre la variable y el objetivo.
    
8. **Funciones de Base:** Se utilizan en regresiones polinómicas o regresiones no lineales para transformar las variables predictoras en funciones más complejas.
    
9. **Transformaciones de Escala Robusta:** Algunas técnicas, como la Escala Robusta, son menos sensibles a los valores atípicos y pueden ser más apropiadas para conjuntos de datos con presencia de outliers.

```python
sns.displot(data=df, x = "sepal_length", hue="species", kde=True)
plt.show()
```
$$Consola$$
![[Pasted image 20230908225518.png]]

### Transformación logarítmica

```python
df["sepal_length_log"] = np.log(df["sepal_length"])
  
sns.displot(data=df, x = "sepal_length_log", hue="species", kde=True)
plt.show()
```
$$Consola$$
![[Pasted image 20230908225556.png]]


## 3- Técnica de Normalización de datos

```python
from sklearn.preprocessing import StandardScaler, MinMaxScaler
```

``StandardScaler()``
Su función principal es realizar una transformación en los datos para que tengan una media (promedio) de cero y una desviación estándar de uno. Esto se conoce como estandarización o escalado estándar.

La estandarización es una técnica común en el preprocesamiento de datos y es útil cuando se trabaja con algoritmos de aprendizaje automático que son sensibles a la escala de las características (como la regresión lineal, la regresión logística y las máquinas de soporte vectorial).
```python
std_scaler = StandardScaler()
df_std_scaler = std_scaler.fit_transform(df.iloc[:,:-2])
df_std_scaler
```
$$Consola$$
![[Pasted image 20230909195347.png]]


Mientras que `StandardScaler()` estandariza los datos para que tengan una media de cero y una desviación estándar de uno, `MinMaxScaler()` realiza una transformación que ajusta los datos a un rango específico, generalmente entre 0 y 1.
```python
mm_scaler = MinMaxScaler()
df_normalized = mm_scaler.fit_transform(df.iloc[:,:-2])
df_normalized
```
$$Consola$$
![[Pasted image 20230909195722.png]]


## 4- Técnica de Correlación (Pearson)

Es una técnica estadística que se utiliza para medir la relación lineal entre dos variables continuas. En otras palabras, determina cuán estrechamente relacionadas están dos variables y en qué dirección se relacionan.

El coeficiente de correlación de Pearson puede tomar valores en el rango de -1 a 1:

- Si el coeficiente es 1, indica una correlación positiva perfecta, lo que significa que a medida que una variable aumenta, la otra también aumenta en una relación lineal perfecta.
- Si el coeficiente es -1, indica una correlación negativa perfecta, lo que significa que a medida que una variable aumenta, la otra disminuye en una relación lineal perfecta.
- Si el coeficiente es 0, indica que no hay correlación lineal entre las dos variables. En otras palabras, no hay una relación lineal predecible entre ellas.

Algunos puntos clave sobre la correlación de Pearson:

- Mide solo relaciones lineales. Si la relación entre las variables es no lineal, el coeficiente de correlación de Pearson no capturará esa relación.
- Es sensible a los valores atípicos (outliers). Los valores atípicos pueden afectar significativamente el valor de la correlación de Pearson.
- No implica causalidad. Una alta correlación entre dos variables no implica necesariamente que una variable cause la otra. La correlación no determina la dirección de la causalidad.

```python
pip install scipy
```



```python
from scipy.stats import pearsonr
```

***Calcular la correlación de pearson***
```python
correlacion, _ = pearsonr(df["sepal_length"], df["petal_length"])
print(f"La correlación de pearson entre sepal length y petal length es: {correlacion}")
```
$$Consola$$
![[Pasted image 20230909200727.png]]

## 5- Técnica Análisis de Clusters

El Análisis de Clusters, también conocido como Agrupamiento o Clustering en inglés, es una técnica de aprendizaje no supervisado en el campo del aprendizaje automático y la estadística. Su objetivo principal es dividir un conjunto de datos en grupos o clústeres, de modo que los elementos dentro de un clúster sean más similares entre sí que con los elementos de otros clústeres. En otras palabras, el análisis de clusters busca descubrir patrones naturales o estructuras intrínsecas en los datos.

```python
from sklearn.cluster import KMeans
```



```python
model = KMeans(n_clusters=3, random_state=42)
df["cluster"] = model.fit_predict(df.iloc[:,:-2])
df
```
$$Consola$$
![[Pasted image 20230909201404.png]]




```python
sns.scatterplot(data=df, x="sepal_length", y="petal_length", hue="cluster")
plt.show()
```
$$Consola$$
![[Pasted image 20230909201421.png]]


## 6-  Técnica Z-Score
El Z-Score, también conocido como puntaje Z, es una técnica estadística utilizada para evaluar cuán lejos de la media se encuentra un valor en una distribución de datos y cuántas desviaciones estándar está por encima o por debajo de la media. El Z-Score se utiliza comúnmente para identificar valores atípicos (outliers) en un conjunto de datos.

***CALCULAR EL Z-SCORE***
```python
df["z_score_sepal_length"] = np.abs((df["sepal_length"] - df["sepal_length"].mean())/df["sepal_length"].std())
df
```
$$Consola$$
![[Pasted image 20230909202534.png]]

```python
outliers = df[df["z_score_sepal_length"] > 2]
outliers
```
$$Consola$$
![[Pasted image 20230909202609.png]]

```python
sns.scatterplot(data = df, x="sepal_length", y="petal_length", hue="species")
sns.scatterplot(data = outliers, x="sepal_length", y="petal_length", c="red")
```
$$Consola$$
![[Pasted image 20230909202636.png]]






___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%