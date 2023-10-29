---
ID: 153
"tags:": 
"nombre:": Clase 4 humai - Data Wrangling Avanzado
---
___
# Data Wrangling Avanzado
___
![](https://www.youtube.com/watch?v=fjOgkNA-sQ4&list=PLon--J7mANNWbXbGraiiMNWcv5T69kkAL&index=4)

___
<a href="https://colab.research.google.com/github/institutohumai/cursos-python/blob/master/AnalisisDeDatos/4_Data_Wrangling_Avanzado/data_wrangling_avanzado.ipynb"> <img src='https://colab.research.google.com/assets/colab-badge.svg' /> </a>
<div align="center"> Recordá abrir en una nueva pestaña </div>

# Data Wrangling Avanzado


## Tabla de Contenidos

I. Data Wrangling Avanzado

    I. Tabla de Contenidos

II. Table of Contents

    I. Introducción
    II. Pandas y Cadenas de caracteres
        I. count
        II. Ejercicio
        III. contains
        IV. lower, upper y title
        V. split

III. ¿Cómo organizar la información? OLAP, OLTP y Tidy data

    I. OLTP y OLAP
    II. Tidy data
        I. Tuberculosis
            I. Tabla 1
            II. Tablas 2.a y 2.b
            III. Tabla 3
            IV. Tabla 4
            V. Tabla 5
    III. Melt
        I. Ejercicios
        II. Ejercicios

IV. Series de Tiempo

    I. Datetime y metodos de manipulacion de series de tiempo
    II. Ventanas y Medias moviles
    III. Shift y Diff

## Introducción

En esta clase vamos a ver cómo hacer manejo avanzado de datos a partir, tanto en cadenas de caracteres como en series de tiempo. El primer dataset que vamos a utilizar es del portal de datos abiertos de España.


```python
# !pip install seaborn
# !pip install numpy==1.18.5
```


```python
import pandas as pd
import numpy as np
```


```python
df = pd.read_csv('https://datasets-humai.s3.amazonaws.com/datasets/parodesprov.csv')
```


```python
df.head()
```





  <div id="df-c4071fea-01d0-4ca6-9d3b-0f713e2fb7bc" class="colab-df-container">
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
      <th>OBJECTID</th>
      <th>Codigo</th>
      <th>Texto</th>
      <th>Cod_Prov</th>
      <th>Cod_CCAA</th>
      <th>TotalParoRegistrado</th>
      <th>PAD_1C02</th>
      <th>PAD_1_COD_PROV</th>
      <th>PAD_1_COD_CCAA</th>
      <th>Shape__Area</th>
      <th>Shape__Length</th>
      <th>Codigop</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1001</td>
      <td>Alegría-Dulantzi</td>
      <td>1</td>
      <td>16</td>
      <td>184.0</td>
      <td>2856.0</td>
      <td>Araba/Álava</td>
      <td>16.0</td>
      <td>3.709269e+07</td>
      <td>48191.568537</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1002</td>
      <td>Amurrio</td>
      <td>1</td>
      <td>16</td>
      <td>766.0</td>
      <td>10260.0</td>
      <td>Araba/Álava</td>
      <td>16.0</td>
      <td>1.799114e+08</td>
      <td>90623.621986</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1003</td>
      <td>Aramaio</td>
      <td>1</td>
      <td>16</td>
      <td>18.0</td>
      <td>1502.0</td>
      <td>Araba/Álava</td>
      <td>16.0</td>
      <td>1.377066e+08</td>
      <td>58592.914048</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1004</td>
      <td>Artziniega</td>
      <td>1</td>
      <td>16</td>
      <td>110.0</td>
      <td>1840.0</td>
      <td>Araba/Álava</td>
      <td>16.0</td>
      <td>5.130078e+07</td>
      <td>31498.524044</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>1006</td>
      <td>Armiñón</td>
      <td>1</td>
      <td>16</td>
      <td>12.0</td>
      <td>234.0</td>
      <td>Araba/Álava</td>
      <td>16.0</td>
      <td>2.380288e+07</td>
      <td>33293.805036</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-c4071fea-01d0-4ca6-9d3b-0f713e2fb7bc')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-c4071fea-01d0-4ca6-9d3b-0f713e2fb7bc button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-c4071fea-01d0-4ca6-9d3b-0f713e2fb7bc');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-635259da-8a05-4a3a-a7d2-51f74ce036c9">
  <button class="colab-df-quickchart" onclick="quickchart('df-635259da-8a05-4a3a-a7d2-51f74ce036c9')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-635259da-8a05-4a3a-a7d2-51f74ce036c9 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




Generalmente cuando en un dataset encontramos campos de texto es recomendable analizar si la carga se hizo con un buen criterio y no hay errores en la carga. Vamos a prestar atención a los campos Texto y PAD_1_COD_PROV.


```python
df["Texto"].head()
```




    0    Alegría-Dulantzi
    1             Amurrio
    2             Aramaio
    3          Artziniega
    4             Armiñón
    Name: Texto, dtype: object



Noten que el primer valor incluye un "-" como separador

Vamos a comenzar eliminando las filas que tienen null el campo Texto, para facilitar el análisis posterior.


```python
df = df[~df["Texto"].isnull()]
```

## Pandas y Cadenas de caracteres

Cuando una pd.Series es de tipo object Pandas permite acceder a métodos para operar sobre strings llamando al método **.str**.

### count

El método **.str.count()** permite contar cuántas ocurrencias de un patrón hay en una Series. Para ello se puede pasar una regex. Las regex o expresiones regulares son una cadena de caracteres que define una búsqueda de un patrón. En esta clase no vamos a ahondar en regex pero sí podemos mencionar que:
- Si pasamos un carácter en particular nos va a matchear cuántas veces aparece.
- El carácter . funcion como comodín, con lo cual cualquier caracter va a matchear.

Entonces, si queremos saber cuántas veces aparece el símbolo "-" en cada término podemos hacer:


```python
df["Texto"].str.count("-").head()
```




    0    1
    1    0
    2    0
    3    0
    4    0
    Name: Texto, dtype: int64



Ahora, nos llama la atención que el símbolo "-" aparece en la primera fila, ¿será algo común?


```python
df["Texto"].str.count("-").value_counts()
```




    0    16009
    1      222
    2        4
    Name: Texto, dtype: int64



### Ejercicio

1- Ver los casos que tiene 2 "-" en el nombre.


```python
df[df["Texto"].str.count("-")==2]
```



2- Graficar un histograma con la cantidad de caracteres en la columna Texto usando count o len Tip: pueden usar el método .hist.


```python
import matplotlib.pyplot as plt
%matplotlib inline
```


```python
df.Texto.str.len().hist()
```
![[Pasted image 20230918202508.png]]


3- Mostrar las diferencias entre usar **.str.count()** y **.str.len()**. Para ello usen el método **pd.Series.equals()**

```python
(df.Texto.str.count("")-1).equals(df.Texto.str.len())
```
``True``
### contains

Digamos que queremos encontrar nombres de ciudades vascas. Para ello sabemos que "herri" en Euskera significa lugar, con lo que esperamos encontrar "erri" en una gran cantidad de ciudades. Vamos a filtrar trayendo solamente las ciudades que incluyen "erri" dentro de su nombre con el método **.str.contains**.


```python
df[df["Texto"].str.contains("erri",case=False)].head() # case es para considerar mayúsculas y minúsculas o no
```





  <div id="df-b39bfb99-27be-4479-9e79-cb3c548c5475" class="colab-df-container">
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
      <th>OBJECTID</th>
      <th>Codigo</th>
      <th>Texto</th>
      <th>Cod_Prov</th>
      <th>Cod_CCAA</th>
      <th>TotalParoRegistrado</th>
      <th>PAD_1C02</th>
      <th>PAD_1_COD_PROV</th>
      <th>PAD_1_COD_CCAA</th>
      <th>Shape__Area</th>
      <th>Shape__Length</th>
      <th>Codigop</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>33</th>
      <td>34</td>
      <td>1046</td>
      <td>Erriberagoitia/Ribera Alta</td>
      <td>1</td>
      <td>16</td>
      <td>26.0</td>
      <td>745.0</td>
      <td>Araba/Álava</td>
      <td>16.0</td>
      <td>2.227260e+08</td>
      <td>114217.030007</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>34</th>
      <td>35</td>
      <td>1047</td>
      <td>Ribera Baja/Erribera Beitia</td>
      <td>1</td>
      <td>16</td>
      <td>72.0</td>
      <td>1353.0</td>
      <td>Araba/Álava</td>
      <td>16.0</td>
      <td>4.706702e+07</td>
      <td>42082.113185</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>162</th>
      <td>163</td>
      <td>3025</td>
      <td>Benferri</td>
      <td>3</td>
      <td>10</td>
      <td>161.0</td>
      <td>1920.0</td>
      <td>Alicante/Alacant</td>
      <td>10.0</td>
      <td>2.002354e+07</td>
      <td>21212.706211</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>2026</th>
      <td>2027</td>
      <td>13081</td>
      <td>Terrinches</td>
      <td>13</td>
      <td>8</td>
      <td>122.0</td>
      <td>748.0</td>
      <td>Ciudad Real</td>
      <td>8.0</td>
      <td>9.099513e+07</td>
      <td>41739.202048</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>2506</th>
      <td>2507</td>
      <td>17056</td>
      <td>Cornellà del Terri</td>
      <td>17</td>
      <td>9</td>
      <td>55.0</td>
      <td>2279.0</td>
      <td>Girona</td>
      <td>9.0</td>
      <td>5.058085e+07</td>
      <td>38058.585347</td>
      <td>17.0</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-b39bfb99-27be-4479-9e79-cb3c548c5475')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-b39bfb99-27be-4479-9e79-cb3c548c5475 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-b39bfb99-27be-4479-9e79-cb3c548c5475');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-f8b3c26b-caf8-493f-8f4c-d6196cbcecb9">
  <button class="colab-df-quickchart" onclick="quickchart('df-f8b3c26b-caf8-493f-8f4c-d6196cbcecb9')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-f8b3c26b-caf8-493f-8f4c-d6196cbcecb9 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>





