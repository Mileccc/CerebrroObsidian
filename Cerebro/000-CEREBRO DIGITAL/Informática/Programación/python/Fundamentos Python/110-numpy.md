---
ID:: 110
tags:: #programación #pagfundamentospython #python   #choice #shuffle #randint #randn #rand #random #numpy
nombre:: "numpy"
---
___
# numpy
Se necesita importar un modulo para su uso
```python
import numpy as np
```
___
## Métodos o funciones
___
### random
Se utiliza para generar números aleatorios, lo que es especialmente útil en simulaciones, análisis estadísticos y otras aplicaciones donde se necesitan datos aleatorios.
#### rand
Genera números aleatorios en un array con distribución uniforme en el rango `[0, 1)`.
```python
random_array = np.random.rand(3, 3)  # Genera una matriz 3x3 de números aleatorios entre 0 y 1
```

#### randn
Genera números aleatorios de una distribución normal (gaussiana) con media 0 y desviación estándar 1.
```python
random_normal_array = np.random.randn(3, 3)  # Genera una matriz 3x3 de números aleatorios de distribución normal
```

#### randint
Genera números enteros aleatorios en un rango especificado.
```python
random_int = np.random.randint(1, 10)  # Genera un número entero aleatorio entre 1 y 9
```

#### shuffle
Permite reorganizar aleatoriamente los elementos de un array.
```python
arr = np.array([1, 2, 3, 4, 5])
np.random.shuffle(arr)  # Reorganiza aleatoriamente los elementos en el array
```
#### choice
Permite seleccionar elementos aleatorios de un array dado.
```python
options = ["rojo", "verde", "azul", "amarillo"]
random_choice = np.random.choice(options)  # Selecciona aleatoriamente un elemento de la lista
```

___

%%
tags:  #programación #pagfundamentospython #python  #choice #shuffle #randint #randn #rand #random #numpy

Vínculos:    [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%