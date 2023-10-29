---
ID: 3
tags: 
nombre: Kaggle Introducción a Machine Learning
---
___
# Kaggle Introducción a Machine Learning
---
## 1- Cómo funcionan los modelos
___
### Introducción
Empezaremos con una visión general de cómo funcionan los modelos de aprendizaje automático y cómo se utilizan. Esto puede parecer básico si has trabajado previamente en modelado estadístico o aprendizaje automático. No te preocupes, avanzaremos pronto para construir modelos potentes.

Este curso te llevará a construir modelos a medida que avanzas a través del siguiente escenario:

**Tu primo ha ganado millones de dólares especulando con bienes raíces. Te ha ofrecido asociarte en el negocio debido a tu interés en la ciencia de datos. Él aportará el dinero y tú proporcionarás modelos que predicen cuánto valen varias casas.**

Le preguntas a tu primo cómo ha predicho valores de bienes raíces en el pasado, y él dice que es solo intuición. Pero al hacer más preguntas, descubres que ha identificado patrones de precios en casas que ha visto en el pasado y utiliza esos patrones para hacer predicciones sobre nuevas casas que está considerando.

El aprendizaje automático funciona de la misma manera. Empezaremos con un modelo llamado el Árbol de Decisión. Hay modelos más sofisticados que ofrecen predicciones más precisas. Pero los árboles de decisión son fáciles de entender y son el bloque de construcción básico de algunos de los mejores modelos en la ciencia de datos.

Para simplificar, comenzaremos con el árbol de decisión más simple posible.

![[Pasted image 20231007170939.png|500]]

Divide las casas en solo dos categorías. El precio previsto para cualquier casa bajo consideración es el precio promedio histórico de las casas en la misma categoría.

Utilizamos datos para decidir cómo dividir las casas en dos grupos y nuevamente para determinar el precio previsto en cada grupo. Este paso de capturar patrones a partir de datos se llama ajustar o entrenar el modelo. Los datos utilizados para ajustar el modelo se llaman datos de entrenamiento.

Los detalles de cómo se ajusta el modelo (por ejemplo, cómo se divide el conjunto de datos) son lo suficientemente complejos como para que los guardemos para más adelante. Después de que el modelo haya sido ajustado, puedes aplicarlo a nuevos datos para predecir los precios de viviendas adicionales.

Entendido, aquí tienes el texto traducido y decorado con Markdown:


### Mejorando el Árbol de Decisión
¿Cuál de los siguientes dos árboles de decisión es más probable que resulte al ajustar los datos de entrenamiento de bienes raíces?

![[Pasted image 20231007171448.png|400]]![[Pasted image 20231007171422.png|450]]

El árbol de decisión de arriba (Árbol de Decisión 1) probablemente tiene más sentido, porque captura la realidad de que las casas con más dormitorios tienden a venderse a precios más altos que las casas con menos dormitorios. La mayor limitación de este modelo es que no captura la mayoría de los factores que afectan el precio de una vivienda, como el número de baños, el tamaño del lote, la ubicación, etc.

Puedes capturar más factores utilizando un árbol que tiene más "divisiones(splits)". Estos se llaman árboles "más profundos(deeper)". Un árbol de decisión que también considera el tamaño total del lote de cada casa podría verse así:

![[Pasted image 20231007172327.png|900]]


Predices el precio de cualquier casa siguiendo el árbol de decisión, siempre eligiendo el camino que corresponde a las características de esa casa. El precio previsto para la casa está en la parte inferior del árbol. El punto en la parte inferior donde hacemos una predicción se llama una hoja(**leaf**).

Las divisiones y los valores en las hojas se determinarán por los datos, así que es hora de que revises los datos con los que trabajarás.

___
## 2- Exploración básica de datos
### Usando Pandas para Familiarizarte con Tus Datos
El primer paso en cualquier proyecto de machine learning es familiarizarte con los datos. Utilizarás la librería Pandas para esto. Pandas es la herramienta principal que los científicos de datos usan para explorar y manipular datos. La mayoría de las personas abrevian pandas en su código como ``pd``. Hacemos esto con el comando