```python
df[df["Texto"].str.contains("erri",case=False)].shape
```


    (48, 12)



### lower, upper y title

Supongamos que queremos estar seguros que las nombres están estandarizados... podemos elegir pasar todo a minúscula o a mayúscula de la siguiente manera:


```python
df["Texto"].str.lower().head()
```




    0    alegría-dulantzi
    1             amurrio
    2             aramaio
    3          artziniega
    4             armiñón
    Name: Texto, dtype: object




```python
df["Texto"].str.upper().head()
```




    0    ALEGRÍA-DULANTZI
    1             AMURRIO
    2             ARAMAIO
    3          ARTZINIEGA
    4             ARMIÑÓN
    Name: Texto, dtype: object



También podemos aplicar mayúscula a la primera letra y al resto minúscula, con **.str.title**. Este método toma en consideración espacios o símbolos no alfabéticos. Es decir, va a comenzar con mayúscula los términos después de un espacio, "-" o "/". Por ejemplo


```python
df["Texto"][df["Texto"].str.count("-") == 2].str.title()
```




    4460     Lozoyuela-Navas-Sieteiglesias
    4809          Oroz-Betelu/Orotz-Betelu
    12630    Lozoyuela-Navas-Sieteiglesias
    12979         Oroz-Betelu/Orotz-Betelu
    Name: Texto, dtype: object



### split

En el ejemplo anterior encontramos el uso de "/". En este caso se refiere a que el nombre de la ciudad (Oroz-Betelu/Orotz-Betelu) tiene dos nombres oficiales, uno en español y otro en vasco.

Supongamos que queremos estandarizar el problema y quedarnos sólo con el nombre que aparece primero, ¿cómo podemos hacerlo?

Primero veamos algunos ejemplos otros ejemplos de nombres con "/":


```python
df["Texto"][df["Texto"].str.count("/") > 0].unique()[:10]
```




    array(['Ayala/Aiara', 'Baños de Ebro/Mañueta', 'Campezo/Kanpezu',
           'Elburgo/Burgelu', 'Elvillar/Bilar', 'Labastida/Bastida',
           'Lanciego/Lantziego', 'Laudio/Llodio',
           'Moreda de Álava/Moreda Araba', 'Erriberagoitia/Ribera Alta'],
          dtype=object)



Nota: en un primer momento uno podría pensar que en este dataset el primer elemento debería ser siempre el nombre en, por ejemplo, español y el segundo en vasco... Sin embargo, no es así :-S

Vamos a usar **.str.split()**, vale la pena mencionar que el método devuelve una lista con un elemento por cada separación que pudo realizar. Para ello recibe como parámetro un string que es un patrón que va a usar, justamente, para dividir la cadena de caracteres. Comúnmente sólo vamos a pasarle un elemento por el cual splitear.


```python
df["Texto"].str.split() # por default split separa por espacios en blanco
```




    0               [Alegría-Dulantzi]
    1                        [Amurrio]
    2                        [Aramaio]
    3                     [Artziniega]
    4                        [Armiñón]
                       ...            
    16334                       [Biel]
    16335                   [Marracos]
    16336    [Villamayor, de, Gállego]
    16337                      [Ceuta]
    16338                    [Melilla]
    Name: Texto, Length: 16235, dtype: object



Noten en el ejemplo anterior que si devuelve una lista con un solo elemento es que no matcheó y, por lo tanto, no dividió el string.

Yendo a nuestro problema, separamos por el caracter '/'. Notar como se transforman los nombres compuestos
MUCHO CUIDADO! Nuestros strings ahora son listas!! :o


```python
df["Texto"].str.split("/").head()
```




    0    [Alegría-Dulantzi]
    1             [Amurrio]
    2             [Aramaio]
    3          [Artziniega]
    4             [Armiñón]
    Name: Texto, dtype: object



Entonces, nos quedamos con la primera versión del nombre al separar por "/"


```python
texto_para_split = df["Texto"][df["Texto"].str.count("/") > 0] # guardo en una variable casos con /

texto_para_split.str.split("/").apply(lambda x: x[0]) # para indexar las listas tengo que usar apply
```




    7                   Ayala
    8           Baños de Ebro
    12                Campezo
    16                Elburgo
    18               Elvillar
                   ...       
    15372              Novelé
    15412             Sagunto
    15447          Vilallonga
    15705    Karrantza Harana
    15757              Urduña
    Name: Texto, Length: 234, dtype: object



Por otra parte, si quisiéramos guardar cada nombre en una columna separada podemos hacerlo usando la opción expand:


```python
texto_para_split.str.split("/", expand=True)
```





  <div id="df-70d7547a-3546-4561-be6e-c6daa887d9ef" class="colab-df-container">
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
      <th>0</th>
      <th>1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>7</th>
      <td>Ayala</td>
      <td>Aiara</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Baños de Ebro</td>
      <td>Mañueta</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Campezo</td>
      <td>Kanpezu</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Elburgo</td>
      <td>Burgelu</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Elvillar</td>
      <td>Bilar</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>15372</th>
      <td>Novelé</td>
      <td>Novetlè</td>
    </tr>
    <tr>
      <th>15412</th>
      <td>Sagunto</td>
      <td>Sagunt</td>
    </tr>
    <tr>
      <th>15447</th>
      <td>Vilallonga</td>
      <td>Villalonga</td>
    </tr>
    <tr>
      <th>15705</th>
      <td>Karrantza Harana</td>
      <td>Valle de Carranza</td>
    </tr>
    <tr>
      <th>15757</th>
      <td>Urduña</td>
      <td>Orduña</td>
    </tr>
  </tbody>
</table>
<p>234 rows × 2 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-70d7547a-3546-4561-be6e-c6daa887d9ef')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-70d7547a-3546-4561-be6e-c6daa887d9ef button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-70d7547a-3546-4561-be6e-c6daa887d9ef');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-b5274fad-e037-4c94-b790-c6bfda7a609d">
  <button class="colab-df-quickchart" onclick="quickchart('df-b5274fad-e037-4c94-b790-c6bfda7a609d')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-b5274fad-e037-4c94-b790-c6bfda7a609d button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




Podemos asignar el resultado de expand de la siguiente manera:


```python
df[["nombre_1", "nombre_2"]] = df["Texto"].str.split("/", expand=True) # usamos el df original y expandimos
```


```python
df[["nombre_1", "nombre_2"]].head() # vemos que hay nulls que nombre_2 porque tienen un solo nombre
```





  <div id="df-82daeeff-a336-47e7-9c38-c960e50e60bb" class="colab-df-container">
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
      <th>nombre_1</th>
      <th>nombre_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alegría-Dulantzi</td>
      <td>None</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Amurrio</td>
      <td>None</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Aramaio</td>
      <td>None</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Artziniega</td>
      <td>None</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Armiñón</td>
      <td>None</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-82daeeff-a336-47e7-9c38-c960e50e60bb')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-82daeeff-a336-47e7-9c38-c960e50e60bb button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-82daeeff-a336-47e7-9c38-c960e50e60bb');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-cd216fba-c314-4358-98be-9013fe6a18a5">
  <button class="colab-df-quickchart" onclick="quickchart('df-cd216fba-c314-4358-98be-9013fe6a18a5')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-cd216fba-c314-4358-98be-9013fe6a18a5 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>





