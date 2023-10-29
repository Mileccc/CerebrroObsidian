---
ID: " 0"
tags: 
nombre: Regresión Lineal
---
___
# Regresión Lineal Simple
___
![](https://www.youtube.com/watch?v=1CGbP0l0iqo&ab_channel=C%C3%B3digoM%C3%A1quina)

## Suposiciones
<ul>

<li>Relación lineal</li>

<li>Normalidad</li>

<li>No multicolinealidad</li>

<li>No auto-correlación</li>

<li>Varianzas iguales</li>

</ul>
## Contexto  y Datos


```python
import pandas as pd
  
datos = pd.read_csv("datos/ingreso.csv")
datos
  
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

      <th>ingreso</th>

      <th>horas</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>9973.577534</td>

      <td>40.905476</td>

    </tr>

    <tr>

      <th>1</th>

      <td>8961.047249</td>

      <td>41.576483</td>

    </tr>

    <tr>

      <th>2</th>

      <td>7437.977263</td>

      <td>41.369239</td>

    </tr>

    <tr>

      <th>3</th>

      <td>12064.915290</td>

      <td>41.537211</td>

    </tr>

    <tr>

      <th>4</th>

      <td>9296.396167</td>

      <td>40.441203</td>

    </tr>

    <tr>

      <th>...</th>

      <td>...</td>

      <td>...</td>

    </tr>

    <tr>

      <th>995</th>

      <td>9998.522402</td>

      <td>41.110352</td>

    </tr>

    <tr>

      <th>996</th>

      <td>6867.097603</td>

      <td>40.617061</td>

    </tr>

    <tr>

      <th>997</th>

      <td>9757.539280</td>

      <td>40.798085</td>

    </tr>

    <tr>

      <th>998</th>

      <td>11044.031510</td>

      <td>41.443604</td>

    </tr>

    <tr>

      <th>999</th>

      <td>13222.253800</td>

      <td>41.402637</td>

    </tr>

  </tbody>

</table>

<p>1000 rows × 2 columns</p>

</div>


```python
import matplotlib.pyplot as plt
  
plt.ylabel("Ingreso ($)")
plt.xlabel("Promedio de horas semanales trabajadas")
plt.scatter(datos["horas"], datos["ingreso"], color="pink")
plt.show()
```

  
  
![[output_4_0 1.png|700]]

  

## Creación del Modelo de Regresión Lineal Simple


```python
from sklearn import linear_model
  
regresion = linear_model.LinearRegression()
  
horas = datos["horas"].values.reshape((-1, 1))
  
modelo = regresion.fit(horas, datos["ingreso"])
  
print("Intersección (b)", modelo.intercept_)
print("Pendiente (m)", modelo.coef_)
  
entrada = [[39.5], [40], [43], [43.5]]
modelo.predict(entrada)
  
plt.scatter(entrada, modelo.predict(entrada), color="red")
plt.plot(entrada, modelo.predict(entrada), color="black")
  
plt.ylabel("Ingreso ($)")
plt.xlabel("Promedio de horas semanales trabajadas")
plt.scatter(datos["horas"], datos["ingreso"], color="pink", alpha=0.55)
plt.show()
```

  
    Intersección (b) -112320.22713310868
    Pendiente (m) [2965.35614382]

  ![[output_7_1.png|700]]

___

%%
tags: #pagmachine_learning #python   

Vínculos: [[000-Menú Machine Learning 📃|Menú Machine Learning 📃]] 
%%