```python
import pandas as pd
```

La parte más importante de la librería Pandas es el DataFrame. Un DataFrame contiene el tipo de datos que podrías considerar como una tabla. Esto es similar a una hoja en Excel, o una tabla en una base de datos SQL.

Pandas tiene poderosos métodos para casi todo lo que querrás hacer con este tipo de datos.

Como ejemplo, veremos datos sobre precios de viviendas en Melbourne, Australia. En los ejercicios prácticos, aplicarás los mismos procesos a un nuevo conjunto de datos, que tiene precios de viviendas en Iowa.

Los datos de ejemplo (Melbourne) están en el file path `../input/melbourne-housing-snapshot/melb_data.csv`.

Cargamos y exploramos los datos con los siguientes comandos:

```python
import pandas as pd
  
# Ruta del archivo a leer
ruta_archivo = 'melb_data.csv'
# leer los datos y almacenarlos en un DataFrame titulado melbourne_data
melb_data = pd.read_csv(ruta_archivo)
# imprimir un resumen de los datos en Melbourne data
melb_data.describe()
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

      <th>Rooms</th>

      <th>Price</th>

      <th>Distance</th>

      <th>Postcode</th>

      <th>Bedroom2</th>

      <th>Bathroom</th>

      <th>Car</th>

      <th>Landsize</th>

      <th>BuildingArea</th>

      <th>YearBuilt</th>

      <th>Lattitude</th>

      <th>Longtitude</th>

      <th>Propertycount</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>count</th>

      <td>13580.000000</td>

      <td>1.358000e+04</td>

      <td>13580.000000</td>

      <td>13580.000000</td>

      <td>13580.000000</td>

      <td>13580.000000</td>

      <td>13518.000000</td>

      <td>13580.000000</td>

      <td>7130.000000</td>

      <td>8205.000000</td>

      <td>13580.000000</td>

      <td>13580.000000</td>

      <td>13580.000000</td>

    </tr>

    <tr>

      <th>mean</th>

      <td>2.937997</td>

      <td>1.075684e+06</td>

      <td>10.137776</td>

      <td>3105.301915</td>

      <td>2.914728</td>

      <td>1.534242</td>

      <td>1.610075</td>

      <td>558.416127</td>

      <td>151.967650</td>

      <td>1964.684217</td>

      <td>-37.809203</td>

      <td>144.995216</td>

      <td>7454.417378</td>

    </tr>

    <tr>

      <th>std</th>

      <td>0.955748</td>

      <td>6.393107e+05</td>

      <td>5.868725</td>

      <td>90.676964</td>

      <td>0.965921</td>

      <td>0.691712</td>

      <td>0.962634</td>

      <td>3990.669241</td>

      <td>541.014538</td>

      <td>37.273762</td>

      <td>0.079260</td>

      <td>0.103916</td>

      <td>4378.581772</td>

    </tr>

    <tr>

      <th>min</th>

      <td>1.000000</td>

      <td>8.500000e+04</td>

      <td>0.000000</td>

      <td>3000.000000</td>

      <td>0.000000</td>

      <td>0.000000</td>

      <td>0.000000</td>

      <td>0.000000</td>

      <td>0.000000</td>

      <td>1196.000000</td>

      <td>-38.182550</td>

      <td>144.431810</td>

      <td>249.000000</td>

    </tr>

    <tr>

      <th>25%</th>

      <td>2.000000</td>

      <td>6.500000e+05</td>

      <td>6.100000</td>

      <td>3044.000000</td>

      <td>2.000000</td>

      <td>1.000000</td>

      <td>1.000000</td>

      <td>177.000000</td>

      <td>93.000000</td>

      <td>1940.000000</td>

      <td>-37.856822</td>

      <td>144.929600</td>

      <td>4380.000000</td>

    </tr>

    <tr>

      <th>50%</th>

      <td>3.000000</td>

      <td>9.030000e+05</td>

      <td>9.200000</td>

      <td>3084.000000</td>

      <td>3.000000</td>

      <td>1.000000</td>

      <td>2.000000</td>

      <td>440.000000</td>

      <td>126.000000</td>

      <td>1970.000000</td>

      <td>-37.802355</td>

      <td>145.000100</td>

      <td>6555.000000</td>

    </tr>

    <tr>

      <th>75%</th>

      <td>3.000000</td>

      <td>1.330000e+06</td>

      <td>13.000000</td>

      <td>3148.000000</td>

      <td>3.000000</td>

      <td>2.000000</td>

      <td>2.000000</td>

      <td>651.000000</td>

      <td>174.000000</td>

      <td>1999.000000</td>

      <td>-37.756400</td>

      <td>145.058305</td>

      <td>10331.000000</td>

    </tr>

    <tr>

      <th>max</th>

      <td>10.000000</td>

      <td>9.000000e+06</td>

      <td>48.100000</td>

      <td>3977.000000</td>

      <td>20.000000</td>

      <td>8.000000</td>

      <td>10.000000</td>

      <td>433014.000000</td>

      <td>44515.000000</td>

      <td>2018.000000</td>

      <td>-37.408530</td>

      <td>145.526350</td>

      <td>21650.000000</td>

    </tr>

  </tbody>

</table>

</div>

### Interpretando la Descripción de los Datos
Los resultados muestran 8 números para cada columna en tu conjunto de datos original. El primer número, el ``count``, muestra cuántas filas tienen valores _no nulos_ (non-missing values).

Los valores faltantes (missing values) surgen por muchas razones. Por ejemplo, el tamaño del segundo dormitorio no se recogería al hacer una encuesta de una casa de 1 dormitorio. Volveremos al tema de los datos faltantes.

El segundo valor es la media (``mean``), que es el _promedio_. Debajo de eso, ``std`` es la _desviación estándar_, que mide cuán dispersos numéricamente están los valores.

Para interpretar los valores ``min``, 25%, 50%, 75% y ``max``, imagina ordenar cada columna del valor más bajo al más alto. El primer valor (el más pequeño) es el min. Si avanzas un cuarto del camino a través de la lista, encontrarás un número que es mayor que el 25% de los valores y menor que el 75% de los valores. Ese es el valor del 25% (pronunciado "percentil 25"). Los ``percentiles`` 50 y 75 se definen de manera análoga, y el max es el número más grande.

***Ejemplos básicos acceso a datos***

```python
# ¿Cuál es el tamaño promedio del lote (redondeado al entero más cercano)?
avg_lot_size = melb_data["Longtitude"].mean()
avg_lot_size
```

    144.99521618777615


```python
# A día de hoy, ¿cuántos años tiene la casa más nueva? (año actual - año en que fue construida)
año_actual=2023
newest_home_age = año_actual - melb_data["YearBuilt"]
newest_home_age
```

    0          NaN
    1        123.0
    2        123.0
    3          NaN
    4          9.0
             ...  
    13575     42.0
    13576     28.0
    13577     26.0
    13578    103.0
    13579    103.0
    Name: YearBuilt, Length: 13580, dtype: float64


```python
newest_home_age.min()
```

    5.0

___
## 3- Tu primer modelo de Machine Learning
### Seleccionar Datos para Modelar 
Tu conjunto de datos tenía demasiadas variables para entender de un vistazo, o incluso para imprimir de manera ordenada. ¿Cómo puedes reducir esta abrumadora cantidad de datos a algo que puedas comprender?

Comenzaremos seleccionando algunas variables utilizando nuestra intuición. Más adelante, los cursos te mostrarán técnicas estadísticas para priorizar automáticamente las variables.

Para elegir las variables/columnas, necesitamos ver una lista de todas las columnas en el conjunto de datos. Esto se hace con la propiedad "columns" del DataFrame (la última línea de código a continuación).




#### Continuar en visual estudio code y en kaggel
- Me quede en kaggel en el tema your first Machine Learning model
- Building Model



___

%%
tags: #pagmachine_learning #python   

Vínculos: [[000-Menú Machine Learning 📃|Menú Machine Learning 📃]] 
%%