```python
df.loc[~df["nombre_2"].isnull(), ["nombre_1", "nombre_2"]].head() # noten el filtro booleano
```





  <div id="df-857c6783-a157-4c81-a90b-3397b14252b5" class="colab-df-container">
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
      <th>nombre_1</th>
      <th>nombre_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>7</th>
      <td>Ayala</td>
      <td>Aiara</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Baños de Ebro</td>
      <td>Mañueta</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Campezo</td>
      <td>Kanpezu</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Elburgo</td>
      <td>Burgelu</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Elvillar</td>
      <td>Bilar</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-857c6783-a157-4c81-a90b-3397b14252b5')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-857c6783-a157-4c81-a90b-3397b14252b5 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-857c6783-a157-4c81-a90b-3397b14252b5');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-617fc5a2-9c7e-4809-a4ae-8f3a463e6498">
  <button class="colab-df-quickchart" onclick="quickchart('df-617fc5a2-9c7e-4809-a4ae-8f3a463e6498')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-617fc5a2-9c7e-4809-a4ae-8f3a463e6498 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




## ¿Cómo organizar la información? OLAP, OLTP y Tidy data

Existen diversas formas de organizar la información. En general, qué vamos a hacer con la información es clave para entender cómo organizarla. Veamos algunos conceptos habituales a la hora de trabajar con datos.

### OLTP y OLAP

La sigla OLTP viene de Online Transaction processing y se refiere a transacciones que ocurren en tiempo real. Un ejemplo típico son los ATMs (automated teller machine), más conocidos como "cajeros automáticos".

En este aspecto transacción tiene dos acepciones y ambas son válidas: por un lado, se procesan transacciones en término de bases de datos (que vamos a ver a continuación), por otro lado, se suele aplicar a transacciones económicas en donde se intercambian entidades económicas.

Sistemas OLTP son la mayoría de los sistemas tradicionales que conocemos, especialmente los sistemas bancarios. Estos son sistemas transaccionales (en la primera acepción de arriba) porque intentan cumplir 4 objetivos (**ACID**):

- Las transacciones son operaciones **atómicas**: se hacen por completo o no se hacen. Imagínense una transferencia bancaria, ésto requiere debitar en una cuenta y acreditar en otra. Si la operación no fuera atómica y fallara podríamos quedarnos en un estado inesperado en el cual se debite de la primera y no se acredite en la segunda. Para evitar ésto, la atomicidad garantiza que si la operación falla en alguna parte del proceso revertimos completamos la operación y no impactamos ningún cambio (hacemos *rollback*).

- Toda transacción debe mantener la **consistencia** de la base de datos, es decir, debe respetar una serie de restricciones. Por ejemplo, podemos pensar que para que una tarjeta de crédito sea de extensión de una cuenta esa cuenta debe existir previamente. Otro ejemplo, puede ser que no pueden existir dos cuentas bancarias diferentes con el mismo número.

- Además, los sistemas transaccionales (especialmente los sistemas OLTP) requieren garantizar el **aislamiento** de las operaciones. Es común que estos sistemas necesiten resolver miles de operaciones concurrentes (es decir, que suceden en simultáneo), el aislamiento consiste en que esas operaciones dejen en la base de datos el mismo estado que si las operaciones fueran secuenciales (es decir, una por vez). Incluso, si una de esas falla, no debería alterar el resultado.


Para ésto, se implementan diferentes algoritmos a fin de asegurar que no se generen errores ni competencias entre usuarios que estan intentando acceder a los mismos registros a la vez.

OLAP (Online Analytical Processing) por otra parte se refiere a todos los sistemas utilizados para analisis y reportes de negocios (Business Intelligence), en los cuales se realizan diferentes operaciones de agregacion sobre los datos, a fin de proveer a los usuarios con informacion relevante.

Las herramientas OLAP permiten realizar análisis multidimensionales, tomando en consideración distintas dimensiones y métricas. En este sentido, está lo que se conoce como "cubo OLAP". El cubo OLAP es un array multidimensional que permite analizar la información vista desde distintos ángulos. Por ejemplo, podemos querer ver un reporte financiero por producto, por ciudad, por tiempo, etc. Cada uno de estos términos es una dimensión del análisis.

Estos sistemas generalmente requieren procesos de carga y transformaciones masivas que pueden durar horas o días, y permiten presentar la información de un modo tal que el análisis es en tiempo real, no así la información que usa.

## Tidy data

**Tidy data** es un trabajo escrito por Hadley Wickham (de la empresa RStudio) que se ha difundido mucho, especialmente en la comunidad de R, sobre buenas prácticas a la hora de estructurar información tabular. Pueden consultar el trabajo acá: https://vita.had.co.nz/papers/tidy-data.pdf

La información tabular consta de **filas** y **columnas**. Las columnas siempre tienen una etiqueta y las filas sólo a veces.

Los *datasets* constan de **valores**, éstos pueden ser numéricos o no numéricos . En el caso en que sea un valor numérico representa una cantidad, si no es numérico es una cualidad. Además, los valores miden o caracterizan un determinado atributo (altura, peso, temperatura, etc.). Este atributo se conoce como **variable**. Por último, esa variable se corresponde con una determinada unidad observada. Generalmente llamamos a eso simplemente **observación** (por ejemplo, la persona a la que se le midió la altura).

Dicho ésto, Wickham define un dataset *tidy* u ordenado como aquel que cumple la tercera forma normal de bases de datos, pero con un lenguaje más cercano al campo del análisis de datos y pensando en información contenida en una tabla, y no en una base de datos con muchas tablas. Las condiciones son:

- Cada variable forma una columna.
- Cada observación forma una fila.
- Cada tipo de unidad observacional forma una tabla.

Además, describe 5 de los errores más comunes a la hora de ordenar la información:

- Los nombres de columna en vez de ser nombres de variables son valores
- Muchas variables se guardan en una sola columna.
- Las variables se guardan tanto en columnas como en filas.
- Distintos tipos de unidades observacionales se guardan en una misma tabla.
- Una única unidad observacional se almacena en distintas tablas.4

### Tuberculosis

A continuación vamos a ver un dataset de tuberculosis representado de distintas maneras...

#### Tabla 1

En esta primera representación de la información vemos que una misma columna (type) contiene dos variables (cases y population)

|country|year|type|count|
| --- | --- | --- | --- |
|Afghanistan|1999|cases|745|
|Afghanistan|1999|population|19987071|
|Afghanistan|2000|cases|2666|
|Afghanistan|2000|population|20595360|
|Brazil|1999|cases|37737|
|Brazil|1999|population|172006362|

#### Tablas 2.a y 2.b
En este caso separamos la tabla en dos tablas. Una donde vemos la población y otra donde vemos la cantidad de casos... ¿Cuál es el problema acá?

Si bien esto puede parecer correcto noten que la unidad observacional en realidad es un país en un año determinado... Con lo cual, lo que estamos haciendo acá es tener la misma unidad observacional en dos tablas. Además, los valores de la variable year están como nombres de columnas...


|country|1999|2000|
| --- | --- | --- |
|Afghanistan|745|2666|
|Brazil|37737|80488|
|China|212258|213766|

|country|1999|2000|
| --- | --- | --- |
|Afghanistan|19987071|20595360|
|Brazil|172006362|174504898|
|China|1272915272|1280428583|

#### Tabla 3

En este caso, perdimos las variables cases y population y calculamos un ratio. Si bien ésto cumple con ser "ordenado" estamos perdiendo las variables originales.

|country|year|rate|
| --- | --- | --- |
|Afghanistan|1999|745/19987071|
|Afghanistan|2000|2666/20595360|
|Brazil|1999|37737/172006362|
|Brazil|2000|80488/174504898|
|China|1999|212258/1272915272|
|China|2000|213766/1280428583|

#### Tabla 4

En la tabla 4 vemos que la variable *year*, *cases* y *population* se juntaron, con lo cual los valores de *year* pasan a formar parte de los nombres de las columnas.

|country|cases_1999|cases_2000|population_1999|population_2000|
| --- | --- | --- | --- | --- |
|Afghanistan|745|19987071|2666|20595360|
|Brazil|37737|172006362|80488|174504898|
|China|212258|1272915272|213766|1280428583|

#### Tabla 5

Finalmente, la tabla *tidy* es:

|country|year|cases|population|
| --- | --- | --- | --- |
|Afghanistan|1999|745|19987071|
|Afghanistan|2000|2666|20595360|
|Brazil|1999|37737|172006362|
|Brazil|2000|80488|174504898|
|China|1999|212258|1272915272|
|China|2000|213766|1280428583|

## Melt

Una de los métodos más útiles de Pandas para pasar de un formato *wide* o *ancho* como el de la tabla 4 a uno *largo* como el de la tabla 5 es **.melt**.

Para aplicar este método vamos a obtener un dataset de Billboard sobre las canciones mas escuchadas del 2000.

Vamos a agregar la opcion de encoding para solucionar un problema con los caracteres usados.


