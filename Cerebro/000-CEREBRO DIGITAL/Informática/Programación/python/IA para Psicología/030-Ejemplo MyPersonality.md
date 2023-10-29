---
ID:: 030
tags:: #pagiapsicologia #python  #pagpython 
nombre:: "Ejemplo MyPersonality"
---
___
# Ejemplo MyPersonality
![](https://youtu.be/epSFqaMICcw?si=4Pll4TU9ExNKKu01&t=4993)

___
La prueba Big5 (Costa y Mac Crae 1985, Goldberg et al. 2006) es una taxonomía o clasificación de rasgos de personalidad que analiza la composición de cinco dimensiones de personalidad en su sentido más amplio. Esta disertación se publicó en el Psychological Review, 41, 1-32. los 5 factores son:

Apertura a la experiencia (inventivo / curioso vs consistente /cauteloso) O
Escrupulosidad (eficiente / organizado vs extravagante / descuidado) C
Extraversión (sociable / enérgico vs solitario / reservado) E
Amabilidad (amigable / compasivo vs desafiante / insensible) A
Neuroticismo ( susceptible / nervioso vs resistente / seguro) N

```python
import pandas as pd
import plotly.express as px
from scipy.stats import pearsonr
import seaborn as sns
import numpy as np
import matplotlib.pyplot as plt
import statsmodels.api as sm
```

### DataSet del DataFrame
```python
df = pd.read_csv("https://unket.s3-sa-east-1.amazonaws.com/data/mypersonality.csv")
```

### visualizamos la cabecera de los datos
```python
df.head()
```
$$Consola$$
![[Pasted image 20230827202523.png]]

### Eliminamos los duplicados de la columna de IDs
```python
df = df.drop_duplicates(subset="#AUTHID")
```

### Si visualizamos el DataFrame de nuevo ya no tendremos datos duplicados con el mismo ID
```python
df.head()
```
$$Consola$$
![[Pasted image 20230827203150.png]]

### Vemos forma del DataFrame con shape
```python
df.shape
```
$$Consola$$
![[Pasted image 20230827203346.png]]
Vemos que tenemos 250 personas y 20 columnas

### Visualizamos la columna con las cantidades de amigos
```python
df["NETWORKSIZE"]
```
$$Consola$$
![[Pasted image 20230827203523.png]]

#### Podemos pasarlo a una lista de Python
```python
cantidades_de_amigos = df["NETWORKSIZE"].tolist()
cantidades_de_amigos
```
$$Consola$$
![[Pasted image 20230827203828.png]]

#### Hacer un gráfico para visualizar los datos
```python
sns.distplot(cantidades_de_amigos)
```
$$Consola$$
![[Pasted image 20230829080836.png]]

#### Calcular la mediana de los amigos

```python
np.median(cantidades_de_amigos)
```
$$Consola$$
![[Pasted image 20230829080938.png]]

#### Calcular la media o promedio
```python
np.mean(cantidades_de_amigos)
```
$$Consola$$
![[Pasted image 20230829081010.png]]

#### Hacemos una correlación entre la extroversión y la cantidad de amigos
```python
pearsonr(df["sEXT"], df["NETWORKSIZE"])
```
$$Consola$$
![[Pasted image 20230829081052.png]]

#### Hacemos la correlación entre Neuroticismo y Cantidad de amigos
```python
pearsonr(df["sNEU"], df["NETWORKSIZE"])
```
$$Consola$$
![[Pasted image 20230829081131.png]]

#### Hacemos la correlación entre amabilidad y Cantidad de amigos
```python
pearsonr(df["sAGR"], df["NETWORKSIZE"])
```
$$Consola$$
![[Pasted image 20230829081218.png]]

#### Graficamos la correlación entre la extroversión y la cantidad de amigos

Necesitaremos la librería statsmodels.api
```python
fig = px.scatter(df, x="sEXT", y="NETWORKSIZE", trendline="ols", trendline_color_override="red")
fig.show()
```
$$Consola$$
![[Pasted image 20230829081313.png]]


#DataFrame #duplicados #gráfico #media #promedio #mediana #correlación #scatter #pearsonr #distplot

___

```python

```
$$Consola$$




```python

```
$$Consola$$




```python

```
$$Consola$$






```python

```
$$Consola$$



```python

```
$$Consola$$




```python

```
$$Consola$$





```python

```
$$Consola$$





```python

```
$$Consola$$







```python

```
$$Consola$$




```python

```
$$Consola$$




```python

```
$$Consola$$




```python

```
$$Consola$$





```python

```
$$Consola$$




```python

```
$$Consola$$




```python

```
$$Consola$$





```python

```
$$Consola$$






```python

```
$$Consola$$





```python

```
$$Consola$$





```python

```
$$Consola$$






```python

```
$$Consola$$




```python

```
$$Consola$$






```python

```
$$Consola$$






```python

```
$$Consola$$



___

%%
tags: #pagiapsicologia #python  #pagpython 

Vínculos:   [[000-Menú IA Psicología 📃|Menú IA para Psicología📃]] , [[900-Algoritmos|Algoritmos]]
%%