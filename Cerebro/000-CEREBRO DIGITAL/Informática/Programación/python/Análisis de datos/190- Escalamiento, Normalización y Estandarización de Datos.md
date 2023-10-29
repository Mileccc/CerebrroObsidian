---
ID: 190
tags: 
nombre: Escalamiento, Normalización y Estandarización de Datos
---
___
# Escalamiento, Normalización y Estandarización de Datos
![](https://www.youtube.com/watch?v=-VuR14Qyl7E&t=447s&ab_channel=C%C3%B3digoM%C3%A1quina)

___
  

```python
import pandas as pd
import matplotlib.pyplot as plt
from sklearn import preprocessing
  
datos = pd.read_csv("datos_personas.csv")
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

      <th>carros</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>22273.577534</td>

      <td>3</td>

    </tr>

    <tr>

      <th>1</th>

      <td>8961.047249</td>

      <td>1</td>

    </tr>

    <tr>

      <th>2</th>

      <td>7437.977263</td>

      <td>2</td>

    </tr>

    <tr>

      <th>3</th>

      <td>12064.915290</td>

      <td>2</td>

    </tr>

    <tr>

      <th>4</th>

      <td>9296.396167</td>

      <td>1</td>

    </tr>

    <tr>

      <th>...</th>

      <td>...</td>

      <td>...</td>

    </tr>

    <tr>

      <th>995</th>

      <td>9998.522402</td>

      <td>0</td>

    </tr>

    <tr>

      <th>996</th>

      <td>6867.097603</td>

      <td>2</td>

    </tr>

    <tr>

      <th>997</th>

      <td>9757.539280</td>

      <td>1</td>

    </tr>

    <tr>

      <th>998</th>

      <td>11044.031510</td>

      <td>1</td>

    </tr>

    <tr>

      <th>999</th>

      <td>1222.253800</td>

      <td>0</td>

    </tr>

  </tbody>

</table>

<p>1000 rows × 2 columns</p>

</div>

  
## Graficando los datos en escala original

```python
fig = plt.figure(figsize=(15, 5))
ax1 = fig.add_subplot(1, 3, 1)
ax2 = fig.add_subplot(1, 3, 2)
ax3 = fig.add_subplot(1, 3, 3)
ax1.set_title("Datos Originales Juntos")
ax1.plot(datos)
ax2.set_title("Ingreso")
ax2.plot(datos["ingreso"], linewidth=0, marker="o", color="blue", markersize=6)
ax3.set_title("Carros")
ax3.plot(datos["carros"], linewidth=0, marker="+", color="orange", markersize=16)
plt.show()
```

  
  

![[000-CEREBRO DIGITAL/Informática/Programación/python/Análisis de datos/ANEXOS/output_4_0.png|1200]]

  

## Distribución de los datos originales


```python
fig = plt.figure(figsize=(8, 8))
ax1 = fig.add_subplot(2, 2, 1)
ax2 = fig.add_subplot(2, 2, 2)
ax3 = fig.add_subplot(2, 2, 3)
ax4 = fig.add_subplot(2, 2, 4)
ax1.set_title("Ingreso")
ax1.plot(datos["ingreso"], linewidth=0, marker="o", color="blue", markersize=6)
ax2.set_title("Carros")
ax2.plot(datos["carros"], linewidth=0, marker="+", color="orange", markersize=16)
ax3.set_title("Ingreso")
ax3.hist(datos["ingreso"], bins=100, color="blue")
ax4.set_title("Carros")
ax4.hist(datos["carros"], color="orange")
plt.show()
```


![[000-CEREBRO DIGITAL/Informática/Programación/python/Análisis de datos/ANEXOS/output_7_0.png|1200]]

## Escala en función del mínimo y máximo

```python
datos_min_max = preprocessing.MinMaxScaler().fit_transform(datos)
  
datos_min_max
```

    array([[1.        , 1.        ],
           [0.36761553, 0.33333333],
           [0.29526521, 0.66666667],
           ...,
           [0.40545125, 0.33333333],
           [0.46656343, 0.33333333],
           [0.        , 0.        ]])

## Normaliza en función de la Norma del Vector

```python
datos_normalizer = preprocessing.Normalizer().transform(datos.T)
datos_normalizer = datos_normalizer.T
# normalizado = X / raíz_cuadrada( X_1^2 + X_2^2 + X_3^2 + ...)
  
datos_normalizer
```


    array([[0.06777903, 0.05886881],
           [0.02726868, 0.01962294],
           [0.02263394, 0.03924588],
           ...,
           [0.02969242, 0.01962294],
           [0.03360725, 0.01962294],
           [0.00371935, 0.        ]])

## Estandariza (desv_std = 1, media = 0)

```python
datos_standard_scaler = preprocessing.StandardScaler().fit_transform(datos)
# estandarizado = (X - media) / std
  
datos_robust_scaler = preprocessing.RobustScaler().fit_transform(datos)
# estandarizado = (X - rango_intercuartílico) / std
  
datos_standard_scaler, datos_robust_scaler
```

    (array([[ 4.81555174,  1.70892042],
            [-0.4413019 , -0.23193185],
            [-1.04273197,  0.73849429],
            ...,
            [-0.12678303, -0.23193185],
            [ 0.38122719, -0.23193185],
            [-3.49719763, -1.20235798]]),
     array([[ 3.70548334,  1.        ],
            [-0.3376601 ,  0.        ],
            [-0.80023109,  0.5       ],
            ...,
            [-0.09575781,  0.        ],
            [ 0.29496225,  0.        ],
            [-2.68800607, -0.5       ]]))

### Rango Intercuartílico

![[IRQmejorado (1).png]]


## Columna 'ingreso': Comparación de métodos


```python
# convierte vectores de numpy a DataFrames para graficarlos
datos_min_max = pd.DataFrame(datos_min_max, columns=["ingreso", "carros"])
datos_normalizer = pd.DataFrame(datos_normalizer, columns=["ingreso", "carros"])
datos_standard_scaler = pd.DataFrame(datos_standard_scaler, columns=["ingreso", "carros"])
datos_robust_scaler = pd.DataFrame(datos_robust_scaler, columns=["ingreso", "carros"])
  
# crea una figura con 5 subfiguras para comparar los métodos
fig = plt.figure(figsize=(15, 3))
ax1 = fig.add_subplot(1, 5, 1)
ax2 = fig.add_subplot(1, 5, 2)
ax3 = fig.add_subplot(1, 5, 3)
ax4 = fig.add_subplot(1, 5, 4)
ax5 = fig.add_subplot(1, 5, 5)
  
# crea y personaliza series de datos
ax1.set_title("INGRESO")
ax1.plot(datos["ingreso"], linewidth=0, marker="*", color="red", markersize=4)
  
ax2.set_title("Min Max")
ax2.plot(datos_min_max["ingreso"], linewidth=0, marker="*", color="red", markersize=4)
  
ax3.set_title("Normalizer")
ax3.plot(datos_normalizer["ingreso"], linewidth=0, marker="*", color="red", markersize=4)
#ax3.set_ylim(0, 1)
  
ax4.set_title("Standard Scaler")
ax4.plot(datos_standard_scaler["ingreso"], linewidth=0, marker="*", color="red", markersize=4)
  
ax5.set_title("Robust Scaler")
ax5.plot(datos_robust_scaler["ingreso"], linewidth=0, marker="*", color="red", markersize=4)
  
plt.show()
  
# crea una figura con 5 subfiguras para mostrar histogramas
fig = plt.figure(figsize=(15, 3))
ax1 = fig.add_subplot(1, 5, 1)
ax2 = fig.add_subplot(1, 5, 2)
ax3 = fig.add_subplot(1, 5, 3)
ax4 = fig.add_subplot(1, 5, 4)
ax5 = fig.add_subplot(1, 5, 5)
  
# crea y personaliza series de datos de los histogramas
ax1.set_title("INGRESO")
ax1.hist(datos["ingreso"], color="red", bins=100)
  
ax2.set_title("Min Max")
ax2.hist(datos_min_max["ingreso"], color="red", bins=100)
  
ax3.set_title("Normalizer")
ax3.hist(datos_normalizer["ingreso"], color="red", bins=100)
  
ax4.set_title("Standard Scaler")
ax4.hist(datos_standard_scaler["ingreso"], color="red", bins=100)

ax5.set_title("Robust Scaler")
ax5.hist(datos_robust_scaler["ingreso"], color="red", bins=100)
  
plt.show()
```

  
  ![[output_18_0.png|1200]]
  
  
![[output_18_1.png|1200]]
  
## Columna 'carros': Comparación de métodos


```python
# crea una figura con 5 subfiguras para comparar los métodos
fig = plt.figure(figsize=(15, 3))
ax1 = fig.add_subplot(1, 5, 1)
ax2 = fig.add_subplot(1, 5, 2)
ax3 = fig.add_subplot(1, 5, 3)
ax4 = fig.add_subplot(1, 5, 4)
ax5 = fig.add_subplot(1, 5, 5)
  
# crea y personaliza series de datos
ax1.set_title("CARROS")
ax1.plot(datos["carros"], linewidth=0, marker="*", color="blue", markersize=4)
  
ax2.set_title("Min Max")
ax2.plot(datos_min_max["carros"], linewidth=0, marker="*", color="blue", markersize=4)
  
ax3.set_title("Normalizer")
ax3.plot(datos_normalizer["carros"], linewidth=0, marker="*", color="blue", markersize=4)
ax3.set_ylim(0, 1)
  
ax4.set_title("Standard Scaler")
ax4.plot(datos_standard_scaler["carros"], linewidth=0, marker="*", color="blue", markersize=4)
  
ax5.set_title("Robust Scaler")
ax5.plot(datos_robust_scaler["carros"], linewidth=0, marker="*", color="blue", markersize=4)
  
plt.show()
  
# crea una figura con 5 subfiguras para mostrar histogramas
fig = plt.figure(figsize=(15, 3))
ax1 = fig.add_subplot(1, 5, 1)
ax2 = fig.add_subplot(1, 5, 2)
ax3 = fig.add_subplot(1, 5, 3)
ax4 = fig.add_subplot(1, 5, 4)
ax5 = fig.add_subplot(1, 5, 5)
  
# crea y personaliza series de datos de los histogramas
ax1.set_title("CARROS")
ax1.hist(datos["carros"], color="blue")
  
ax2.set_title("Min Max")
ax2.hist(datos_min_max["carros"], color="blue")
  
ax3.set_title("Normalizer")
ax3.hist(datos_normalizer["carros"], color="blue")
  
ax4.set_title("Standard Scaler")
ax4.hist(datos_standard_scaler["carros"], color="blue")
  
ax5.set_title("Robust Scaler")
ax5.hist(datos_robust_scaler["carros"], color="blue")
  
plt.show()
```

  
  ![[output_21_0.png|1200]]

![[output_21_1.png|1200]]



___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%