```python
billboard = pd.read_csv('https://raw.githubusercontent.com/hadley/tidy-data/master/data/billboard.csv', warn_bad_lines=False, error_bad_lines=False, encoding='iso-8859-1')

billboard
```

![[Pasted image 20230920165425.png]]

### Ejercicios

1- Analicen el dataset, vean cuáles son las variables, qué es la observación. ¿Es necesario separarlo en dos tablas? Nota: lo que se está midiendo en las columnas x1st.week a x76th.week es la posición en el ranking de las 100 canciones más escuchadas en esa semana. Es decir, x1st.week es la posición en el ranking durante la primera semana que esa canción fue top 100.

2- ¿Por qué creen que hay tantas columnas con valores nulos?

3- ¿Cómo podríamos hacer este dataset más ordenado? (no miren la continuación de la notebook :-S)

Veamos primero como luce el dataset
```python
billboard.head()
```

  <div id="df-7f30bc9b-a8b2-423d-946e-cb7a1b4fbbfd" class="colab-df-container">
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
      <th>year</th>
      <th>artist.inverted</th>
      <th>track</th>
      <th>time</th>
      <th>genre</th>
      <th>date.entered</th>
      <th>date.peaked</th>
      <th>x1st.week</th>
      <th>x2nd.week</th>
      <th>x3rd.week</th>
      <th>...</th>
      <th>x67th.week</th>
      <th>x68th.week</th>
      <th>x69th.week</th>
      <th>x70th.week</th>
      <th>x71st.week</th>
      <th>x72nd.week</th>
      <th>x73rd.week</th>
      <th>x74th.week</th>
      <th>x75th.week</th>
      <th>x76th.week</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2000</td>
      <td>Destiny's Child</td>
      <td>Independent Women Part I</td>
      <td>3:38</td>
      <td>Rock</td>
      <td>2000-09-23</td>
      <td>2000-11-18</td>
      <td>78</td>
      <td>63.0</td>
      <td>49.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2000</td>
      <td>Santana</td>
      <td>Maria, Maria</td>
      <td>4:18</td>
      <td>Rock</td>
      <td>2000-02-12</td>
      <td>2000-04-08</td>
      <td>15</td>
      <td>8.0</td>
      <td>6.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2000</td>
      <td>Savage Garden</td>
      <td>I Knew I Loved You</td>
      <td>4:07</td>
      <td>Rock</td>
      <td>1999-10-23</td>
      <td>2000-01-29</td>
      <td>71</td>
      <td>48.0</td>
      <td>43.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2000</td>
      <td>Madonna</td>
      <td>Music</td>
      <td>3:45</td>
      <td>Rock</td>
      <td>2000-08-12</td>
      <td>2000-09-16</td>
      <td>41</td>
      <td>23.0</td>
      <td>18.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2000</td>
      <td>Aguilera, Christina</td>
      <td>Come On Over Baby (All I Want Is You)</td>
      <td>3:38</td>
      <td>Rock</td>
      <td>2000-08-05</td>
      <td>2000-10-14</td>
      <td>57</td>
      <td>47.0</td>
      <td>45.0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 83 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-7f30bc9b-a8b2-423d-946e-cb7a1b4fbbfd')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-7f30bc9b-a8b2-423d-946e-cb7a1b4fbbfd button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-7f30bc9b-a8b2-423d-946e-cb7a1b4fbbfd');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-23c6777a-d55a-4ed8-a80f-d0ff89943f1e">
  <button class="colab-df-quickchart" onclick="quickchart('df-23c6777a-d55a-4ed8-a80f-d0ff89943f1e')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-23c6777a-d55a-4ed8-a80f-d0ff89943f1e button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>

Lo que querríamos es poder mantener todas las columnas excepto las columnas que incluyen "week" en el nombre. Para poder tener un formato "tidy" u "ordenado" deberíamos tener, por un lado, una columna week que indique el número de la semana (y preferentemente que sea un entero), y por otro lado una columna ranking con el valor del ranking en esa semana.

Para lograr ésto, vamos a usar la función **.melt**. Esta función recibe el DataFrame y vamos a usar el parámetro id_vars para pasarle la lista de columnas que van a ser constantes, es decir, que no van a variar. Con las demás columnas .melt va a:

1- tomar los nombres de columnas no incluídas en id_vars y convertirlos en una columna

2- va a tomar los valores de esas columnas y convertirlos en una segunda columna.

```python
pd.melt(billboard,
        id_vars=["year", "artist.inverted", "track", "time", "genre", "date.entered", "date.peaked"]).head()
```


  <div id="df-875e7df8-fda3-4a9e-890b-63e0488cba7e" class="colab-df-container">
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
      <th>year</th>
      <th>artist.inverted</th>
      <th>track</th>
      <th>time</th>
      <th>genre</th>
      <th>date.entered</th>
      <th>date.peaked</th>
      <th>variable</th>
      <th>value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2000</td>
      <td>Destiny's Child</td>
      <td>Independent Women Part I</td>
      <td>3:38</td>
      <td>Rock</td>
      <td>2000-09-23</td>
      <td>2000-11-18</td>
      <td>x1st.week</td>
      <td>78.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2000</td>
      <td>Santana</td>
      <td>Maria, Maria</td>
      <td>4:18</td>
      <td>Rock</td>
      <td>2000-02-12</td>
      <td>2000-04-08</td>
      <td>x1st.week</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2000</td>
      <td>Savage Garden</td>
      <td>I Knew I Loved You</td>
      <td>4:07</td>
      <td>Rock</td>
      <td>1999-10-23</td>
      <td>2000-01-29</td>
      <td>x1st.week</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2000</td>
      <td>Madonna</td>
      <td>Music</td>
      <td>3:45</td>
      <td>Rock</td>
      <td>2000-08-12</td>
      <td>2000-09-16</td>
      <td>x1st.week</td>
      <td>41.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2000</td>
      <td>Aguilera, Christina</td>
      <td>Come On Over Baby (All I Want Is You)</td>
      <td>3:38</td>
      <td>Rock</td>
      <td>2000-08-05</td>
      <td>2000-10-14</td>
      <td>x1st.week</td>
      <td>57.0</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-875e7df8-fda3-4a9e-890b-63e0488cba7e')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-875e7df8-fda3-4a9e-890b-63e0488cba7e button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-875e7df8-fda3-4a9e-890b-63e0488cba7e');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-0d938a19-a9c0-434c-bc34-ceb0550f8300">
  <button class="colab-df-quickchart" onclick="quickchart('df-0d938a19-a9c0-434c-bc34-ceb0550f8300')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-0d938a19-a9c0-434c-bc34-ceb0550f8300 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>

Ahora, querríamos que variable se llame week y value se llame ranking, para eso hacemos...


```python
billboard_2 = pd.melt(billboard,
                      id_vars=["year", "artist.inverted", "track", "time", "genre", "date.entered", "date.peaked"],
                      var_name="week",
                      value_name="ranking")
```

```python
billboard_2.head()
```


  <div id="df-99dd9e38-9673-4b1d-9e96-a5ed0b6bcfa9" class="colab-df-container">
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
      <th>year</th>
      <th>artist.inverted</th>
      <th>track</th>
      <th>time</th>
      <th>genre</th>
      <th>date.entered</th>
      <th>date.peaked</th>
      <th>week</th>
      <th>ranking</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2000</td>
      <td>Destiny's Child</td>
      <td>Independent Women Part I</td>
      <td>3:38</td>
      <td>Rock</td>
      <td>2000-09-23</td>
      <td>2000-11-18</td>
      <td>x1st.week</td>
      <td>78.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2000</td>
      <td>Santana</td>
      <td>Maria, Maria</td>
      <td>4:18</td>
      <td>Rock</td>
      <td>2000-02-12</td>
      <td>2000-04-08</td>
      <td>x1st.week</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2000</td>
      <td>Savage Garden</td>
      <td>I Knew I Loved You</td>
      <td>4:07</td>
      <td>Rock</td>
      <td>1999-10-23</td>
      <td>2000-01-29</td>
      <td>x1st.week</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2000</td>
      <td>Madonna</td>
      <td>Music</td>
      <td>3:45</td>
      <td>Rock</td>
      <td>2000-08-12</td>
      <td>2000-09-16</td>
      <td>x1st.week</td>
      <td>41.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2000</td>
      <td>Aguilera, Christina</td>
      <td>Come On Over Baby (All I Want Is You)</td>
      <td>3:38</td>
      <td>Rock</td>
      <td>2000-08-05</td>
      <td>2000-10-14</td>
      <td>x1st.week</td>
      <td>57.0</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-99dd9e38-9673-4b1d-9e96-a5ed0b6bcfa9')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-99dd9e38-9673-4b1d-9e96-a5ed0b6bcfa9 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-99dd9e38-9673-4b1d-9e96-a5ed0b6bcfa9');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-aef25101-3c4f-40b2-bf1c-94f515b99e65">
  <button class="colab-df-quickchart" onclick="quickchart('df-aef25101-3c4f-40b2-bf1c-94f515b99e65')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-aef25101-3c4f-40b2-bf1c-94f515b99e65 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>

