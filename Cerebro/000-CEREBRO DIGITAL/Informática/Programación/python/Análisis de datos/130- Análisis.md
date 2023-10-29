---
ID: 130
"tags:": 
"nombre:": Análisis
---
___
# Análisis
___
## Análisis Exploratorio y Análisis Univariado
___
![](https://www.youtube.com/watch?v=2EzqI9FDJ04&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=20)

___
```python
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
  
sns.set(style="darkgrid")
  
df = sns.load_dataset("tips")
df.head()
```
$$Consola$$
![[Pasted image 20230906160847.png]]



```python
df.info()
```
$$Consola$$
![[Pasted image 20230906160914.png]]


```python
df.describe()
```
$$Consola$$
![[Pasted image 20230906160945.png]]

___

### Análisis univariado

El **análisis univariado** es una técnica estadística que se utiliza para estudiar y describir una sola variable en un conjunto de datos sin considerar ninguna relación con otras variables. En este tipo de análisis, nos enfocamos en comprender las características y propiedades de una variable individualmente. Algunos aspectos clave del análisis univariado incluyen:

- **Medidas de tendencia central**: Esto implica calcular valores como la media, la mediana y la moda para entender dónde se concentran los datos en la variable.
    
- **Medidas de dispersión**: Aquí evaluamos la variabilidad de los datos, utilizando medidas como la desviación estándar o el rango intercuartílico.
    
- **Visualización**: A menudo, se representan los datos mediante gráficos como histogramas, gráficos de barras o diagramas de caja para visualizar la distribución de la variable.
    
- **Resumen estadístico**: Se resumen los principales hallazgos del análisis univariado en un informe que incluye estadísticas clave y visualizaciones.
___
#### En gráfica de barras (frecuencia)

```python
sns.histplot(data=df, x="total_bill")
plt.plot()
```
$$Consola$$
![[Pasted image 20230906160803.png]]
___
#### En gráfica de cajas

```python
sns.boxplot(data=df, x="total_bill")
plt.plot()
```
$$Consola$$
![[Pasted image 20230906161716.png]]
___
#### Gráfica de Kde (densidad)

```python
sns.kdeplot(data=df , x="total_bill")
plt.show()
```
$$Consola$$
![[Pasted image 20230906161826.png]]

___

### Análisis exploratorio
Por otro lado, el **análisis exploratorio** se refiere a un enfoque más amplio y flexible en la exploración de datos. A diferencia del análisis univariado, el análisis exploratorio considera múltiples variables y busca descubrir patrones, relaciones y tendencias en los datos. Algunos aspectos clave del análisis exploratorio incluyen:

- **Análisis de correlación**: Se examina cómo las variables se relacionan entre sí. Esto puede ayudar a identificar asociaciones o dependencias entre variables.
    
- **Visualización multidimensional**: Utilizando gráficos de dispersión o mapas de calor, se representan las relaciones entre múltiples variables de manera simultánea.
    
- **Identificación de valores atípicos**: Se busca detectar valores inusuales o atípicos que pueden tener un impacto significativo en el análisis.
    
- **Análisis de tendencias a lo largo del tiempo**: Si los datos tienen un componente temporal, se analizan las tendencias y patrones a lo largo del tiempo.
    
- **Modelado inicial**: A veces, se realizan modelos preliminares para comprender mejor la relación entre las variables y predecir resultados.
    

En resumen, el análisis univariado se enfoca en una sola variable a la vez y se centra en su descripción, mientras que el análisis exploratorio abarca un enfoque más amplio e incluye la exploración de múltiples variables para descubrir patrones y relaciones en los datos. Ambos son componentes esenciales en la exploración y comprensión de conjuntos de datos.
___
#### Análisis exploratorio bivariado
El **análisis exploratorio bivariado** se centra en el estudio de la relación entre dos variables en un conjunto de datos. A diferencia del análisis univariado que se enfoca en una sola variable, el análisis bivariado explora cómo dos variables interactúan entre sí. Algunos aspectos clave del análisis exploratorio bivariado incluyen:

- **Gráficos de dispersión**: Se utilizan gráficos de dispersión para visualizar la relación entre las dos variables. Estos gráficos muestran cómo los puntos de datos se distribuyen en un plano bidimensional, lo que puede revelar patrones como correlaciones positivas, negativas o la ausencia de correlación.
    
- **Coeficiente de correlación**: Se calcula el coeficiente de correlación, como el coeficiente de correlación de Pearson, para cuantificar la fuerza y la dirección de la relación entre las dos variables. Un valor cercano a 1 indica una correlación positiva, cerca de -1 indica una correlación negativa y cerca de 0 indica una falta de correlación.
    
- **Análisis de regresión**: En el análisis bivariado, a menudo se realiza un análisis de regresión para modelar y predecir una variable en función de la otra. Esto puede ayudar a entender cómo una variable influye en la otra.

```python
sns.scatterplot(data=df, x="total_bill", y="tip")
```
$$Consola$$
![[Pasted image 20230906164214.png]]

Relación entre el precio total y la propina

```python
sns.barplot(data=df, x="sex", y="tip")
plt.show()
```
$$Consola$$
![[Pasted image 20230906164322.png]]

Relación entre el sexo y la propina

```python
sns.boxplot(data=df, x="sex", y="total_bill")
plt.show()
```
$$Consola$$
![[Pasted image 20230906164404.png]]

Relación entre gasto total entre un hombre y una mujer
___
#### Análisis exploratorio Multivariado
Por otro lado, el **análisis exploratorio multivariado** se enfoca en el estudio de las relaciones entre tres o más variables en un conjunto de datos. Este tipo de análisis es más complejo y poderoso, ya que puede revelar patrones y asociaciones más sofisticados. Algunos aspectos clave del análisis exploratorio multivariado incluyen:

- **Análisis de correlación múltiple**: Se examina cómo múltiples variables se relacionan entre sí utilizando técnicas como la matriz de correlación. Esto permite identificar patrones complejos de correlación.
    
- **Análisis factorial**: Se utiliza el análisis factorial para reducir la dimensionalidad de los datos y encontrar patrones subyacentes en un conjunto de variables relacionadas.
    
- **Clustering**: Se aplican algoritmos de clustering para agrupar observaciones similares en grupos basados en múltiples variables. Esto puede revelar segmentos o categorías ocultas en los datos.
    
- **Análisis de componentes principales (PCA)**: El PCA es una técnica que reduce la dimensionalidad de los datos al identificar las direcciones principales de variación en un conjunto de variables. Esto puede simplificar la interpretación de los datos multivariados.

```python
sns.pairplot(df, hue="sex" )
plt.show()
```
$$Consola$$
![[Pasted image 20230906164626.png]]

##### Caso practico


```python
sns.barplot(data=df, x="day", y="tip", errorbar=None)
plt.title("Propinas promedio por día")
plt.show()
# Los domingos se paga más propina
```
$$Consola$$
![[Pasted image 20230906172335.png]]



```python
sns.barplot(data=df, x="time", y="tip", errorbar=None)
plt.title("Propinas promedio por tiempo")
plt.show()
# En la cena se paga más propina
```
$$Consola$$
![[Pasted image 20230906172404.png]]


```python
sns.barplot(data=df, x="smoker", y="tip", errorbar=None)
plt.title("Propinas promedio por fumador/no fumador")
plt.show()
# Cliente fumador o no, no afecta a la propina
```
$$Consola$$
![[Pasted image 20230906172433.png]]



##### Gráfico de barra de propinas promedio (Dia, sexo)
```python
sns.barplot(data=df, x="day", y="tip", hue="sex", errorbar=None)
plt.title("Propinas promedio por día y sexo")
plt.show()
```
$$Consola$$
![[Pasted image 20230906172457.png]]


##### Gráfico de barra de propinas promedio (tiempo, sexo)
```python
sns.barplot(data=df, x="time", y="tip", hue="sex", errorbar=None)
plt.title("Propinas promedio por día y sexo")
plt.show()
```
$$Consola$$
![[Pasted image 20230906172525.png]]


##### Gráfico de barra de propinas promedio (fumador, sexo)
```python
sns.barplot(data=df, x="smoker", y="tip", hue="sex", errorbar=None)
plt.title("Propinas promedio por día y sexo")
plt.show()
```
$$Consola$$
![[Pasted image 20230906172555.png]]


#### Gráfico de dispersión entre size y tip

```python
sns.scatterplot(data=df, x="size", y="tip")
plt.title("Relación entre tamaño de fiesta y propinas")
plt.show()
```
$$Consola$$
![[Pasted image 20230907202432.png]]

#### Gráfico de barras de propinas promedio por tamaño de la fiesta
```python
sns.barplot(data=df, x="size", y="tip", errorbar=None)
plt.title("Propinas promedio por tamaño de la fiesta")
plt.show()
```
$$Consola$$
![[Pasted image 20230907202459.png]]


#### Calcule el porcentaje de propina y lo agregamos al DataFrame
```python
df["tip_percentage"] = (df["tip"]/df["total_bill"])*100
df
```
$$Consola$$
![[Pasted image 20230907202534.png]]

#### Gráfico de barras de porcentaje de propina promedio por sexo
```python
sns.barplot(data=df, x="sex", y="tip_percentage", errorbar=None)
plt.title("Porcentaje de propina promedio por sexo")
plt.show()
```
$$Consola$$
![[Pasted image 20230907202559.png]]


#### Gráfico de porcentaje de propina promedio por día
```python
sns.barplot(data=df, x="day", y="tip_percentage", errorbar=None)
plt.title("Porcentaje de propina promedio por día")
plt.show()
```
$$Consola$$
![[Pasted image 20230907202624.png]]


#### Gráfico de porcentaje de propina promedio horario
```python
sns.barplot(data=df, x="time", y="tip_percentage", errorbar=None)
plt.title("Porcentaje de propina promedio por tiempo")
plt.show()
```
$$Consola$$
![[Pasted image 20230907202652.png]]

#### Gráfico de porcentaje de propina promedio por fumador/no fumador
```python
sns.barplot(data=df, x="smoker", y="tip_percentage", errorbar=None)
plt.title("Porcentaje de propina promedio por Fumador/noFumador")
plt.show()
```
$$Consola$$
![[Pasted image 20230907202713.png]]



___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%