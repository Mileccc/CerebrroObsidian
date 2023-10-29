---
ID: 90
tags: 
nombre: Árboles de Decisión (decision trees) usando Entropía
---
___
# Árboles de Decisión (decision trees) usando Entropía
![](https://www.youtube.com/watch?v=z5rmY-LV7ME&ab_channel=C%C3%B3digoM%C3%A1quina)

___
**Resumen**
Los árboles de decisión son modelos de clasificación que consisten en un conjunto de reglas si-entonces que permiten predecir una clase objetivo. Se crean dividiendo recursivamente los datos en nodos basados en las variables predictoras. Son modelos interpretables que permiten entender fácilmente cómo se toman las decisiones. 

Utilizan medidas como la entropía para seleccionar las mejores variables en los nodos. La entropía mide la incertidumbre asociada a una variable aleatoria. Entre mayor sea la entropía de una variable, más útil es para clasificar. 

Se crean con algoritmos recursivos que particionan los datos y generan las ramas del árbol. Es importante controlar la profundidad para evitar sobreentrenamiento. Los hiperparámetros se ajustan con datos de validación.

**Puntos clave:**

- (02:04) Estructura de nodos de decisión y nodos terminales 
- (05:41) No requieren supuestos sobre distribución de datos
- (09:00) Explicación intuitiva de entropía y logaritmos
- (18:13) Entropía para seleccionar variables de nodos  
- (22:55) Separación de datos en entrenamiento y prueba
- (26:19) Creación de modelo con sklearn y entropía
- (39:50) Riesgo de sobreentrenamiento y sobreajuste



### Padecimientos cardíacos

  
## Gráfica dispersión: Edad y Colesterol

```python
import pandas as pd
import matplotlib.pyplot as plt
  
pacientes = pd.read_csv("pacientes.csv")
  
saludables = pacientes[pacientes["problema_cardiaco"]==0]
cardiacos = pacientes[pacientes["problema_cardiaco"]==1]
  
plt.figure(figsize=(6, 6))
plt.xlabel('Edad', fontsize = 20.0)
plt.ylabel('Colesterol', fontsize = 20.0)
plt.scatter(saludables["edad"], saludables["colesterol"],
            label="Saludable (Clase: 0)", marker="*", c="skyblue", s=200)
plt.scatter(cardiacos["edad"], cardiacos["colesterol"],
            label="Cardíaco (Clase: 1)", marker="*", c="lightcoral", s=200)
plt.legend(bbox_to_anchor=(1, 0.15))
plt.show()
```

  
  ![[output_4_0 2.png|800]]

## Entropía:

#### Promedio de información almacenada en una variable aleatoria

```python
from scipy.stats import entropy
from math import log
  
edades = pd.Series([40, 30, 20, 50])
colesterol = pd.Series([100, 110, 100, 110])
  
print(edades.value_counts()/edades.size)
print(colesterol.value_counts()/colesterol.size)
print(entropy(edades.value_counts()/edades.size, base=2))
print(entropy(colesterol.value_counts()/colesterol.size, base=2))
  
```

  
    30    0.25
    20    0.25
    50    0.25
    40    0.25
    dtype: float64
    110    0.5
    100    0.5
    dtype: float64
    2.0
    1.0


## Datos de Entrenamiento y Prueba

```python
from sklearn.model_selection import train_test_split
  
datos_entrena, datos_prueba, clase_entrena, clase_prueba = train_test_split(
    pacientes[["edad", "colesterol"]],
    pacientes["problema_cardiaco"],
    test_size=0.30)
```

## Creación del Árbol de Decisión

```python
from sklearn import tree
  
arbol_decision = tree.DecisionTreeClassifier(criterion="entropy")
  
arbol = arbol_decision.fit(datos_entrena, clase_entrena)
  
accuracy = arbol_decision.score(datos_prueba, clase_prueba)
  
print(accuracy)
  
print(tree.export_text(arbol,
                      feature_names=["Edad", "Colesterol"]))
plt.figure(figsize=(12, 6))
tree.plot_tree(arbol,
              feature_names=["Edad", "Colesterol"])
plt.show()
```

    0.4111111111111111
    |--- Edad <= 54.50
    |   |--- Colesterol <= 173.50
    |   |   |--- class: 0
    |   |--- Colesterol >  173.50
    |   |   |--- Colesterol <= 271.50
    |   |   |   |--- Edad <= 52.50
    |   |   |   |   |--- Edad <= 51.50
    |   |   |   |   |   |--- Colesterol <= 198.50
    |   |   |   |   |   |   |--- Colesterol <= 194.50
    |   |   |   |   |   |   |   |--- Edad <= 42.50
    |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |--- Edad >  42.50
    |   |   |   |   |   |   |   |   |--- Edad <= 44.50
    |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |   |--- Edad >  44.50
    |   |   |   |   |   |   |   |   |   |--- Edad <= 47.50
    |   |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |   |   |--- Edad >  47.50
    |   |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |--- Colesterol >  194.50
    |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |--- Colesterol >  198.50
    |   |   |   |   |   |   |--- Colesterol <= 217.00
    |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |--- Colesterol >  217.00
    |   |   |   |   |   |   |   |--- Edad <= 44.50
    |   |   |   |   |   |   |   |   |--- Colesterol <= 219.50
    |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |   |--- Colesterol >  219.50
    |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |--- Edad >  44.50
    |   |   |   |   |   |   |   |   |--- Colesterol <= 229.00
    |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |   |--- Colesterol >  229.00
    |   |   |   |   |   |   |   |   |   |--- Colesterol <= 233.50
    |   |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |   |   |--- Colesterol >  233.50
    |   |   |   |   |   |   |   |   |   |   |--- Edad <= 45.50
    |   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
    |   |   |   |   |   |   |   |   |   |   |--- Edad >  45.50
    |   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
    |   |   |   |   |--- Edad >  51.50
    |   |   |   |   |   |--- Colesterol <= 202.50
    |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |--- Colesterol >  202.50
    |   |   |   |   |   |   |--- Colesterol <= 226.50
    |   |   |   |   |   |   |   |--- Colesterol <= 204.50
    |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |--- Colesterol >  204.50
    |   |   |   |   |   |   |   |   |--- Colesterol <= 208.50
    |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |   |--- Colesterol >  208.50
    |   |   |   |   |   |   |   |   |   |--- Colesterol <= 217.50
    |   |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |   |   |--- Colesterol >  217.50
    |   |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |--- Colesterol >  226.50
    |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |--- Edad >  52.50
    |   |   |   |   |--- class: 1
    |   |   |--- Colesterol >  271.50
    |   |   |   |--- Colesterol <= 292.50
    |   |   |   |   |--- Colesterol <= 278.50
    |   |   |   |   |   |--- Colesterol <= 274.50
    |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |--- Colesterol >  274.50
    |   |   |   |   |   |   |--- Edad <= 47.50
    |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |--- Edad >  47.50
    |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |--- Colesterol >  278.50
    |   |   |   |   |   |--- class: 0
    |   |   |   |--- Colesterol >  292.50
    |   |   |   |   |--- Colesterol <= 304.50
    |   |   |   |   |   |--- class: 1
    |   |   |   |   |--- Colesterol >  304.50
    |   |   |   |   |   |--- Edad <= 51.50
    |   |   |   |   |   |   |--- Colesterol <= 308.50
    |   |   |   |   |   |   |   |--- Colesterol <= 305.50
    |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |--- Colesterol >  305.50
    |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |--- Colesterol >  308.50
    |   |   |   |   |   |   |   |--- Colesterol <= 313.00
    |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |--- Colesterol >  313.00
    |   |   |   |   |   |   |   |   |--- Colesterol <= 328.00
    |   |   |   |   |   |   |   |   |   |--- Edad <= 42.50
    |   |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |   |   |--- Edad >  42.50
    |   |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |   |--- Colesterol >  328.00
    |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |--- Edad >  51.50
    |   |   |   |   |   |   |--- class: 1
    |--- Edad >  54.50
    |   |--- Edad <= 63.50
    |   |   |--- Colesterol <= 251.50
    |   |   |   |--- Colesterol <= 235.00
    |   |   |   |   |--- Colesterol <= 222.50
    |   |   |   |   |   |--- Colesterol <= 206.50
    |   |   |   |   |   |   |--- Colesterol <= 202.50
    |   |   |   |   |   |   |   |--- Colesterol <= 190.00
    |   |   |   |   |   |   |   |   |--- Edad <= 60.50
    |   |   |   |   |   |   |   |   |   |--- Colesterol <= 172.00
    |   |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |   |   |--- Colesterol >  172.00
    |   |   |   |   |   |   |   |   |   |   |--- Edad <= 59.50
    |   |   |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |   |   |   |--- Edad >  59.50
    |   |   |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |   |--- Edad >  60.50
    |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |--- Colesterol >  190.00
    |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |--- Colesterol >  202.50
    |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |--- Colesterol >  206.50
    |   |   |   |   |   |   |--- Colesterol <= 213.50
    |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |--- Colesterol >  213.50
    |   |   |   |   |   |   |   |--- Edad <= 58.50
    |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |--- Edad >  58.50
    |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |--- Colesterol >  222.50
    |   |   |   |   |   |--- Edad <= 58.50
    |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |--- Edad >  58.50
    |   |   |   |   |   |   |--- Edad <= 59.50
    |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |--- Edad >  59.50
    |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |--- Colesterol >  235.00
    |   |   |   |   |--- Colesterol <= 240.50
    |   |   |   |   |   |--- class: 1
    |   |   |   |   |--- Colesterol >  240.50
    |   |   |   |   |   |--- Colesterol <= 246.00
    |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |--- Colesterol >  246.00
    |   |   |   |   |   |   |--- Colesterol <= 248.50
    |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |--- Colesterol >  248.50
    |   |   |   |   |   |   |   |--- Colesterol <= 249.50
    |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |--- Colesterol >  249.50
    |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |--- Colesterol >  251.50
    |   |   |   |--- Colesterol <= 337.50
    |   |   |   |   |--- Edad <= 59.50
    |   |   |   |   |   |--- Colesterol <= 266.00
    |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |--- Colesterol >  266.00
    |   |   |   |   |   |   |--- Colesterol <= 311.00
    |   |   |   |   |   |   |   |--- Colesterol <= 301.50
    |   |   |   |   |   |   |   |   |--- Edad <= 57.50
    |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |   |--- Edad >  57.50
    |   |   |   |   |   |   |   |   |   |--- Colesterol <= 283.50
    |   |   |   |   |   |   |   |   |   |   |--- Colesterol <= 276.50
    |   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
    |   |   |   |   |   |   |   |   |   |   |--- Colesterol >  276.50
    |   |   |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |   |   |--- Colesterol >  283.50
    |   |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |--- Colesterol >  301.50
    |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |--- Colesterol >  311.00
    |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |--- Edad >  59.50
    |   |   |   |   |   |--- class: 0
    |   |   |   |--- Colesterol >  337.50
    |   |   |   |   |--- Colesterol <= 400.50
    |   |   |   |   |   |--- Edad <= 56.00
    |   |   |   |   |   |   |--- Colesterol <= 347.50
    |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |--- Colesterol >  347.50
    |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |--- Edad >  56.00
    |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |--- Colesterol >  400.50
    |   |   |   |   |   |--- class: 0
    |   |--- Edad >  63.50
    |   |   |--- Colesterol <= 341.00
    |   |   |   |--- Colesterol <= 204.50
    |   |   |   |   |--- class: 1
    |   |   |   |--- Colesterol >  204.50
    |   |   |   |   |--- Colesterol <= 217.50
    |   |   |   |   |   |--- class: 0
    |   |   |   |   |--- Colesterol >  217.50
    |   |   |   |   |   |--- Colesterol <= 228.50
    |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |--- Colesterol >  228.50
    |   |   |   |   |   |   |--- Colesterol <= 259.50
    |   |   |   |   |   |   |   |--- Edad <= 68.00
    |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |--- Edad >  68.00
    |   |   |   |   |   |   |   |   |--- Colesterol <= 246.50
    |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |   |--- Colesterol >  246.50
    |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |--- Colesterol >  259.50
    |   |   |   |   |   |   |   |--- Colesterol <= 303.50
    |   |   |   |   |   |   |   |   |--- Colesterol <= 292.00
    |   |   |   |   |   |   |   |   |   |--- Edad <= 70.50
    |   |   |   |   |   |   |   |   |   |   |--- Edad <= 69.00
    |   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
    |   |   |   |   |   |   |   |   |   |   |--- Edad >  69.00
    |   |   |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |   |   |--- Edad >  70.50
    |   |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |   |--- Colesterol >  292.00
    |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |--- Colesterol >  303.50
    |   |   |   |   |   |   |   |   |--- Colesterol <= 311.00
    |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |   |   |   |   |   |   |--- Colesterol >  311.00
    |   |   |   |   |   |   |   |   |   |--- Colesterol <= 317.50
    |   |   |   |   |   |   |   |   |   |   |--- class: 1
    |   |   |   |   |   |   |   |   |   |--- Colesterol >  317.50
    |   |   |   |   |   |   |   |   |   |   |--- class: 0
    |   |   |--- Colesterol >  341.00
    |   |   |   |--- class: 1

  
  ![[output_13_1.png|1400]]


## Clasifica a nuevos pacientes
```python
print("Nuevo paciente", arbol_decision.predict([[70, 150]]))
```

    Nuevo paciente [1]


___

%%
tags: #pagmachine_learning #python   

Vínculos: [[000-Menú Machine Learning 📃|Menú Machine Learning 📃]] 
%%