### Ejercicios

1- Quédense sólo con la parte numérica de week sin usar regex, y conviertan a número los valores de la columna.

```python

```
2- Conviertan los valores de la columna ranking a entero. Tip: prueben usar pd.isna() para saber si un valor es nulo o no.

```python

```
3- Vean cuántas filas totales hay y eliminen las filas con nulos, ahora vuelvan a ver cuántas filas quedan.

```python

```

```python

```

```python

```
## Series de Tiempo

Las series de tiempo representan uno de los problemas mas interesantes en la ciencia de datos ya que refiere a eventos continuos y ordenados los cuales pueden ser independientes o tener alguna correlacion entre si. En este modulo veremos los metodos mas utilizados para manipular series de tiempo en pandas

### Datetime y metodos de manipulacion de series de tiempo

Para esta seccion vamos a utilizar el dataset de consumo energetico de Alemania.


```python
df_energia = pd.read_csv('https://raw.githubusercontent.com/jenfly/opsd/master/opsd_germany_daily.csv')
```

Primeramente vamos a evaluar el dataset


```python
df_energia.columns = ['Fecha', 'Consumo', 'Eolica', 'Solar', 'Suma']
df_energia.tail(10)
```

![[Pasted image 20230918195909.png]]


Las columnas son las siguientes:
    - Date — La fecha (yyyy-mm-dd)
    - Consumo — Electricidad Consumida en GWh
    - Eolica — Produccion de energia eolica en GWh
    - Solar — Produccion de energia solar en GWh
    - Suma — Suma de las dos anteriores GWh

Antes de comenzar a explorar el dataset, veamos algunas funciones de pandas para crear fechas. El metodo to_datetime nos permite transformar un string en cierto formato a un objeto del tipo Timestamp, el cual consiste de una fecha y una hora. Podemos ver que acepta varios formatos


```python
pd.to_datetime('2018-01-15 3:45pm')
```




    Timestamp('2018-01-15 15:45:00')




```python
pd.to_datetime('7/8/1952')
```




    Timestamp('1952-07-08 00:00:00')



Vamos a convertir el dtype de nuestra columna Fecha de object a  datetime64


```python
df_energia.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4383 entries, 0 to 4382
    Data columns (total 5 columns):
     #   Column   Non-Null Count  Dtype  
    ---  ------   --------------  -----  
     0   Fecha    4383 non-null   object 
     1   Consumo  4383 non-null   float64
     2   Eolica   2920 non-null   float64
     3   Solar    2188 non-null   float64
     4   Suma     2187 non-null   float64
    dtypes: float64(4), object(1)
    memory usage: 171.3+ KB
    


```python
df_energia["Fecha"] = pd.to_datetime(df_energia["Fecha"])
```


```python
df_energia.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4383 entries, 0 to 4382
    Data columns (total 5 columns):
     #   Column   Non-Null Count  Dtype         
    ---  ------   --------------  -----         
     0   Fecha    4383 non-null   datetime64[ns]
     1   Consumo  4383 non-null   float64       
     2   Eolica   2920 non-null   float64       
     3   Solar    2188 non-null   float64       
     4   Suma     2187 non-null   float64       
    dtypes: datetime64[ns](1), float64(4)
    memory usage: 171.3 KB
    

Convertir la columna *Fecha* en datetime nos permite filtrar usando la información temporal...

```python
df_energia.head()
```


  <div id="df-a54f4ea6-5e16-4a8b-8bc6-8db9e6ecde69" class="colab-df-container">
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
      <th>Fecha</th>
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2006-01-01</td>
      <td>1069.184</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2006-01-02</td>
      <td>1380.521</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2006-01-03</td>
      <td>1442.533</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2006-01-04</td>
      <td>1457.217</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2006-01-05</td>
      <td>1477.131</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-a54f4ea6-5e16-4a8b-8bc6-8db9e6ecde69')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-a54f4ea6-5e16-4a8b-8bc6-8db9e6ecde69 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-a54f4ea6-5e16-4a8b-8bc6-8db9e6ecde69');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-491afe15-2069-4a8c-8e5a-974c9dd0e632">
  <button class="colab-df-quickchart" onclick="quickchart('df-491afe15-2069-4a8c-8e5a-974c9dd0e632')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-491afe15-2069-4a8c-8e5a-974c9dd0e632 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




Podemos traernos los casos posteriores a 2009, por default a partir del 1ero de enero...


```python
df_energia[df_energia["Fecha"] > "2009"].head()
```





  <div id="df-290cc193-aaef-459e-acc5-aee0fd905ddc" class="colab-df-container">
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
      <th>Fecha</th>
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1097</th>
      <td>2009-01-02</td>
      <td>1161.911</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1098</th>
      <td>2009-01-03</td>
      <td>1178.078</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1099</th>
      <td>2009-01-04</td>
      <td>1130.021</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1100</th>
      <td>2009-01-05</td>
      <td>1333.041</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1101</th>
      <td>2009-01-06</td>
      <td>1340.896</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-290cc193-aaef-459e-acc5-aee0fd905ddc')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-290cc193-aaef-459e-acc5-aee0fd905ddc button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-290cc193-aaef-459e-acc5-aee0fd905ddc');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-18146c23-77ba-491b-b76a-64294940d05d">
  <button class="colab-df-quickchart" onclick="quickchart('df-18146c23-77ba-491b-b76a-64294940d05d')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-18146c23-77ba-491b-b76a-64294940d05d button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




Con el método **.between** podemos filtrar por un rango de fechas...


```python
df_energia[df_energia["Fecha"].between("2008", "2010")].head()
```





  <div id="df-96b2d3cb-5bbb-495e-b9ee-29fa37cd275f" class="colab-df-container">
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
      <th>Fecha</th>
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>730</th>
      <td>2008-01-01</td>
      <td>1083.424</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>731</th>
      <td>2008-01-02</td>
      <td>1396.483</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>732</th>
      <td>2008-01-03</td>
      <td>1523.427</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>733</th>
      <td>2008-01-04</td>
      <td>1512.429</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>734</th>
      <td>2008-01-05</td>
      <td>1355.843</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-96b2d3cb-5bbb-495e-b9ee-29fa37cd275f')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-96b2d3cb-5bbb-495e-b9ee-29fa37cd275f button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-96b2d3cb-5bbb-495e-b9ee-29fa37cd275f');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-f59f23e6-d9b1-48da-b327-f1b27ddad622">
  <button class="colab-df-quickchart" onclick="quickchart('df-f59f23e6-d9b1-48da-b327-f1b27ddad622')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-f59f23e6-d9b1-48da-b327-f1b27ddad622 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




En vez de filtrar usando años podemos pasar la fecha completa (siempre tengan presente el formato de la fecha)...


```python
df_energia[df_energia["Fecha"].between("2008-01-01", "2010-01-22")].head()
```





  <div id="df-707e06a4-ee7d-44c1-8106-7ceda6bcc7ee" class="colab-df-container">
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
      <th>Fecha</th>
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>730</th>
      <td>2008-01-01</td>
      <td>1083.424</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>731</th>
      <td>2008-01-02</td>
      <td>1396.483</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>732</th>
      <td>2008-01-03</td>
      <td>1523.427</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>733</th>
      <td>2008-01-04</td>
      <td>1512.429</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>734</th>
      <td>2008-01-05</td>
      <td>1355.843</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-707e06a4-ee7d-44c1-8106-7ceda6bcc7ee')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-707e06a4-ee7d-44c1-8106-7ceda6bcc7ee button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-707e06a4-ee7d-44c1-8106-7ceda6bcc7ee');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-ed323209-5670-4bfd-9037-6a40343374ff">
  <button class="colab-df-quickchart" onclick="quickchart('df-ed323209-5670-4bfd-9037-6a40343374ff')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-ed323209-5670-4bfd-9037-6a40343374ff button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




Y como si fuera poco también podemos filtrar sólo usando el año y el mes, sin especificar el día...


```python
df_energia[df_energia["Fecha"].between("2008-01", "2010-02")].head()
```





  <div id="df-3481ac0d-851a-4922-bed0-52c90d58c0ea" class="colab-df-container">
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
      <th>Fecha</th>
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>730</th>
      <td>2008-01-01</td>
      <td>1083.424</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>731</th>
      <td>2008-01-02</td>
      <td>1396.483</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>732</th>
      <td>2008-01-03</td>
      <td>1523.427</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>733</th>
      <td>2008-01-04</td>
      <td>1512.429</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>734</th>
      <td>2008-01-05</td>
      <td>1355.843</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-3481ac0d-851a-4922-bed0-52c90d58c0ea')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-3481ac0d-851a-4922-bed0-52c90d58c0ea button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-3481ac0d-851a-4922-bed0-52c90d58c0ea');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-7f78962e-c3a4-48c1-ab79-0b91cdb0af2c">
  <button class="colab-df-quickchart" onclick="quickchart('df-7f78962e-c3a4-48c1-ab79-0b91cdb0af2c')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-7f78962e-c3a4-48c1-ab79-0b91cdb0af2c button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>





