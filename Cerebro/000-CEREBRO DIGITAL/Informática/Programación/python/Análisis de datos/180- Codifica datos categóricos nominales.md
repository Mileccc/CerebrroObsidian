---
ID: 180
tags: 
nombre: Codifica datos categóricos nominales
---
___
# Codifica datos categóricos nominales
___
![](https://www.youtube.com/watch?v=cp7Uo5MSFSE&ab_channel=C%C3%B3digoM%C3%A1quina)

___
## Contexto y Datos (categóricos)


```python
import pandas as pd
  
datos = {"nombre" : ["Mariana", "Ana", "Elsa", "Gustavo",
                     "Pedro", "Raúl", "Carlos", "José", "Luis"],
         "saldo" : [10000.00, 8000.00, 9000.00, 2000.00,
                    2100.00, 12000.00, 5000.00, 10000.00, 200.00],
         "pais" : ["Argentina", "Bolivia", "Chile", "Colombia",
                   "Costa Rica", "Ecuador", "México", "Perú", "Perú"]}
  
datos = pd.DataFrame(datos)
datos["pais"] = datos["pais"].astype("category")
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

      <th>nombre</th>

      <th>saldo</th>

      <th>pais</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>Mariana</td>

      <td>10000.0</td>

      <td>Argentina</td>

    </tr>

    <tr>

      <th>1</th>

      <td>Ana</td>

      <td>8000.0</td>

      <td>Bolivia</td>

    </tr>

    <tr>

      <th>2</th>

      <td>Elsa</td>

      <td>9000.0</td>

      <td>Chile</td>

    </tr>

    <tr>

      <th>3</th>

      <td>Gustavo</td>

      <td>2000.0</td>

      <td>Colombia</td>

    </tr>

    <tr>

      <th>4</th>

      <td>Pedro</td>

      <td>2100.0</td>

      <td>Costa Rica</td>

    </tr>

    <tr>

      <th>5</th>

      <td>Raúl</td>

      <td>12000.0</td>

      <td>Ecuador</td>

    </tr>

    <tr>

      <th>6</th>

      <td>Carlos</td>

      <td>5000.0</td>

      <td>México</td>

    </tr>

    <tr>

      <th>7</th>

      <td>José</td>

      <td>10000.0</td>

      <td>Perú</td>

    </tr>

    <tr>

      <th>8</th>

      <td>Luis</td>

      <td>200.0</td>

      <td>Perú</td>

    </tr>

  </tbody>

</table>

</div>

#  INAPROPIADA Codificación con Reemplazo

```python
datos_sesgados = datos.copy()
  
reemplazos = {"Argentina" : 1,
             "Bolivia" : 2,
             "Chile" : 3,
             "Colombia" : 4,                        
             "Costa Rica" : 5,
             "Ecuador" : 6,
             "México" : 7,
             "Perú" : 8}
  
datos_sesgados["pais"].replace(reemplazos, inplace=True)
datos_sesgados
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

      <th>nombre</th>

      <th>saldo</th>

      <th>pais</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>Mariana</td>

      <td>10000.0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>1</th>

      <td>Ana</td>

      <td>8000.0</td>

      <td>2</td>

    </tr>

    <tr>

      <th>2</th>

      <td>Elsa</td>

      <td>9000.0</td>

      <td>3</td>

    </tr>

    <tr>

      <th>3</th>

      <td>Gustavo</td>

      <td>2000.0</td>

      <td>4</td>

    </tr>

    <tr>

      <th>4</th>

      <td>Pedro</td>

      <td>2100.0</td>

      <td>5</td>

    </tr>

    <tr>

      <th>5</th>

      <td>Raúl</td>

      <td>12000.0</td>

      <td>6</td>

    </tr>

    <tr>

      <th>6</th>

      <td>Carlos</td>

      <td>5000.0</td>

      <td>7</td>

    </tr>

    <tr>

      <th>7</th>

      <td>José</td>

      <td>10000.0</td>

      <td>8</td>

    </tr>

    <tr>

      <th>8</th>

      <td>Luis</td>

      <td>200.0</td>

      <td>8</td>

    </tr>

  </tbody>

</table>

</div>


# Codificación de Categorías One-hot

```python
from sklearn.preprocessing import OneHotEncoder
  
codificador = OneHotEncoder()
  
codificacion = codificador.fit_transform(datos[["pais"]])
  
#print(type(codificacion))
#print(codificacion)
#print(codificacion.toarray())
  
nuevas_cols = pd.DataFrame(codificacion.toarray(),
                           columns=codificador.categories_)
print(nuevas_cols)
  
datos = pd.concat([datos, nuevas_cols], axis="columns")
datos
```

  
      Argentina Bolivia Chile Colombia Costa Rica Ecuador México Perú
    0       1.0     0.0   0.0      0.0        0.0     0.0    0.0  0.0
    1       0.0     1.0   0.0      0.0        0.0     0.0    0.0  0.0
    2       0.0     0.0   1.0      0.0        0.0     0.0    0.0  0.0
    3       0.0     0.0   0.0      1.0        0.0     0.0    0.0  0.0
    4       0.0     0.0   0.0      0.0        1.0     0.0    0.0  0.0
    5       0.0     0.0   0.0      0.0        0.0     1.0    0.0  0.0
    6       0.0     0.0   0.0      0.0        0.0     0.0    1.0  0.0
    7       0.0     0.0   0.0      0.0        0.0     0.0    0.0  1.0
    8       0.0     0.0   0.0      0.0        0.0     0.0    0.0  1.0

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

      <th>nombre</th>

      <th>saldo</th>

      <th>pais</th>

      <th>(Argentina,)</th>

      <th>(Bolivia,)</th>

      <th>(Chile,)</th>

      <th>(Colombia,)</th>

      <th>(Costa Rica,)</th>

      <th>(Ecuador,)</th>

      <th>(México,)</th>

      <th>(Perú,)</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>Mariana</td>

      <td>10000.0</td>

      <td>Argentina</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>1</th>

      <td>Ana</td>

      <td>8000.0</td>

      <td>Bolivia</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>2</th>

      <td>Elsa</td>

      <td>9000.0</td>

      <td>Chile</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>3</th>

      <td>Gustavo</td>

      <td>2000.0</td>

      <td>Colombia</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>4</th>

      <td>Pedro</td>

      <td>2100.0</td>

      <td>Costa Rica</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>5</th>

      <td>Raúl</td>

      <td>12000.0</td>

      <td>Ecuador</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>6</th>

      <td>Carlos</td>

      <td>5000.0</td>

      <td>México</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>7</th>

      <td>José</td>

      <td>10000.0</td>

      <td>Perú</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

    </tr>

    <tr>

      <th>8</th>

      <td>Luis</td>

      <td>200.0</td>

      <td>Perú</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

    </tr>

  </tbody>

</table>

</div>


```python
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

      <th>nombre</th>

      <th>saldo</th>

      <th>pais</th>

      <th>(Argentina,)</th>

      <th>(Bolivia,)</th>

      <th>(Chile,)</th>

      <th>(Colombia,)</th>

      <th>(Costa Rica,)</th>

      <th>(Ecuador,)</th>

      <th>(México,)</th>

      <th>(Perú,)</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>Mariana</td>

      <td>10000.0</td>

      <td>Argentina</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>1</th>

      <td>Ana</td>

      <td>8000.0</td>

      <td>Bolivia</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>2</th>

      <td>Elsa</td>

      <td>9000.0</td>

      <td>Chile</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>3</th>

      <td>Gustavo</td>

      <td>2000.0</td>

      <td>Colombia</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>4</th>

      <td>Pedro</td>

      <td>2100.0</td>

      <td>Costa Rica</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>5</th>

      <td>Raúl</td>

      <td>12000.0</td>

      <td>Ecuador</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>6</th>

      <td>Carlos</td>

      <td>5000.0</td>

      <td>México</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

      <td>0.0</td>

    </tr>

    <tr>

      <th>7</th>

      <td>José</td>

      <td>10000.0</td>

      <td>Perú</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

    </tr>

    <tr>

      <th>8</th>

      <td>Luis</td>

      <td>200.0</td>

      <td>Perú</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>0.0</td>

      <td>1.0</td>

    </tr>

  </tbody>

</table>

</div>


___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%