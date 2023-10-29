---
ID: 12
"tags:": 
nombre: Series y DataFrames (Código Máquina)
---
___
# Series y DataFrames (Código Máquina)
___
## 1- Series El Componente Principal de los DataFrames
![](https://www.youtube.com/watch?v=E7Tt458sTUE)

### Creación de una Serie

```python

import pandas as pd

  

indice = ["Juan", "Maria", "Francisco", "Pedro", "Luis"]

datos_lista = [40, 20, 36, 34, 20]

  

datos_dicc = {"Juan":40, "Maria":20, "Francisco":36, "Pedro":34, "Luis":20}

```

  
```python

serie = pd.Series(datos_lista, index=indice, dtype="i8")

serie

```


    Juan         40
    Maria        20
    Francisco    36
    Pedro        34
    Luis         20
    dtype: int64


```python

serie = pd.Series(datos_dicc)

serie

```

  
    Juan         40
    Maria        20
    Francisco    36
    Pedro        34
    Luis         20
    dtype: int64

### Atributos y acceso a los elementos de una Serie

```python

serie.dtype, serie.size, serie.index, serie.values

```

 
    (dtype('int64'),
     5,
     Index(['Juan', 'Maria', 'Francisco', 'Pedro', 'Luis'], dtype='object'),
     array([40, 20, 36, 34, 20], dtype=int64))

  
```python

for elemento in serie:

    print(elemento)

```

    40
    20
    36
    34
    20

```python

serie["Juan"], serie[["Juan", "Pedro"]]

```

    (40,
     Juan     40
     Pedro    34
     dtype: int64)

  

```python

serie[0], serie[0:3], serie[[0,3]]

```

    (40,
     Juan         40
     Maria        20
     Francisco    36
     dtype: int64,
     Juan     40
     Pedro    34
     dtype: int64)


### Métodos básicos comunes

```python

serie.astype("f8")

```

  
    Juan         40.0
    Maria        20.0
    Francisco    36.0
    Pedro        34.0
    Luis         20.0
    dtype: float64


```python

serie.value_counts()

```

  
    20    2
    34    1
    36    1
    40    1
    dtype: int64


```python

serie.sort_index(inplace=True)

serie

```

  
    Francisco    36
    Juan         40
    Luis         20
    Maria        20
    Pedro        34
    dtype: int64

  
```python

serie.sort_values(inplace=True)

serie

```

  
    Luis         20
    Maria        20
    Pedro        34
    Francisco    36
    Juan         40
    dtype: int64

### Operaciones vectoriales aritméticas + / - *


```python

serie*serie

```

  
    Luis          400
    Maria         400
    Pedro        1156
    Francisco    1296
    Juan         1600
    dtype: int64

### Funciones de estadística y de agregación básicas

```python

serie.max(), serie.min(), serie.argmax(), serie.argmin(), serie.sum()

```

    (40, 20, 4, 0, 150)


```python

serie.mode(), serie.mean(), serie.median(), serie.std(), serie.count()

```

  
    (0    20
     dtype: int64,
     30.0,
     34.0,
     9.38083151964686,
     5)

```python

serie.describe()

```

  
    count     5.000000
    mean     30.000000
    std       9.380832
    min      20.000000
    25%      20.000000
    50%      34.000000
    75%      36.000000
    max      40.000000
    dtype: float64


```python

serie.quantile(0)

```

  
    20.0


```python

serie.plot()

```

    <AxesSubplot:>

  ![[output_22_1.png|800]]
___
## 2- Creación y Manipulación de DataFrames
___
![](https://www.youtube.com/watch?v=DjQyHmy9AqQ)
### Creación de un DataFrame

```python

import pandas as pd

nombre_paises = ["China", "India", "Estados Unidos", "Indonesia", "Pakistán",
                 "Brasil", "Nigeria", "Bangladesh", "Rusia", "México"]
encabezado = ["poblacion", "porcentaje"]

datos = [[1439, 18.47],
        [1380, 17.70],
        [331, 4.25],
        [273, 3.51],
        [220, 2.83],
        [212, 2.73],
        [206, 2.64],
        [164, 2.11],
        [145, 1.87],
        [128, 1.65]]
  
paises = pd.DataFrame(datos, index=nombre_paises, columns=encabezado)
paises
  
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

      <th>poblacion</th>

      <th>porcentaje</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>China</th>

      <td>1439</td>

      <td>18.47</td>

    </tr>

    <tr>

      <th>India</th>

      <td>1380</td>

      <td>17.70</td>

    </tr>

    <tr>

      <th>Estados Unidos</th>

      <td>331</td>

      <td>4.25</td>

    </tr>

    <tr>

      <th>Indonesia</th>

      <td>273</td>

      <td>3.51</td>

    </tr>

    <tr>

      <th>Pakistán</th>

      <td>220</td>

      <td>2.83</td>

    </tr>

    <tr>

      <th>Brasil</th>

      <td>212</td>

      <td>2.73</td>

    </tr>

    <tr>

      <th>Nigeria</th>

      <td>206</td>

      <td>2.64</td>

    </tr>

    <tr>

      <th>Bangladesh</th>

      <td>164</td>

      <td>2.11</td>

    </tr>

    <tr>

      <th>Rusia</th>

      <td>145</td>

      <td>1.87</td>

    </tr>

    <tr>

      <th>México</th>

      <td>128</td>

      <td>1.65</td>

    </tr>

  </tbody>

</table>

</div>

  


```python

datos = {"China": [1439, 18.47],
         "India": [1380, 17.70],
         "Estados Unidos": [331, 4.25],
         "Indonesia": [273, 3.51],
         "Pakistán": [220, 2.83],
         "Brasil": [212, 2.73],
         "Nigeria": [206, 2.64],
         "Bangladesh": [164, 2.11],
         "Rusia": [145, 1.87],
         "México": [128, 1.65]}
  
paises = pd.DataFrame(datos, index=encabezado)
paises = paises.T
paises
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

      <th>poblacion</th>

      <th>porcentaje</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>China</th>

      <td>1439.0</td>

      <td>18.47</td>

    </tr>

    <tr>

      <th>India</th>

      <td>1380.0</td>

      <td>17.70</td>

    </tr>

    <tr>

      <th>Estados Unidos</th>

      <td>331.0</td>

      <td>4.25</td>

    </tr>

    <tr>

      <th>Indonesia</th>

      <td>273.0</td>

      <td>3.51</td>

    </tr>

    <tr>

      <th>Pakistán</th>

      <td>220.0</td>

      <td>2.83</td>

    </tr>

    <tr>

      <th>Brasil</th>

      <td>212.0</td>

      <td>2.73</td>

    </tr>

    <tr>

      <th>Nigeria</th>

      <td>206.0</td>

      <td>2.64</td>

    </tr>

    <tr>

      <th>Bangladesh</th>

      <td>164.0</td>

      <td>2.11</td>

    </tr>

    <tr>

      <th>Rusia</th>

      <td>145.0</td>

      <td>1.87</td>

    </tr>

    <tr>

      <th>México</th>

      <td>128.0</td>

      <td>1.65</td>

    </tr>

  </tbody>

</table>

</div>


### Atributos básicos de  un DataFrame
```python
paises.dtypes
```


    poblacion     float64
    porcentaje    float64
    dtype: object


```python
paises.values, paises.size
```

    (array([[1439.  ,   18.47],
            [1380.  ,   17.7 ],
            [ 331.  ,    4.25],
            [ 273.  ,    3.51],
            [ 220.  ,    2.83],
            [ 212.  ,    2.73],
            [ 206.  ,    2.64],
            [ 164.  ,    2.11],
            [ 145.  ,    1.87],
            [ 128.  ,    1.65]]),
     20)

  

```python
paises.index, paises.columns
```


    (Index(['China', 'India', 'Estados Unidos', 'Indonesia', 'Pakistán', 'Brasil',
            'Nigeria', 'Bangladesh', 'Rusia', 'México'],
           dtype='object'),
     Index(['poblacion', 'porcentaje'], dtype='object'))

### Acceso a los elementos de un DataFrame

```python
paises.poblacion
```


    China             1439.0
    India             1380.0
    Estados Unidos     331.0
    Indonesia          273.0
    Pakistán           220.0
    Brasil             212.0
    Nigeria            206.0
    Bangladesh         164.0
    Rusia              145.0
    México             128.0
    Name: poblacion, dtype: float64

```python
paises["poblacion"], paises[["poblacion", "porcentaje"]]
```


    (China             1439.0
     India             1380.0
     Estados Unidos     331.0
     Indonesia          273.0
     Pakistán           220.0
     Brasil             212.0
     Nigeria            206.0
     Bangladesh         164.0
     Rusia              145.0
     México             128.0
     Name: poblacion, dtype: float64,
                     poblacion  porcentaje
     China              1439.0       18.47
     India              1380.0       17.70
     Estados Unidos      331.0        4.25
     Indonesia           273.0        3.51
     Pakistán            220.0        2.83
     Brasil              212.0        2.73
     Nigeria             206.0        2.64
     Bangladesh          164.0        2.11
     Rusia               145.0        1.87
     México              128.0        1.65)


```python
paises["poblacion"][0], paises.poblacion[0], paises["poblacion"][0:3]
```


    (1439.0,
     1439.0,
     China             1439.0
     India             1380.0
     Estados Unidos     331.0
     Name: poblacion, dtype: float64)

 

```python
paises.iloc[0], paises.loc["China"]
```


    (poblacion     1439.00
     porcentaje      18.47
     Name: China, dtype: float64,
     poblacion     1439.00
     porcentaje      18.47
     Name: China, dtype: float64)

### Métodos básicos comunes de DataFrames

```python
paises["poblacion"] = paises["poblacion"].astype("int")
```

```python
paises.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Index: 10 entries, China to México
    Data columns (total 2 columns):
     #   Column      Non-Null Count  Dtype  
    ---  ------      --------------  -----  
     0   poblacion   10 non-null     int32  
     1   porcentaje  10 non-null     float64
    dtypes: float64(1), int32(1)
    memory usage: 520.0+ bytes

```python
paises.head(), paises.tail()
```
  

    (                poblacion  porcentaje
     China                1439       18.47
     India                1380       17.70
     Estados Unidos        331        4.25
     Indonesia             273        3.51
     Pakistán              220        2.83,
                 poblacion  porcentaje
     Brasil            212        2.73
     Nigeria           206        2.64
     Bangladesh        164        2.11
     Rusia             145        1.87
     México            128        1.65)


```python
paises.sort_index()
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

      <th>poblacion</th>

      <th>porcentaje</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>Bangladesh</th>

      <td>164</td>

      <td>2.11</td>

    </tr>

    <tr>

      <th>Brasil</th>

      <td>212</td>

      <td>2.73</td>

    </tr>

    <tr>

      <th>China</th>

      <td>1439</td>

      <td>18.47</td>

    </tr>

    <tr>

      <th>Estados Unidos</th>

      <td>331</td>

      <td>4.25</td>

    </tr>

    <tr>

      <th>India</th>

      <td>1380</td>

      <td>17.70</td>

    </tr>

    <tr>

      <th>Indonesia</th>

      <td>273</td>

      <td>3.51</td>

    </tr>

    <tr>

      <th>México</th>

      <td>128</td>

      <td>1.65</td>

    </tr>

    <tr>

      <th>Nigeria</th>

      <td>206</td>

      <td>2.64</td>

    </tr>

    <tr>

      <th>Pakistán</th>

      <td>220</td>

      <td>2.83</td>

    </tr>

    <tr>

      <th>Rusia</th>

      <td>145</td>

      <td>1.87</td>

    </tr>

  </tbody>

</table>

</div>

 

```python
paises
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

      <th>poblacion</th>

      <th>porcentaje</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>China</th>

      <td>1439</td>

      <td>18.47</td>

    </tr>

    <tr>

      <th>India</th>

      <td>1380</td>

      <td>17.70</td>

    </tr>

    <tr>

      <th>Estados Unidos</th>

      <td>331</td>

      <td>4.25</td>

    </tr>

    <tr>

      <th>Indonesia</th>

      <td>273</td>

      <td>3.51</td>

    </tr>

    <tr>

      <th>Pakistán</th>

      <td>220</td>

      <td>2.83</td>

    </tr>

    <tr>

      <th>Brasil</th>

      <td>212</td>

      <td>2.73</td>

    </tr>

    <tr>

      <th>Nigeria</th>

      <td>206</td>

      <td>2.64</td>

    </tr>

    <tr>

      <th>Bangladesh</th>

      <td>164</td>

      <td>2.11</td>

    </tr>

    <tr>

      <th>Rusia</th>

      <td>145</td>

      <td>1.87</td>

    </tr>

    <tr>

      <th>México</th>

      <td>128</td>

      <td>1.65</td>

    </tr>

  </tbody>

</table>

</div>


### Agregar y borrar renglones y columnas


```python
tasa_fertilidad = [1.7, 2.2, 1.8, 2.3, 3.6, 1.7, 5.4, 2.1, 1.8, 2.1]
paises["tasa_fertilidad"] = tasa_fertilidad
paises
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

      <th>poblacion</th>

      <th>porcentaje</th>

      <th>tasa_fertilidad</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>China</th>

      <td>1439</td>

      <td>18.47</td>

      <td>1.7</td>

    </tr>

    <tr>

      <th>India</th>

      <td>1380</td>

      <td>17.70</td>

      <td>2.2</td>

    </tr>

    <tr>

      <th>Estados Unidos</th>

      <td>331</td>

      <td>4.25</td>

      <td>1.8</td>

    </tr>

    <tr>

      <th>Indonesia</th>

      <td>273</td>

      <td>3.51</td>

      <td>2.3</td>

    </tr>

    <tr>

      <th>Pakistán</th>

      <td>220</td>

      <td>2.83</td>

      <td>3.6</td>

    </tr>

    <tr>

      <th>Brasil</th>

      <td>212</td>

      <td>2.73</td>

      <td>1.7</td>

    </tr>

    <tr>

      <th>Nigeria</th>

      <td>206</td>

      <td>2.64</td>

      <td>5.4</td>

    </tr>

    <tr>

      <th>Bangladesh</th>

      <td>164</td>

      <td>2.11</td>

      <td>2.1</td>

    </tr>

    <tr>

      <th>Rusia</th>

      <td>145</td>

      <td>1.87</td>

      <td>1.8</td>

    </tr>

    <tr>

      <th>México</th>

      <td>128</td>

      <td>1.65</td>

      <td>2.1</td>

    </tr>

  </tbody>

</table>

</div>



```python
paises.pop("tasa_fertilidad")
#del paises["tasa_fertilidad"]
#paises.drop("tasa_fertilidad", axis=1, inplace=True)
```

  

    China             1.7
    India             2.2
    Estados Unidos    1.8
    Indonesia         2.3
    Pakistán          3.6
    Brasil            1.7
    Nigeria           5.4
    Bangladesh        2.1
    Rusia             1.8
    México            2.1
    Name: tasa_fertilidad, dtype: float64


```python
# Japón -> 126, 1.62
renglon = pd.Series(name="Japón", data=[126, 1.62], index=["poblacion", "porcentaje"])
renglon
paises = paises.append(renglon)
paises
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

      <th>poblacion</th>

      <th>porcentaje</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>China</th>

      <td>1439.0</td>

      <td>18.47</td>

    </tr>

    <tr>

      <th>India</th>

      <td>1380.0</td>

      <td>17.70</td>

    </tr>

    <tr>

      <th>Estados Unidos</th>

      <td>331.0</td>

      <td>4.25</td>

    </tr>

    <tr>

      <th>Indonesia</th>

      <td>273.0</td>

      <td>3.51</td>

    </tr>

    <tr>

      <th>Pakistán</th>

      <td>220.0</td>

      <td>2.83</td>

    </tr>

    <tr>

      <th>Brasil</th>

      <td>212.0</td>

      <td>2.73</td>

    </tr>

    <tr>

      <th>Nigeria</th>

      <td>206.0</td>

      <td>2.64</td>

    </tr>

    <tr>

      <th>Bangladesh</th>

      <td>164.0</td>

      <td>2.11</td>

    </tr>

    <tr>

      <th>Rusia</th>

      <td>145.0</td>

      <td>1.87</td>

    </tr>

    <tr>

      <th>México</th>

      <td>128.0</td>

      <td>1.65</td>

    </tr>

    <tr>

      <th>Japón</th>

      <td>126.0</td>

      <td>1.62</td>

    </tr>

  </tbody>

</table>

</div>



```python
paises.drop(["Japón"], axis=0, inplace=True)
```

### Funciones de estadística y de agregación básicas

```python
paises.describe(), paises.min()
```


    (         poblacion  porcentaje
     count    10.000000   10.000000
     mean    449.800000    5.776000
     std     509.476376    6.534478
     min     128.000000    1.650000
     25%     174.500000    2.242500
     50%     216.000000    2.780000
     75%     316.500000    4.065000
     max    1439.000000   18.470000,
     poblacion     128.00
     porcentaje      1.65
     dtype: float64)

```python
paises.cumsum()
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

      <th>poblacion</th>

      <th>porcentaje</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>China</th>

      <td>1439.0</td>

      <td>18.47</td>

    </tr>

    <tr>

      <th>India</th>

      <td>2819.0</td>

      <td>36.17</td>

    </tr>

    <tr>

      <th>Estados Unidos</th>

      <td>3150.0</td>

      <td>40.42</td>

    </tr>

    <tr>

      <th>Indonesia</th>

      <td>3423.0</td>

      <td>43.93</td>

    </tr>

    <tr>

      <th>Pakistán</th>

      <td>3643.0</td>

      <td>46.76</td>

    </tr>

    <tr>

      <th>Brasil</th>

      <td>3855.0</td>

      <td>49.49</td>

    </tr>

    <tr>

      <th>Nigeria</th>

      <td>4061.0</td>

      <td>52.13</td>

    </tr>

    <tr>

      <th>Bangladesh</th>

      <td>4225.0</td>

      <td>54.24</td>

    </tr>

    <tr>

      <th>Rusia</th>

      <td>4370.0</td>

      <td>56.11</td>

    </tr>

    <tr>

      <th>México</th>

      <td>4498.0</td>

      <td>57.76</td>

    </tr>

  </tbody>

</table>

</div>


```python
paises.boxplot()
```

    <AxesSubplot:>


![[output_27_1.png|700]]

___
## 3- Cargar datos de Excel y CSV a DataFrames de Pandas con Python


![](https://www.youtube.com/watch?v=uGx0PHD6o9M&ab_channel=C%C3%B3digoM%C3%A1quina)

___
```python
import pandas as pd
  
ventas = pd.read_csv("ventas.csv", index_col=0)
ventas
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

      <th>Trimestre 1</th>

      <th>Trimestre 2</th>

      <th>Trimestre 3</th>

      <th>Trimestre 4</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>Sucursal Norte</th>

      <td>1001</td>

      <td>1002</td>

      <td>1003</td>

      <td>1004</td>

    </tr>

    <tr>

      <th>Sucursal Este</th>

      <td>2001</td>

      <td>2002</td>

      <td>2003</td>

      <td>2004</td>

    </tr>

    <tr>

      <th>Sucursal Oeste</th>

      <td>3001</td>

      <td>3002</td>

      <td>3003</td>

      <td>3004</td>

    </tr>

    <tr>

      <th>Sucursal Sur</th>

      <td>4001</td>

      <td>4002</td>

      <td>4003</td>

      <td>4004</td>

    </tr>

  </tbody>

</table>

</div>


### Más opciones

```python
ventas = pd.read_csv("ventas.csv", index_col=0, usecols=[0,1,3], nrows=2)
ventas
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

      <th>Trimestre 1</th>

      <th>Trimestre 3</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>Sucursal Norte</th>

      <td>1001</td>

      <td>1003</td>

    </tr>

    <tr>

      <th>Sucursal Este</th>

      <td>2001</td>

      <td>2003</td>

    </tr>

  </tbody>

</table>

</div>


### Archivo sin encabezado y creandoselo

```python
ventas = pd.read_csv("ventas2.csv", index_col=0, header=None, names=["T1","T2","T3","T4"])
ventas
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

      <th>T1</th>

      <th>T2</th>

      <th>T3</th>

      <th>T4</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>Sucursal Norte</th>

      <td>1001</td>

      <td>1002</td>

      <td>1003</td>

      <td>1004</td>

    </tr>

    <tr>

      <th>Sucursal Este</th>

      <td>2001</td>

      <td>2002</td>

      <td>2003</td>

      <td>2004</td>

    </tr>

    <tr>

      <th>Sucursal Oeste</th>

      <td>3001</td>

      <td>3002</td>

      <td>3003</td>

      <td>3004</td>

    </tr>

    <tr>

      <th>Sucursal Sur</th>

      <td>4001</td>

      <td>4002</td>

      <td>4003</td>

      <td>4004</td>

    </tr>

  </tbody>

</table>

</div>


### Datos con basura a eliminar

#### Contenido del CSV basura:

`Estos son los datos de ventas``

``,Trimestre 1,Trimestr 2,Trimestre 3,Trimestre 4``

``Sucursal Norte,1001,1002,1003,1004``

``Sucursal Este,2001,2002,2003,2004``

``Sucursal Oeste,3001,3002,3003,3004``

``Sucursal Sur,4001,4002,4003,4004``

``Las ventas las registró Juan Pérez``

  
  

```python
ventas = pd.read_csv("ventas_basura.csv", index_col=0, skiprows=1,skipfooter=1, engine="python")
ventas
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

      <th>Trimestre 1</th>

      <th>Trimestr 2</th>

      <th>Trimestre 3</th>

      <th>Trimestre 4</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>Sucursal Norte</th>

      <td>1001</td>

      <td>1002</td>

      <td>1003</td>

      <td>1004</td>

    </tr>

    <tr>

      <th>Sucursal Este</th>

      <td>2001</td>

      <td>2002</td>

      <td>2003</td>

      <td>2004</td>

    </tr>

    <tr>

      <th>Sucursal Oeste</th>

      <td>3001</td>

      <td>3002</td>

      <td>3003</td>

      <td>3004</td>

    </tr>

    <tr>

      <th>Sucursal Sur</th>

      <td>4001</td>

      <td>4002</td>

      <td>4003</td>

      <td>4004</td>

    </tr>

  </tbody>

</table>

</div>


### Tratamiento de archivo excel


```python
ventas = pd.read_excel("ventas_anuales.xlsx", index_col=0, skiprows=1,sheet_name=None)
ventas["2020"]
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

      <th>Trimestre 1</th>

      <th>Trimestre 2</th>

      <th>Trimestre 3</th>

      <th>Trimestre 4</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>Sucursal Norte</th>

      <td>1001</td>

      <td>1002</td>

      <td>1003</td>

      <td>1004</td>

    </tr>

    <tr>

      <th>Sucursal Este</th>

      <td>2001</td>

      <td>2002</td>

      <td>2003</td>

      <td>2004</td>

    </tr>

    <tr>

      <th>Sucursal Oeste</th>

      <td>3001</td>

      <td>3002</td>

      <td>3003</td>

      <td>3004</td>

    </tr>

    <tr>

      <th>Sucursal Sur</th>

      <td>4001</td>

      <td>4002</td>

      <td>4003</td>

      <td>4004</td>

    </tr>

  </tbody>

</table>

</div>


___
## 4- Filtra Datos en DataFrames
![](https://www.youtube.com/watch?v=Ys02DmUwl30&ab_channel=C%C3%B3digoM%C3%A1quina)

___
# Filtrar Datos en DataFrames


```python
import pandas as pd

datos = {"pais" : ["Estados Unidos", "China", "Brasil", "India", "México"],
         "km2": [9833517, 9600000, 8515767, 3287263, 1964375]}

paises = pd.DataFrame(datos)
paises
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

      <th>pais</th>

      <th>km2</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>Estados Unidos</td>

      <td>9833517</td>

    </tr>

    <tr>

      <th>1</th>

      <td>China</td>

      <td>9600000</td>

    </tr>

    <tr>

      <th>2</th>

      <td>Brasil</td>

      <td>8515767</td>

    </tr>

    <tr>

      <th>3</th>

      <td>India</td>

      <td>3287263</td>

    </tr>

    <tr>

      <th>4</th>

      <td>México</td>

      <td>1964375</td>

    </tr>

  </tbody>

</table>

</div>

# ¿Cómo filtrar datos?

```python
filtro = [True, False, False, False, True]
paises[filtro]
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

      <th>pais</th>

      <th>km2</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>Estados Unidos</td>

      <td>9833517</td>

    </tr>

    <tr>

      <th>4</th>

      <td>México</td>

      <td>1964375</td>

    </tr>

  </tbody>

</table>

</div>

#### Crear filtro para países con superficie mayor a 3287263 km^2

```python
filtro = paises["km2"]>3287263
```

#### Filtrar países con superficie mayor a 3287263 km^2


```python
paises[paises["km2"]>3287263]
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

      <th>pais</th>

      <th>km2</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>Estados Unidos</td>

      <td>9833517</td>

    </tr>

    <tr>

      <th>1</th>

      <td>China</td>

      <td>9600000</td>

    </tr>

    <tr>

      <th>2</th>

      <td>Brasil</td>

      <td>8515767</td>

    </tr>

  </tbody>

</table>

</div>

#### Crear DataFrame a partir de datos_paises.csv

```python
paises = pd.read_csv("datos_paises.csv", index_col=0)
paises
paises[paises["continente"]=="Africa"]
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

      <th>continente</th>

      <th>km2</th>

      <th>poblacion_miles</th>

    </tr>

    <tr>

      <th>pais</th>

      <th></th>

      <th></th>

      <th></th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>Nigeria</th>

      <td>Africa</td>

      <td>923768.0</td>

      <td>190886</td>

    </tr>

    <tr>

      <th>Ethiopia</th>

      <td>Africa</td>

      <td>1104300.0</td>

      <td>104957</td>

    </tr>

    <tr>

      <th>Egypt</th>

      <td>Africa</td>

      <td>1002000.0</td>

      <td>97553</td>

    </tr>

    <tr>

      <th>Democratic Republic of the Congo</th>

      <td>Africa</td>

      <td>2344858.0</td>

      <td>81340</td>

    </tr>

    <tr>

      <th>United Republic of Tanzania</th>

      <td>Africa</td>

      <td>947303.0</td>

      <td>57310</td>

    </tr>

    <tr>

      <th>South Africa</th>

      <td>Africa</td>

      <td>1221037.0</td>

      <td>56717</td>

    </tr>

    <tr>

      <th>Kenya</th>

      <td>Africa</td>

      <td>591958.0</td>

      <td>49700</td>

    </tr>

    <tr>

      <th>Uganda</th>

      <td>Africa</td>

      <td>241550.0</td>

      <td>42863</td>

    </tr>

    <tr>

      <th>Algeria</th>

      <td>Africa</td>

      <td>2381741.0</td>

      <td>41318</td>

    </tr>

    <tr>

      <th>Sudan</th>

      <td>Africa</td>

      <td>NaN</td>

      <td>40533</td>

    </tr>

    <tr>

      <th>Morocco</th>

      <td>Africa</td>

      <td>446550.0</td>

      <td>35740</td>

    </tr>

    <tr>

      <th>Angola</th>

      <td>Africa</td>

      <td>1246700.0</td>

      <td>29784</td>

    </tr>

    <tr>

      <th>Mozambique</th>

      <td>Africa</td>

      <td>799380.0</td>

      <td>29669</td>

    </tr>

    <tr>

      <th>Ghana</th>

      <td>Africa</td>

      <td>238537.0</td>

      <td>28834</td>

    </tr>

    <tr>

      <th>Madagascar</th>

      <td>Africa</td>

      <td>587295.0</td>

      <td>25571</td>

    </tr>

    <tr>

      <th>Cameroon</th>

      <td>Africa</td>

      <td>475650.0</td>

      <td>24054</td>

    </tr>

    <tr>

      <th>Niger</th>

      <td>Africa</td>

      <td>1267000.0</td>

      <td>21477</td>

    </tr>

    <tr>

      <th>Burkina Faso</th>

      <td>Africa</td>

      <td>272967.0</td>

      <td>19193</td>

    </tr>

    <tr>

      <th>Malawi</th>

      <td>Africa</td>

      <td>118484.0</td>

      <td>18622</td>

    </tr>

    <tr>

      <th>Mali</th>

      <td>Africa</td>

      <td>1240192.0</td>

      <td>18542</td>

    </tr>

    <tr>

      <th>Zambia</th>

      <td>Africa</td>

      <td>752612.0</td>

      <td>17094</td>

    </tr>

    <tr>

      <th>Zimbabwe</th>

      <td>Africa</td>

      <td>390757.0</td>

      <td>16530</td>

    </tr>

    <tr>

      <th>Senegal</th>

      <td>Africa</td>

      <td>196712.0</td>

      <td>15851</td>

    </tr>

    <tr>

      <th>Chad</th>

      <td>Africa</td>

      <td>1284000.0</td>

      <td>14900</td>

    </tr>

    <tr>

      <th>Somalia</th>

      <td>Africa</td>

      <td>637657.0</td>

      <td>14742</td>

    </tr>

    <tr>

      <th>Guinea</th>

      <td>Africa</td>

      <td>245857.0</td>

      <td>12717</td>

    </tr>

    <tr>

      <th>South Sudan</th>

      <td>Africa</td>

      <td>658841.0</td>

      <td>12576</td>

    </tr>

    <tr>

      <th>Rwanda</th>

      <td>Africa</td>

      <td>26338.0</td>

      <td>12208</td>

    </tr>

    <tr>

      <th>Tunisia</th>

      <td>Africa</td>

      <td>163610.0</td>

      <td>11532</td>

    </tr>

    <tr>

      <th>Benin</th>

      <td>Africa</td>

      <td>114763.0</td>

      <td>11176</td>

    </tr>

    <tr>

      <th>Burundi</th>

      <td>Africa</td>

      <td>27830.0</td>

      <td>10864</td>

    </tr>

    <tr>

      <th>Togo</th>

      <td>Africa</td>

      <td>56785.0</td>

      <td>7798</td>

    </tr>

    <tr>

      <th>Sierra Leone</th>

      <td>Africa</td>

      <td>72300.0</td>

      <td>7557</td>

    </tr>

    <tr>

      <th>Libya</th>

      <td>Africa</td>

      <td>1676198.0</td>

      <td>6375</td>

    </tr>

    <tr>

      <th>Congo</th>

      <td>Africa</td>

      <td>342000.0</td>

      <td>5261</td>

    </tr>

    <tr>

      <th>Eritrea</th>

      <td>Africa</td>

      <td>117600.0</td>

      <td>5069</td>

    </tr>

    <tr>

      <th>Liberia</th>

      <td>Africa</td>

      <td>111369.0</td>

      <td>4732</td>

    </tr>

    <tr>

      <th>Central African Republic</th>

      <td>Africa</td>

      <td>622984.0</td>

      <td>4659</td>

    </tr>

    <tr>

      <th>Mauritania</th>

      <td>Africa</td>

      <td>1030700.0</td>

      <td>4420</td>

    </tr>

    <tr>

      <th>Namibia</th>

      <td>Africa</td>

      <td>824116.0</td>

      <td>2534</td>

    </tr>

    <tr>

      <th>Botswana</th>

      <td>Africa</td>

      <td>582000.0</td>

      <td>2292</td>

    </tr>

    <tr>

      <th>Lesotho</th>

      <td>Africa</td>

      <td>30355.0</td>

      <td>2233</td>

    </tr>

    <tr>

      <th>Gambia</th>

      <td>Africa</td>

      <td>11295.0</td>

      <td>2101</td>

    </tr>

    <tr>

      <th>Gabon</th>

      <td>Africa</td>

      <td>267668.0</td>

      <td>2025</td>

    </tr>

    <tr>

      <th>Guinea-Bissau</th>

      <td>Africa</td>

      <td>36125.0</td>

      <td>1861</td>

    </tr>

    <tr>

      <th>Swaziland</th>

      <td>Africa</td>

      <td>17363.0</td>

      <td>1367</td>

    </tr>

    <tr>

      <th>Equatorial Guinea</th>

      <td>Africa</td>

      <td>28052.0</td>

      <td>1268</td>

    </tr>

    <tr>

      <th>Mauritius</th>

      <td>Africa</td>

      <td>1969.0</td>

      <td>1265</td>

    </tr>

    <tr>

      <th>Djibouti</th>

      <td>Africa</td>

      <td>23200.0</td>

      <td>957</td>

    </tr>

    <tr>

      <th>Comoros</th>

      <td>Africa</td>

      <td>2235.0</td>

      <td>814</td>

    </tr>

    <tr>

      <th>Western Sahara</th>

      <td>Africa</td>

      <td>266000.0</td>

      <td>553</td>

    </tr>

    <tr>

      <th>Cabo Verde</th>

      <td>Africa</td>

      <td>4033.0</td>

      <td>546</td>

    </tr>

    <tr>

      <th>Mayotte</th>

      <td>Africa</td>

      <td>374.0</td>

      <td>253</td>

    </tr>

    <tr>

      <th>Sao Tome and Principe</th>

      <td>Africa</td>

      <td>964.0</td>

      <td>204</td>

    </tr>

    <tr>

      <th>Seychelles</th>

      <td>Africa</td>

      <td>457.0</td>

      <td>95</td>

    </tr>

    <tr>

      <th>Saint Helena</th>

      <td>Africa</td>

      <td>308.0</td>

      <td>4</td>

    </tr>

  </tbody>

</table>

</div>


### Seleccionando países de extensión pequeña

#### Crear filtro para países con superficie menor a 50 km^2


```python
filtro = paises["km2"] < 50
filtro
```

    pais
    China                          False
    India                          False
    United States of America       False
    Indonesia                      False
    Brazil                         False
                                   ...  
    Saint Helena                   False
    Falkland Islands (Malvinas)    False
    Niue                           False
    Holy See                        True
    Tokelau                         True
    Name: km2, Length: 229, dtype: bool


#### Filtrar países con superficie menor a 50 km^2


```python
paises[filtro]
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

      <th>continente</th>

      <th>km2</th>

      <th>poblacion_miles</th>

    </tr>

    <tr>

      <th>pais</th>

      <th></th>

      <th></th>

      <th></th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>China, Macao SAR</th>

      <td>Asia</td>

      <td>30.0</td>

      <td>623</td>

    </tr>

    <tr>

      <th>Sint Maarten (Dutch part)</th>

      <td>America</td>

      <td>34.0</td>

      <td>40</td>

    </tr>

    <tr>

      <th>Monaco</th>

      <td>Europa</td>

      <td>2.0</td>

      <td>39</td>

    </tr>

    <tr>

      <th>Gibraltar</th>

      <td>Europa</td>

      <td>6.0</td>

      <td>35</td>

    </tr>

    <tr>

      <th>Bonaire, Sint Eustatius and Saba</th>

      <td>America</td>

      <td>1.0</td>

      <td>25</td>

    </tr>

    <tr>

      <th>Nauru</th>

      <td>Oceania</td>

      <td>21.0</td>

      <td>11</td>

    </tr>

    <tr>

      <th>Tuvalu</th>

      <td>Oceania</td>

      <td>26.0</td>

      <td>11</td>

    </tr>

    <tr>

      <th>Holy See</th>

      <td>Europa</td>

      <td>1.0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>Tokelau</th>

      <td>Oceania</td>

      <td>12.0</td>

      <td>1</td>

    </tr>

  </tbody>

</table>

</div>

### Seleccionando países pequeños pero altamente poblados
#### Países con superficie menor a 50 km^2 y población mayor 500

```python
paises[ (paises["km2"]<50) & (paises["poblacion_miles"]>500)]
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

      <th>continente</th>

      <th>km2</th>

      <th>poblacion_miles</th>

    </tr>

    <tr>

      <th>pais</th>

      <th></th>

      <th></th>

      <th></th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>China, Macao SAR</th>

      <td>Asia</td>

      <td>30.0</td>

      <td>623</td>

    </tr>

  </tbody>

</table>

</div>


### Seleccionando países muy pequeños ó poco poblados

#### Países con superficie menor a 5 km^2 ó con población menor a 5

```python
paises[ (paises["km2"]<5) | (paises["poblacion_miles"]<5) ]
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

      <th>continente</th>

      <th>km2</th>

      <th>poblacion_miles</th>

    </tr>

    <tr>

      <th>pais</th>

      <th></th>

      <th></th>

      <th></th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>Monaco</th>

      <td>Europa</td>

      <td>2.0</td>

      <td>39</td>

    </tr>

    <tr>

      <th>Bonaire, Sint Eustatius and Saba</th>

      <td>America</td>

      <td>1.0</td>

      <td>25</td>

    </tr>

    <tr>

      <th>Saint Helena</th>

      <td>Africa</td>

      <td>308.0</td>

      <td>4</td>

    </tr>

    <tr>

      <th>Falkland Islands (Malvinas)</th>

      <td>America</td>

      <td>12173.0</td>

      <td>3</td>

    </tr>

    <tr>

      <th>Niue</th>

      <td>Oceania</td>

      <td>260.0</td>

      <td>2</td>

    </tr>

    <tr>

      <th>Holy See</th>

      <td>Europa</td>

      <td>1.0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>Tokelau</th>

      <td>Oceania</td>

      <td>12.0</td>

      <td>1</td>

    </tr>

  </tbody>

</table>

</div>

### Seleccionando países pequeños, poco poblados y europeos
#### Países europeos con superficie menor a 50 km^2 y con población menor a 50

```python
paises[(paises["continente"]=="Europa") &
       (paises["km2"]<50) &
       (paises["poblacion_miles"]<50) ]
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

      <th>continente</th>

      <th>km2</th>

      <th>poblacion_miles</th>

    </tr>

    <tr>

      <th>pais</th>

      <th></th>

      <th></th>

      <th></th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>Monaco</th>

      <td>Europa</td>

      <td>2.0</td>

      <td>39</td>

    </tr>

    <tr>

      <th>Gibraltar</th>

      <td>Europa</td>

      <td>6.0</td>

      <td>35</td>

    </tr>

    <tr>

      <th>Holy See</th>

      <td>Europa</td>

      <td>1.0</td>

      <td>1</td>

    </tr>

  </tbody>

</table>

</div>

### Seleccionando países pequeños, poco poblados y no europeos
#### Países no europeos con superficie menor a 50 km^2 y con población menor a 50

```python
paises[~(paises["continente"]=="Europa") &
       (paises["km2"]<50) &
       (paises["poblacion_miles"]<50) ]
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

      <th>continente</th>

      <th>km2</th>

      <th>poblacion_miles</th>

    </tr>

    <tr>

      <th>pais</th>

      <th></th>

      <th></th>

      <th></th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>Sint Maarten (Dutch part)</th>

      <td>America</td>

      <td>34.0</td>

      <td>40</td>

    </tr>

    <tr>

      <th>Bonaire, Sint Eustatius and Saba</th>

      <td>America</td>

      <td>1.0</td>

      <td>25</td>

    </tr>

    <tr>

      <th>Nauru</th>

      <td>Oceania</td>

      <td>21.0</td>

      <td>11</td>

    </tr>

    <tr>

      <th>Tuvalu</th>

      <td>Oceania</td>

      <td>26.0</td>

      <td>11</td>

    </tr>

    <tr>

      <th>Tokelau</th>

      <td>Oceania</td>

      <td>12.0</td>

      <td>1</td>

    </tr>

  </tbody>

</table>

</div>



```python
paises.loc[~(paises["continente"]=="Europa") &
       (paises["km2"]<50) &
       (paises["poblacion_miles"]<50) ]
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

      <th>continente</th>

      <th>km2</th>

      <th>poblacion_miles</th>

    </tr>

    <tr>

      <th>pais</th>

      <th></th>

      <th></th>

      <th></th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>Sint Maarten (Dutch part)</th>

      <td>America</td>

      <td>34.0</td>

      <td>40</td>

    </tr>

    <tr>

      <th>Bonaire, Sint Eustatius and Saba</th>

      <td>America</td>

      <td>1.0</td>

      <td>25</td>

    </tr>

    <tr>

      <th>Nauru</th>

      <td>Oceania</td>

      <td>21.0</td>

      <td>11</td>

    </tr>

    <tr>

      <th>Tuvalu</th>

      <td>Oceania</td>

      <td>26.0</td>

      <td>11</td>

    </tr>

    <tr>

      <th>Tokelau</th>

      <td>Oceania</td>

      <td>12.0</td>

      <td>1</td>

    </tr>

  </tbody>

</table>

</div>



___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%