```python
df_energia[df_energia["Fecha"].between("2008-01", "2010-02")].tail()
```





  <div id="df-d8ce19b7-3a0d-42e1-8a34-e4167ed3428b" class="colab-df-container">
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
      <th>Fecha</th>
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1488</th>
      <td>2010-01-28</td>
      <td>1585.269</td>
      <td>306.149</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1489</th>
      <td>2010-01-29</td>
      <td>1493.020</td>
      <td>145.473</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1490</th>
      <td>2010-01-30</td>
      <td>1322.933</td>
      <td>189.627</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1491</th>
      <td>2010-01-31</td>
      <td>1203.635</td>
      <td>174.109</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1492</th>
      <td>2010-02-01</td>
      <td>1536.453</td>
      <td>151.409</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-d8ce19b7-3a0d-42e1-8a34-e4167ed3428b')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-d8ce19b7-3a0d-42e1-8a34-e4167ed3428b button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-d8ce19b7-3a0d-42e1-8a34-e4167ed3428b');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-7d1e9eb4-4637-48e3-9074-7d850e6218ee">
  <button class="colab-df-quickchart" onclick="quickchart('df-7d1e9eb4-4637-48e3-9074-7d850e6218ee')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-7d1e9eb4-4637-48e3-9074-7d850e6218ee button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




Ahora, vamos a convertir nuestra columna Fecha en un índice temporal... Esto va a crear un nuevo tipo de objeto llamado DatetimeIndex


```python
df_energia = df_energia.set_index("Fecha")
```


```python
df_energia.tail(10)
```





  <div id="df-4294c144-46ce-4745-b2a2-fbbe37848431" class="colab-df-container">
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
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
    </tr>
    <tr>
      <th>Fecha</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-12-22</th>
      <td>1423.23782</td>
      <td>228.773</td>
      <td>10.065</td>
      <td>238.838</td>
    </tr>
    <tr>
      <th>2017-12-23</th>
      <td>1272.17085</td>
      <td>748.074</td>
      <td>8.450</td>
      <td>756.524</td>
    </tr>
    <tr>
      <th>2017-12-24</th>
      <td>1141.75730</td>
      <td>812.422</td>
      <td>9.949</td>
      <td>822.371</td>
    </tr>
    <tr>
      <th>2017-12-25</th>
      <td>1111.28338</td>
      <td>587.810</td>
      <td>15.765</td>
      <td>603.575</td>
    </tr>
    <tr>
      <th>2017-12-26</th>
      <td>1130.11683</td>
      <td>717.453</td>
      <td>30.923</td>
      <td>748.376</td>
    </tr>
    <tr>
      <th>2017-12-27</th>
      <td>1263.94091</td>
      <td>394.507</td>
      <td>16.530</td>
      <td>411.037</td>
    </tr>
    <tr>
      <th>2017-12-28</th>
      <td>1299.86398</td>
      <td>506.424</td>
      <td>14.162</td>
      <td>520.586</td>
    </tr>
    <tr>
      <th>2017-12-29</th>
      <td>1295.08753</td>
      <td>584.277</td>
      <td>29.854</td>
      <td>614.131</td>
    </tr>
    <tr>
      <th>2017-12-30</th>
      <td>1215.44897</td>
      <td>721.247</td>
      <td>7.467</td>
      <td>728.714</td>
    </tr>
    <tr>
      <th>2017-12-31</th>
      <td>1107.11488</td>
      <td>721.176</td>
      <td>19.980</td>
      <td>741.156</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-4294c144-46ce-4745-b2a2-fbbe37848431')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-4294c144-46ce-4745-b2a2-fbbe37848431 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-4294c144-46ce-4745-b2a2-fbbe37848431');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-66e3dd35-5eb9-4ebf-a501-746782b141e5">
  <button class="colab-df-quickchart" onclick="quickchart('df-66e3dd35-5eb9-4ebf-a501-746782b141e5')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-66e3dd35-5eb9-4ebf-a501-746782b141e5 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>





```python
df_energia.index
```




    DatetimeIndex(['2006-01-01', '2006-01-02', '2006-01-03', '2006-01-04',
                   '2006-01-05', '2006-01-06', '2006-01-07', '2006-01-08',
                   '2006-01-09', '2006-01-10',
                   ...
                   '2017-12-22', '2017-12-23', '2017-12-24', '2017-12-25',
                   '2017-12-26', '2017-12-27', '2017-12-28', '2017-12-29',
                   '2017-12-30', '2017-12-31'],
                  dtype='datetime64[ns]', name='Fecha', length=4383, freq=None)



Primeramente vamos a agregar columnas que nos proporcionen mas informacion sobre las fechas


```python
df_energia['Anio'] = df_energia.index.year
df_energia['Mes'] = df_energia.index.month
df_energia['Dia'] = df_energia.index.day_name()
df_energia.sample(5, random_state=0)
```





  <div id="df-bf9c8ab4-0642-4cc5-a42e-24c734ca9c51" class="colab-df-container">
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
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
      <th>Anio</th>
      <th>Mes</th>
      <th>Dia</th>
    </tr>
    <tr>
      <th>Fecha</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2008-08-23</th>
      <td>1152.011</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2008</td>
      <td>8</td>
      <td>Saturday</td>
    </tr>
    <tr>
      <th>2013-08-08</th>
      <td>1291.984</td>
      <td>79.666</td>
      <td>93.371</td>
      <td>173.037</td>
      <td>2013</td>
      <td>8</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <th>2009-08-27</th>
      <td>1281.057</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2009</td>
      <td>8</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <th>2015-10-02</th>
      <td>1391.050</td>
      <td>81.229</td>
      <td>160.641</td>
      <td>241.870</td>
      <td>2015</td>
      <td>10</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>2009-06-02</th>
      <td>1201.522</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2009</td>
      <td>6</td>
      <td>Tuesday</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-bf9c8ab4-0642-4cc5-a42e-24c734ca9c51')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-bf9c8ab4-0642-4cc5-a42e-24c734ca9c51 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-bf9c8ab4-0642-4cc5-a42e-24c734ca9c51');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-f7541efa-3a66-4954-9181-355f896859d9">
  <button class="colab-df-quickchart" onclick="quickchart('df-f7541efa-3a66-4954-9181-355f896859d9')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-f7541efa-3a66-4954-9181-355f896859d9 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




Como creamos el indice por las fechas, podemos localizar cualquier dia que querramos ahora


```python
df_energia.loc['2017-08-10']
```




    Consumo    1351.491
    Eolica      100.274
    Solar         71.16
    Suma        171.434
    Anio           2017
    Mes               8
    Dia        Thursday
    Name: 2017-08-10 00:00:00, dtype: object



Incluso podemos buscar rangos de fechas


```python
df_energia.loc['2014-01-20':'2014-01-22']
```





  <div id="df-93347c5b-6d1d-4638-bca4-d3dc66c35f54" class="colab-df-container">
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
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
      <th>Anio</th>
      <th>Mes</th>
      <th>Dia</th>
    </tr>
    <tr>
      <th>Fecha</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2014-01-20</th>
      <td>1590.687</td>
      <td>78.647</td>
      <td>6.371</td>
      <td>85.018</td>
      <td>2014</td>
      <td>1</td>
      <td>Monday</td>
    </tr>
    <tr>
      <th>2014-01-21</th>
      <td>1624.806</td>
      <td>15.643</td>
      <td>5.835</td>
      <td>21.478</td>
      <td>2014</td>
      <td>1</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>2014-01-22</th>
      <td>1625.155</td>
      <td>60.259</td>
      <td>11.992</td>
      <td>72.251</td>
      <td>2014</td>
      <td>1</td>
      <td>Wednesday</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-93347c5b-6d1d-4638-bca4-d3dc66c35f54')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-93347c5b-6d1d-4638-bca4-d3dc66c35f54 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-93347c5b-6d1d-4638-bca4-d3dc66c35f54');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-884f00ee-4259-4689-9deb-3eebc0ef607d">
  <button class="colab-df-quickchart" onclick="quickchart('df-884f00ee-4259-4689-9deb-3eebc0ef607d')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-884f00ee-4259-4689-9deb-3eebc0ef607d button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




O buscar por algun mes en particular


