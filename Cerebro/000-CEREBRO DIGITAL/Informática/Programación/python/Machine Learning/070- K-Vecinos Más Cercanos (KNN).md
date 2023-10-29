---
ID: 70
tags: 
nombre: K-Vecinos Más Cercanos (KNN)
---
___
# K-Vecinos Más Cercanos (KNN)
![](https://www.youtube.com/watch?v=XN6fChNqfbs&ab_channel=C%C3%B3digoM%C3%A1quina)

___
### Datos de clientes bancarios: crédito

  
  

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn import preprocessing
from sklearn.neighbors import KNeighborsClassifier
  
clientes = pd.read_csv("creditos.csv")
clientes
```

<div>

<style scoped>

    .dataframe tbody tr th:only-of-type {

        vertical-align: middle;

    }

  

    .dataframe tbody tr th {

        vertical-align: top;

    }

  

    .dataframe thead th {

        text-align: right;

    }

</style>

<table border="1" class="dataframe">

  <thead>

    <tr style="text-align: right;">

      <th></th>

      <th>edad</th>

      <th>credito</th>

      <th>cumplio</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>18</td>

      <td>363112</td>

      <td>0</td>

    </tr>

    <tr>

      <th>1</th>

      <td>19</td>

      <td>477965</td>

      <td>1</td>

    </tr>

    <tr>

      <th>2</th>

      <td>20</td>

      <td>239072</td>

      <td>0</td>

    </tr>

    <tr>

      <th>3</th>

      <td>22</td>

      <td>195265</td>

      <td>0</td>

    </tr>

    <tr>

      <th>4</th>

      <td>22</td>

      <td>482174</td>

      <td>0</td>

    </tr>

    <tr>

      <th>...</th>

      <td>...</td>

      <td>...</td>

      <td>...</td>

    </tr>

    <tr>

      <th>195</th>

      <td>55</td>

      <td>100000</td>

      <td>0</td>

    </tr>

    <tr>

      <th>196</th>

      <td>55</td>

      <td>523144</td>

      <td>0</td>

    </tr>

    <tr>

      <th>197</th>

      <td>55</td>

      <td>543771</td>

      <td>0</td>

    </tr>

    <tr>

      <th>198</th>

      <td>56</td>

      <td>285288</td>

      <td>0</td>

    </tr>

    <tr>

      <th>199</th>

      <td>57</td>

      <td>422969</td>

      <td>0</td>

    </tr>

  </tbody>

</table>

<p>200 rows × 3 columns</p>

</div>

## Pagadores VS Deudores


```python
buenos = clientes[clientes["cumplio"]==1]
malos = clientes[clientes["cumplio"]==0]
```


## Gráfica: Pagadores VS Deudores

```python
plt.scatter(buenos["edad"], buenos["credito"],
            marker="*", s=150, color="skyblue",
            label="Sí pagó (Clase: 1)")
  
plt.scatter(malos["edad"], malos["credito"],
            marker="*", s=150, color="red",
            label="No pagó (Clase: 0)")
  
plt.ylabel("Monto del crédito")
plt.xlabel("Edad")
plt.legend(bbox_to_anchor=(1, 0.2))
plt.show()
```

  
  
![[output_7_0 2.png|700]]


## Preparación de los datos (Escalar)

```python
datos = clientes[["edad", "credito"]]
clase = clientes["cumplio"]
  
escalador = preprocessing.MinMaxScaler()
  
datos = escalador.fit_transform(datos)
```

  
## Creación del Modelo KNN
### Valor de K

```python
clasificador = KNeighborsClassifier(n_neighbors=3)
  
clasificador.fit(datos, clase)
```


    KNeighborsClassifier(n_neighbors=3)

## Nuevo Solicitante (Clasificación)  

```python
edad = 53
monto = 350000
  
#Escalar los datos del nuevo solicitante
solicitante = escalador.transform([[edad, monto]])
  
#Calcular clase y probabilidades
print("Clase:", clasificador.predict(solicitante))
print("Probabilidades por clase",
      clasificador.predict_proba(solicitante))
  
#Código para graficar
plt.scatter(buenos["edad"], buenos["credito"],
            marker="*", s=150, color="skyblue", label="Sí pagó (Clase: 1)")
plt.scatter(malos["edad"], malos["credito"],
            marker="*", s=150, color="red", label="No pagó (Clase: 0)")
plt.scatter(edad, monto, marker="P", s=250, color="green", label="Solicitante")
plt.ylabel("Monto del crédito")
plt.xlabel("Edad")
plt.legend(bbox_to_anchor=(1, 0.3))
plt.show()
```
    Clase: [0]

    Probabilidades por clase [[0.66666667 0.33333333]]

  
  ![[output_16_1.png|700]]
  
## Regiones de las clases
#### Pagadores vs Deudores


```python
#Datos sinténticos de todos los posibles solicitantes
creditos = np.array([np.arange(100000, 600010, 1000)]*43).reshape(1, -1)
edades = np.array([np.arange(18, 61)]*501).reshape(1, -1)
todos = pd.DataFrame(np.stack((edades, creditos), axis=2)[0],
                     columns=["edad", "credito"])
  
#Escalar los datos
solicitantes = escalador.transform(todos)
  
#Predecir todas las clases
clases_resultantes = clasificador.predict(solicitantes)
  
#Código para graficar
buenos = todos[clases_resultantes==1]
malos = todos[clases_resultantes==0]
plt.scatter(buenos["edad"], buenos["credito"],
            marker="*", s=150, color="skyblue", label="Sí pagará (Clase: 1)")
plt.scatter(malos["edad"], malos["credito"],
            marker="*", s=150, color="red", label="No pagará (Clase: 0)")
plt.ylabel("Monto del crédito")
plt.xlabel("Edad")
plt.legend(bbox_to_anchor=(1, 0.2))
plt.show()
```

  
  
![[000-CEREBRO DIGITAL/Informática/Programación/python/Machine Learning/ANEXOS/output_19_0.png|1200]]



___

%%
tags: #pagmachine_learning #python   

Vínculos: [[000-Menú Machine Learning 📃|Menú Machine Learning 📃]] 
%%