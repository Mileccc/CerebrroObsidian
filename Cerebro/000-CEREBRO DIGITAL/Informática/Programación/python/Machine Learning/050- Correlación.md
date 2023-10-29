---
ID: " 050"
tags:
  - "#pagmachine_learning"
  - python
nombre: Correlación
---
___
# Correlación
___
## >>>> Correlación <<<<
![](https://www.youtube.com/watch?v=IBMrXyTR6CU&ab_channel=C%C3%B3digoM%C3%A1quina)

### Magnitud y dirección de una relación lineal entre 2 variables

```python
import matplotlib.pyplot as plt
import pandas as pd
  
personas = pd.read_csv("datos/personas.csv")
personas

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

      <th>altura</th>

      <th>peso</th>

      <th>ingreso</th>

      <th>horas_trabajadas</th>

      <th>ausencias</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>134.433878</td>

      <td>70.617864</td>

      <td>9973.577534</td>

      <td>40.905476</td>

      <td>4</td>

    </tr>

    <tr>

      <th>1</th>

      <td>167.158746</td>

      <td>109.268295</td>

      <td>8961.047249</td>

      <td>41.576483</td>

      <td>4</td>

    </tr>

    <tr>

      <th>2</th>

      <td>141.480812</td>

      <td>81.034644</td>

      <td>7437.977263</td>

      <td>41.369239</td>

      <td>5</td>

    </tr>

    <tr>

      <th>3</th>

      <td>123.227119</td>

      <td>57.884172</td>

      <td>12064.915290</td>

      <td>41.537211</td>

      <td>3</td>

    </tr>

    <tr>

      <th>4</th>

      <td>143.554951</td>

      <td>93.581094</td>

      <td>9296.396167</td>

      <td>40.441203</td>

      <td>4</td>

    </tr>

    <tr>

      <th>...</th>

      <td>...</td>

      <td>...</td>

      <td>...</td>

      <td>...</td>

      <td>...</td>

    </tr>

    <tr>

      <th>995</th>

      <td>169.059462</td>

      <td>109.612155</td>

      <td>9998.522402</td>

      <td>41.110352</td>

      <td>4</td>

    </tr>

    <tr>

      <th>996</th>

      <td>151.873081</td>

      <td>91.697127</td>

      <td>6867.097603</td>

      <td>40.617061</td>

      <td>5</td>

    </tr>

    <tr>

      <th>997</th>

      <td>131.156800</td>

      <td>78.301155</td>

      <td>9757.539280</td>

      <td>40.798085</td>

      <td>4</td>

    </tr>

    <tr>

      <th>998</th>

      <td>156.454396</td>

      <td>94.163603</td>

      <td>11044.031510</td>

      <td>41.443604</td>

      <td>3</td>

    </tr>

    <tr>

      <th>999</th>

      <td>149.558353</td>

      <td>87.134622</td>

      <td>13222.253800</td>

      <td>41.402637</td>

      <td>2</td>

    </tr>

  </tbody>

</table>

<p>1000 rows × 5 columns</p>

</div>


# Relación: Altura y Peso


```python

plt.scatter(personas["altura"], personas["peso"])

plt.xlabel("Altura (cms)")

plt.ylabel("Peso (kgs)")

plt.show()

```

  ![[output_4_0.png|700]]

# Relación: Ingreso y Horas Trabajadas

```python
plt.scatter(personas["ingreso"], personas["horas_trabajadas"])
plt.xlabel("Ingreso ($)")
plt.ylabel("Horas Trabajadas")
plt.show()
```


![[output_7_0 1.png|700]]

  

# Relación: Ingreso y Ausencias

```python
plt.scatter(personas["ingreso"], personas["ausencias"])
plt.xlabel("Ingreso ($)")
plt.ylabel("Ausencias")
plt.show()
```

![[output_10_0.png|700]]

# Relación: Ingreso y Peso de una persona

```python
plt.scatter(personas["ingreso"], personas["peso"])
plt.xlabel("Ingreso ($)")
plt.ylabel("Peso (kg)")
plt.show()
```

  
![[output_13_0 1.png|700]]


# Matriz de Correlación

```python
matriz = personas.corr() # -1 (existe una relación fuerte)  0   1 (existe relación fuerte)
plt.matshow(matriz, cmap="bwr", vmin=-1, vmax=1)
plt.xticks(range(5), personas.columns, rotation=90)
plt.yticks(range(5), personas.columns)
  
for i in range(len(matriz.columns)):
    for j in range(len(matriz.columns)):
        plt.text(i, j, round(matriz.iloc[i, j], 2),
                 ha="center", va="center")
  
plt.colorbar()
plt.show()
```

  
  ![[output_16_0.png|700]]

___

%%
tags: #pagmachine_learning #python   
Vínculos: [[000-Menú Machine Learning 📃|Menú Machine Learning 📃]] 
%%