```python
df_energia.loc['2016-05']
```





  <div id="df-c974611f-8c5d-4b7d-ba16-9356a28f1139" class="colab-df-container">
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
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
      <th>Anio</th>
      <th>Mes</th>
      <th>Dia</th>
    </tr>
    <tr>
      <th>Fecha</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-05-01</th>
      <td>1078.602</td>
      <td>179.870</td>
      <td>147.931</td>
      <td>327.801</td>
      <td>2016</td>
      <td>5</td>
      <td>Sunday</td>
    </tr>
    <tr>
      <th>2016-05-02</th>
      <td>1405.185</td>
      <td>81.868</td>
      <td>197.183</td>
      <td>279.051</td>
      <td>2016</td>
      <td>5</td>
      <td>Monday</td>
    </tr>
    <tr>
      <th>2016-05-03</th>
      <td>1462.935</td>
      <td>208.678</td>
      <td>139.151</td>
      <td>347.829</td>
      <td>2016</td>
      <td>5</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>2016-05-04</th>
      <td>1430.136</td>
      <td>84.961</td>
      <td>174.185</td>
      <td>259.146</td>
      <td>2016</td>
      <td>5</td>
      <td>Wednesday</td>
    </tr>
    <tr>
      <th>2016-05-05</th>
      <td>1111.379</td>
      <td>150.624</td>
      <td>212.713</td>
      <td>363.337</td>
      <td>2016</td>
      <td>5</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <th>2016-05-06</th>
      <td>1254.051</td>
      <td>255.574</td>
      <td>217.569</td>
      <td>473.143</td>
      <td>2016</td>
      <td>5</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>2016-05-07</th>
      <td>1149.938</td>
      <td>315.362</td>
      <td>215.963</td>
      <td>531.325</td>
      <td>2016</td>
      <td>5</td>
      <td>Saturday</td>
    </tr>
    <tr>
      <th>2016-05-08</th>
      <td>1072.653</td>
      <td>390.557</td>
      <td>217.819</td>
      <td>608.376</td>
      <td>2016</td>
      <td>5</td>
      <td>Sunday</td>
    </tr>
    <tr>
      <th>2016-05-09</th>
      <td>1403.845</td>
      <td>360.421</td>
      <td>207.427</td>
      <td>567.848</td>
      <td>2016</td>
      <td>5</td>
      <td>Monday</td>
    </tr>
    <tr>
      <th>2016-05-10</th>
      <td>1431.813</td>
      <td>258.663</td>
      <td>157.710</td>
      <td>416.373</td>
      <td>2016</td>
      <td>5</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>2016-05-11</th>
      <td>1441.717</td>
      <td>304.436</td>
      <td>180.639</td>
      <td>485.075</td>
      <td>2016</td>
      <td>5</td>
      <td>Wednesday</td>
    </tr>
    <tr>
      <th>2016-05-12</th>
      <td>1444.324</td>
      <td>319.678</td>
      <td>129.861</td>
      <td>449.539</td>
      <td>2016</td>
      <td>5</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <th>2016-05-13</th>
      <td>1405.332</td>
      <td>216.936</td>
      <td>135.926</td>
      <td>352.862</td>
      <td>2016</td>
      <td>5</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>2016-05-14</th>
      <td>1168.618</td>
      <td>387.183</td>
      <td>132.009</td>
      <td>519.192</td>
      <td>2016</td>
      <td>5</td>
      <td>Saturday</td>
    </tr>
    <tr>
      <th>2016-05-15</th>
      <td>1048.215</td>
      <td>391.687</td>
      <td>130.935</td>
      <td>522.622</td>
      <td>2016</td>
      <td>5</td>
      <td>Sunday</td>
    </tr>
    <tr>
      <th>2016-05-16</th>
      <td>1080.327</td>
      <td>264.281</td>
      <td>115.660</td>
      <td>379.941</td>
      <td>2016</td>
      <td>5</td>
      <td>Monday</td>
    </tr>
    <tr>
      <th>2016-05-17</th>
      <td>1406.559</td>
      <td>193.380</td>
      <td>113.156</td>
      <td>306.536</td>
      <td>2016</td>
      <td>5</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>2016-05-18</th>
      <td>1432.772</td>
      <td>88.949</td>
      <td>151.707</td>
      <td>240.656</td>
      <td>2016</td>
      <td>5</td>
      <td>Wednesday</td>
    </tr>
    <tr>
      <th>2016-05-19</th>
      <td>1436.909</td>
      <td>60.078</td>
      <td>119.795</td>
      <td>179.873</td>
      <td>2016</td>
      <td>5</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <th>2016-05-20</th>
      <td>1415.619</td>
      <td>179.200</td>
      <td>144.397</td>
      <td>323.597</td>
      <td>2016</td>
      <td>5</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>2016-05-21</th>
      <td>1175.567</td>
      <td>133.517</td>
      <td>186.839</td>
      <td>320.356</td>
      <td>2016</td>
      <td>5</td>
      <td>Saturday</td>
    </tr>
    <tr>
      <th>2016-05-22</th>
      <td>1099.152</td>
      <td>217.768</td>
      <td>185.444</td>
      <td>403.212</td>
      <td>2016</td>
      <td>5</td>
      <td>Sunday</td>
    </tr>
    <tr>
      <th>2016-05-23</th>
      <td>1430.635</td>
      <td>179.097</td>
      <td>83.886</td>
      <td>262.983</td>
      <td>2016</td>
      <td>5</td>
      <td>Monday</td>
    </tr>
    <tr>
      <th>2016-05-24</th>
      <td>1454.007</td>
      <td>179.908</td>
      <td>57.672</td>
      <td>237.580</td>
      <td>2016</td>
      <td>5</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>2016-05-25</th>
      <td>1426.676</td>
      <td>27.068</td>
      <td>100.661</td>
      <td>127.729</td>
      <td>2016</td>
      <td>5</td>
      <td>Wednesday</td>
    </tr>
    <tr>
      <th>2016-05-26</th>
      <td>1221.096</td>
      <td>21.700</td>
      <td>169.098</td>
      <td>190.798</td>
      <td>2016</td>
      <td>5</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <th>2016-05-27</th>
      <td>1313.710</td>
      <td>37.271</td>
      <td>143.397</td>
      <td>180.668</td>
      <td>2016</td>
      <td>5</td>
      <td>Friday</td>
    </tr>
    <tr>
      <th>2016-05-28</th>
      <td>1169.531</td>
      <td>85.468</td>
      <td>160.593</td>
      <td>246.061</td>
      <td>2016</td>
      <td>5</td>
      <td>Saturday</td>
    </tr>
    <tr>
      <th>2016-05-29</th>
      <td>1096.905</td>
      <td>163.103</td>
      <td>124.929</td>
      <td>288.032</td>
      <td>2016</td>
      <td>5</td>
      <td>Sunday</td>
    </tr>
    <tr>
      <th>2016-05-30</th>
      <td>1423.574</td>
      <td>246.019</td>
      <td>121.137</td>
      <td>367.156</td>
      <td>2016</td>
      <td>5</td>
      <td>Monday</td>
    </tr>
    <tr>
      <th>2016-05-31</th>
      <td>1435.085</td>
      <td>106.179</td>
      <td>141.406</td>
      <td>247.585</td>
      <td>2016</td>
      <td>5</td>
      <td>Tuesday</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-c974611f-8c5d-4b7d-ba16-9356a28f1139')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-c974611f-8c5d-4b7d-ba16-9356a28f1139 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-c974611f-8c5d-4b7d-ba16-9356a28f1139');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-682a222c-18ef-424b-9cbc-ed9d09fb4563">
  <button class="colab-df-quickchart" onclick="quickchart('df-682a222c-18ef-424b-9cbc-ed9d09fb4563')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-682a222c-18ef-424b-9cbc-ed9d09fb4563 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




Ahora veamos como se ve nuestra data de consumo de energía


```python
#! pip install seaborn
import matplotlib.pyplot as plt
import seaborn as sns
df_energia['Consumo'].plot(linewidth=0.5);
```

![[output_131_0.png]]


## Ventanas y Medias moviles

Las ventanas moviles se refiere a aplicar alguna operacion de agregacion, por ejemplo el promedio sobre un conjunto de datos ordenados a la vez, por ejemplo el promedio de los ultimos 6 dias sobre cada conjunto ordenado de 6 dias en el dataset. Veamos un ejemplo para entenderlo mejor


```python
opsd_7d = df_energia["Consumo"].rolling(6).mean()
opsd_7d.head(10)
```




    Fecha
    2006-01-01            NaN
    2006-01-02            NaN
    2006-01-03            NaN
    2006-01-04            NaN
    2006-01-05            NaN
    2006-01-06    1371.668833
    2006-01-07    1410.186000
    2006-01-08    1381.430000
    2006-01-09    1395.895000
    2006-01-10    1415.844000
    Name: Consumo, dtype: float64



