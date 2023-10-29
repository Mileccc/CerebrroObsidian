---
ID: " 120"
tags: 
nombre: Impureza GINI
---
___
# Impureza GINI
___
![](https://www.youtube.com/watch?v=PFn31_hzQ2Y&ab_channel=C%C3%B3digoM%C3%A1quina)
___

**Resumen :

El video explica el concepto de impureza Gini, una métrica utilizada en algoritmos de aprendizaje automático como los bosques aleatorios. Se calcula para medir la capacidad de clasificación de un atributo en un conjunto de datos respecto a una variable objetivo. 

Se presenta un caso práctico de clasificación de jugadores de basquetbol según si llegan a ser veteranos, utilizando características como puntos, minutos, rebotes y asistencias por partido. Cada característica tiene asignado "alto" o "bajo" según esté por encima o por debajo del promedio.

Se muestra que la impureza Gini va de 0 a 1, donde 0 es perfectamente puro (clasifica sin error) y 1 es completamente impuro (no clasifica). Se calcula la impureza Gini de cada característica, resultando que rebotes tiene 0, asistencias 0.5 y puntos y minutos valores intermedios. Esto indica que rebotes clasifica perfectamente y asistencias no aporta nada a la clasificación.

Luego se explica paso a paso cómo calcular la impureza Gini mediante probabilidades a partir de conteos y agrupaciones. Se aplica el peso de cada categoría según la cantidad de instancias. Finalmente se obtiene el valor para la característica puntos.

**Mapa Mental Markdown:**
![[Pasted image 20231003233109.png]] 


# Contexto y Datos

```python
import pandas as pd
  
puntos_partido = pd.Series(["alto", "bajo", "alto", "alto", "alto",
                            "alto", "bajo", "alto", "alto", "bajo"])
  
minutos_partido = pd.Series(["alto", "alto", "bajo", "bajo", "bajo",
                             "alto", "bajo", "bajo", "bajo", "alto"])
  
rebotes_partido = pd.Series(["alto", "bajo", "bajo", "alto", "bajo",
                             "alto", "bajo", "alto", "bajo", "alto"])
  
asistencias_partido = pd.Series(["bajo", "bajo", "bajo", "bajo", "bajo",
                                 "bajo", "bajo", "bajo", "bajo", "bajo"])
  
# 1: Veterano (carrera de cinco años o más)
clase = pd.Series([1, 0, 0, 1, 0, 1, 0, 1, 0, 1])
  
datos = pd.DataFrame({"puntos": puntos_partido,
                      "minutos": minutos_partido,
                      "asistencias": asistencias_partido,
                      "rebotes": rebotes_partido,                      
                      "clase": clase})
```


# Interpretación de la Impureza GINI



```python
def impureza_gini(caracteristica, clase, datos):
    """str, str, DataFrame -> float"""    
    atributo_clase = datos.groupby([caracteristica, clase])[clase].count()
    atributo = datos.groupby([caracteristica])[clase].count()
    procesados = pd.merge(atributo_clase, atributo, on=[caracteristica],
                          suffixes=('_individual', '_total'))
    procesados["combinacion"] = (procesados[clase+"_individual"]/
                                 procesados[clase+"_total"])**2
    gini_combinacion = 1 - procesados.groupby([caracteristica, clase+"_total"])["combinacion"].sum()
    gini_pesado = (gini_combinacion * atributo) / atributo.sum()
    return gini_pesado.sum()
  
  
print("puntos -> impureza: %0.4f" % impureza_gini("puntos", "clase", datos))
print("minutos -> impureza: %0.4f" % impureza_gini("minutos", "clase", datos))
print("asistencias -> impureza: %0.4f" % impureza_gini("asistencias", "clase", datos))
print("rebotes -> impureza: %0.4f" % impureza_gini("rebotes", "clase", datos))
  
datos
```

  
    puntos -> impureza: 0.4762
    minutos -> impureza: 0.4167
    asistencias -> impureza: 0.5000
    rebotes -> impureza: 0.0000
  
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

      <th>puntos</th>

      <th>minutos</th>

      <th>asistencias</th>

      <th>rebotes</th>

      <th>clase</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>alto</td>

      <td>alto</td>

      <td>bajo</td>

      <td>alto</td>

      <td>1</td>

    </tr>

    <tr>

      <th>1</th>

      <td>bajo</td>

      <td>alto</td>

      <td>bajo</td>

      <td>bajo</td>

      <td>0</td>

    </tr>

    <tr>

      <th>2</th>

      <td>alto</td>

      <td>bajo</td>

      <td>bajo</td>

      <td>bajo</td>

      <td>0</td>

    </tr>

    <tr>

      <th>3</th>

      <td>alto</td>

      <td>bajo</td>

      <td>bajo</td>

      <td>alto</td>

      <td>1</td>

    </tr>

    <tr>

      <th>4</th>

      <td>alto</td>

      <td>bajo</td>

      <td>bajo</td>

      <td>bajo</td>

      <td>0</td>

    </tr>

    <tr>

      <th>5</th>

      <td>alto</td>

      <td>alto</td>

      <td>bajo</td>

      <td>alto</td>

      <td>1</td>

    </tr>

    <tr>

      <th>6</th>

      <td>bajo</td>

      <td>bajo</td>

      <td>bajo</td>

      <td>bajo</td>

      <td>0</td>

    </tr>

    <tr>

      <th>7</th>

      <td>alto</td>

      <td>bajo</td>

      <td>bajo</td>

      <td>alto</td>

      <td>1</td>

    </tr>

    <tr>

      <th>8</th>

      <td>alto</td>

      <td>bajo</td>

      <td>bajo</td>

      <td>bajo</td>

      <td>0</td>

    </tr>

    <tr>

      <th>9</th>

      <td>bajo</td>

      <td>alto</td>

      <td>bajo</td>

      <td>alto</td>

      <td>1</td>

    </tr>

  </tbody>

</table>

</div>

  
# Impureza del atributo 'puntos'

```python
# Cuántos jugadores por categoría de puntos y por clase (novato o veterano)
puntos_y_clase = datos.groupby(["puntos", "clase"])["clase"].count()
  
print("\n\nJUGADORES POR PUNTOS Y CLASE\n\n", puntos_y_clase)
  
# Cuántos jugadores por categoría de puntos
puntos = datos.groupby(["puntos"])["clase"].count()
  
print("\n\nJUGADORES POR PUNTOS\n\n", puntos)
  
# Unir ambas series de datos para procesamiento posterior
jugadores = pd.merge(
    puntos_y_clase,
    puntos,
    on=["puntos"],
    suffixes=('_indivual', '_total'))
  
print("\n\nUNION\n\n", jugadores)
```
  
    JUGADORES POR PUNTOS Y CLASE
     puntos  clase
    alto    0        3
            1        4
    bajo    0        2
            1        1
            
    Name: clase, dtype: int64
    JUGADORES POR PUNTOS
     puntos
    alto    7
    bajo    3
    Name: clase, dtype: int64
    UNION
    
             clase_indivual  clase_total
    puntos                            
    alto                 3            7
    alto                 4            7
    bajo                 2            3
    bajo                 1            3

  

# Cálculo de la Impureza GINI para 'puntos'

```python
# Probabilidad para cada categoría de puntos con respecto a la clase
jugadores["combinaciones"] = (jugadores["clase_indivual"]/jugadores["clase_total"])**2
print(jugadores)
  
# Impureza gini para cada combinación
gini_por_combinacion = 1 - jugadores.groupby(["puntos", "clase_total"])["combinaciones"].sum()
print("\n\n",gini_por_combinacion)
  
# Impureza gini para cada combinación con pesos
gini_con_peso_por_combinacion = (gini_por_combinacion * puntos) / puntos.sum()
print("\n\n", gini_con_peso_por_combinacion)
print("\n", gini_con_peso_por_combinacion.sum())
```

  
            clase_indivual  clase_total  combinaciones
    puntos                                            
    alto                 3            7       0.183673
    alto                 4            7       0.326531
    bajo                 2            3       0.444444
    bajo                 1            3       0.111111

     puntos  clase_total
    alto    7              0.489796
    bajo    3              0.444444
    Name: combinaciones, dtype: float64
    
     puntos  clase_total
    alto    7              0.342857
    bajo    3              0.133333
    dtype: float64
     0.4761904761904763

  

___

%%
tags: #pagmachine_learning #python   

Vínculos: [[000-Menú Machine Learning 📃|Menú Machine Learning 📃]] 
%%