Podemos observar como las primeras 5 mediciones son Nan, ya que utiliza los primeros 5 valores para calcular a partir del 6to dia la media. El valor en el 7mo dia va a ser calculado con los datos del 2do al 6to dia, y asi sucesivamente.

Este tipo de metodos son particularmente utiles en analisis financiero.

## Shift y Diff

La operacion de Shift, como su nombre lo dice traducido al castellano, desplazar los datos una cantidad N de periodos. Veamoslo con el ejemplo del consumo, suponiendo que quiero crear otra columna con el consumo total del periodo anterior para poder compararlo con el actual


```python
df_energia['ConsumoAyer'] = df_energia['Suma'].shift(periods=1)

```

Veamos como quedo ahora el dataset


```python
df_energia.tail(10)
```





  <div id="df-841e0191-5614-49c2-866a-1b58ae0cb883" class="colab-df-container">
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
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
      <th>Anio</th>
      <th>Mes</th>
      <th>Dia</th>
      <th>ConsumoAyer</th>
    </tr>
    <tr>
      <th>Fecha</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-12-22</th>
      <td>1423.23782</td>
      <td>228.773</td>
      <td>10.065</td>
      <td>238.838</td>
      <td>2017</td>
      <td>12</td>
      <td>Friday</td>
      <td>266.352</td>
    </tr>
    <tr>
      <th>2017-12-23</th>
      <td>1272.17085</td>
      <td>748.074</td>
      <td>8.450</td>
      <td>756.524</td>
      <td>2017</td>
      <td>12</td>
      <td>Saturday</td>
      <td>238.838</td>
    </tr>
    <tr>
      <th>2017-12-24</th>
      <td>1141.75730</td>
      <td>812.422</td>
      <td>9.949</td>
      <td>822.371</td>
      <td>2017</td>
      <td>12</td>
      <td>Sunday</td>
      <td>756.524</td>
    </tr>
    <tr>
      <th>2017-12-25</th>
      <td>1111.28338</td>
      <td>587.810</td>
      <td>15.765</td>
      <td>603.575</td>
      <td>2017</td>
      <td>12</td>
      <td>Monday</td>
      <td>822.371</td>
    </tr>
    <tr>
      <th>2017-12-26</th>
      <td>1130.11683</td>
      <td>717.453</td>
      <td>30.923</td>
      <td>748.376</td>
      <td>2017</td>
      <td>12</td>
      <td>Tuesday</td>
      <td>603.575</td>
    </tr>
    <tr>
      <th>2017-12-27</th>
      <td>1263.94091</td>
      <td>394.507</td>
      <td>16.530</td>
      <td>411.037</td>
      <td>2017</td>
      <td>12</td>
      <td>Wednesday</td>
      <td>748.376</td>
    </tr>
    <tr>
      <th>2017-12-28</th>
      <td>1299.86398</td>
      <td>506.424</td>
      <td>14.162</td>
      <td>520.586</td>
      <td>2017</td>
      <td>12</td>
      <td>Thursday</td>
      <td>411.037</td>
    </tr>
    <tr>
      <th>2017-12-29</th>
      <td>1295.08753</td>
      <td>584.277</td>
      <td>29.854</td>
      <td>614.131</td>
      <td>2017</td>
      <td>12</td>
      <td>Friday</td>
      <td>520.586</td>
    </tr>
    <tr>
      <th>2017-12-30</th>
      <td>1215.44897</td>
      <td>721.247</td>
      <td>7.467</td>
      <td>728.714</td>
      <td>2017</td>
      <td>12</td>
      <td>Saturday</td>
      <td>614.131</td>
    </tr>
    <tr>
      <th>2017-12-31</th>
      <td>1107.11488</td>
      <td>721.176</td>
      <td>19.980</td>
      <td>741.156</td>
      <td>2017</td>
      <td>12</td>
      <td>Sunday</td>
      <td>728.714</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-841e0191-5614-49c2-866a-1b58ae0cb883')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-841e0191-5614-49c2-866a-1b58ae0cb883 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-841e0191-5614-49c2-866a-1b58ae0cb883');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-8488d4f6-f150-4a4d-887e-8714551b2562">
  <button class="colab-df-quickchart" onclick="quickchart('df-8488d4f6-f150-4a4d-887e-8714551b2562')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-8488d4f6-f150-4a4d-887e-8714551b2562 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




Podemos observar como la columna 'ConsumoAyer' es el valor de la columna 'Suma' exactamente del periodo anterior. Esto se puede realizar con tantos periodos como uno desee, pero hay que tener cuidado porque al inicio de nuestro dataset van a quedar valores Nan por la cantidad de periodos que elijamos. Hay que evaluar con que valor completamos esos valores.

Por ultimo supongamos que deseamos hacer la diferencia fila a fila del valor de ayer con el valor de hoy para el consumo total. Aqui nos conviene utilizar el metodo diff.


```python
df_energia['Diferencia'] = df_energia['Suma'].diff(1)
```


```python
df_energia.tail(10)
```





  <div id="df-7e7210da-1992-4e68-b1fd-c83b4d03704f" class="colab-df-container">
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
      <th>Consumo</th>
      <th>Eolica</th>
      <th>Solar</th>
      <th>Suma</th>
      <th>Anio</th>
      <th>Mes</th>
      <th>Dia</th>
      <th>ConsumoAyer</th>
      <th>Diferencia</th>
    </tr>
    <tr>
      <th>Fecha</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-12-22</th>
      <td>1423.23782</td>
      <td>228.773</td>
      <td>10.065</td>
      <td>238.838</td>
      <td>2017</td>
      <td>12</td>
      <td>Friday</td>
      <td>266.352</td>
      <td>-27.514</td>
    </tr>
    <tr>
      <th>2017-12-23</th>
      <td>1272.17085</td>
      <td>748.074</td>
      <td>8.450</td>
      <td>756.524</td>
      <td>2017</td>
      <td>12</td>
      <td>Saturday</td>
      <td>238.838</td>
      <td>517.686</td>
    </tr>
    <tr>
      <th>2017-12-24</th>
      <td>1141.75730</td>
      <td>812.422</td>
      <td>9.949</td>
      <td>822.371</td>
      <td>2017</td>
      <td>12</td>
      <td>Sunday</td>
      <td>756.524</td>
      <td>65.847</td>
    </tr>
    <tr>
      <th>2017-12-25</th>
      <td>1111.28338</td>
      <td>587.810</td>
      <td>15.765</td>
      <td>603.575</td>
      <td>2017</td>
      <td>12</td>
      <td>Monday</td>
      <td>822.371</td>
      <td>-218.796</td>
    </tr>
    <tr>
      <th>2017-12-26</th>
      <td>1130.11683</td>
      <td>717.453</td>
      <td>30.923</td>
      <td>748.376</td>
      <td>2017</td>
      <td>12</td>
      <td>Tuesday</td>
      <td>603.575</td>
      <td>144.801</td>
    </tr>
    <tr>
      <th>2017-12-27</th>
      <td>1263.94091</td>
      <td>394.507</td>
      <td>16.530</td>
      <td>411.037</td>
      <td>2017</td>
      <td>12</td>
      <td>Wednesday</td>
      <td>748.376</td>
      <td>-337.339</td>
    </tr>
    <tr>
      <th>2017-12-28</th>
      <td>1299.86398</td>
      <td>506.424</td>
      <td>14.162</td>
      <td>520.586</td>
      <td>2017</td>
      <td>12</td>
      <td>Thursday</td>
      <td>411.037</td>
      <td>109.549</td>
    </tr>
    <tr>
      <th>2017-12-29</th>
      <td>1295.08753</td>
      <td>584.277</td>
      <td>29.854</td>
      <td>614.131</td>
      <td>2017</td>
      <td>12</td>
      <td>Friday</td>
      <td>520.586</td>
      <td>93.545</td>
    </tr>
    <tr>
      <th>2017-12-30</th>
      <td>1215.44897</td>
      <td>721.247</td>
      <td>7.467</td>
      <td>728.714</td>
      <td>2017</td>
      <td>12</td>
      <td>Saturday</td>
      <td>614.131</td>
      <td>114.583</td>
    </tr>
    <tr>
      <th>2017-12-31</th>
      <td>1107.11488</td>
      <td>721.176</td>
      <td>19.980</td>
      <td>741.156</td>
      <td>2017</td>
      <td>12</td>
      <td>Sunday</td>
      <td>728.714</td>
      <td>12.442</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-7e7210da-1992-4e68-b1fd-c83b4d03704f')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-7e7210da-1992-4e68-b1fd-c83b4d03704f button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-7e7210da-1992-4e68-b1fd-c83b4d03704f');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-df0902ca-2626-42b7-bba7-1818c28f54c5">
  <button class="colab-df-quickchart" onclick="quickchart('df-df0902ca-2626-42b7-bba7-1818c28f54c5')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-df0902ca-2626-42b7-bba7-1818c28f54c5 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>



___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%