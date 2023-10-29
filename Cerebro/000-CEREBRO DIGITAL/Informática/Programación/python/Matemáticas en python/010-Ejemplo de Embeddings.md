---
ID: 10
"tags:": 
nombre: Ejemplo de Embeddings
---
___

# Ejemplo de Embeddings

![](https://youtu.be/Wxj0u0vqUk0?t=4493)
___

## Embedding de personalidad: ¿Cómo somos?

En una escala de 0 a 100, ¿Qué tan introvertido/extrovertido eres (donde 0 es el más introvertido y 100 es el más extrovertido)? ¿Alguna vez ha realizado una prueba de personalidad como la prueba de los Cinco Grandes Rasgos de la Personalidad? Si no lo has hecho, estas son pruebas que te hacen una lista de preguntas, y luego te califican en una serie de ejes, siendo la introversión/extraversión uno de ellos.

Imaginemos que Jay obtuvo una puntuación de 38/100 en el rasgo introversión/extraversión. Podemos graficar eso de esta manera:

![[introversion-extraversion-100.png|600]]

Supongamos que, además de ese, también contemplamos otro de los 5 rasgos y que las escalas de 0 a 100 son reemplazadas por una escala de -1 a 1. Así obtendríamos un vector que represente a Jay de la siguiente manera:

![[two-traits-vector.png|600]]

Ahora podemos decir que este vector representa parcialmente la personalidad de Jay. La utilidad de tal representación viene cuando compararlo con otras dos personas. Digamos que lo atropella un autobús y necesita ser reemplazado por alguien con una personalidad similar. En la siguiente figura, ¿Cuál de las dos personas se parece más a Jay?

![[personality-two-persons.png|600]]

Podemos ver que la persona n° 1 es más parecida a Jay porque gráficamente su vector está más "cerca" al de Jay. Ahora supongamos que tenemos un vector con los 5 rasgos... el análisis gráfico no es una opción. Sin embargo, podemos calcular la similaridad a través del ángulo entre los vectores (que se calcula utilizando el coseno como ya vimos) para obtener una métrica que facilite la comparación.

![[embeddings-cosine-personality.png|800]]

Seguimos viendo que la persona más parecida es la n°1, pero ahora tenemos una métrica para saber cuán mejor reemplazo es con respecto a la otra persona.

## Embedding de palabras: ¿Cómo codificamos el significado?
Para que las palabras sean procesadas por modelos de aprendizaje automático, necesitan alguna forma de representación numérica que los modelos puedan usar en sus cálculos. Ahora que entendemos el poder de representación de los vectores, podemos proceder a observar ejemplos de vectores de palabras entrenados (también llamados embeddings de palabras) y comenzar a observar algunas de sus propiedades interesantes.

Word2Vec fue el primer algoritmo en demostrar que podemos usar un vector para representar correctamente las palabras de una manera que capturara las relaciones semánticas o de significado. Por ejemplo, al analizar estos vectores podemos saber si las palabras son similares u opuestas (analizando la dirección y el sentido del vector), o que un par de palabras como “Estocolmo” y “Suecia” tienen entre ellas la misma relación que tienen “El Cairo” y “Egipto” (analizando las distancias entre los vectores), o también relaciones sintácticas o basadas en la gramática (por ejemplo, la relación entre “tenía” y “tengo” es la misma que entre “era” y “es”).

Este es un embedding para la palabra "rey" (vector GloVe entrenado en Wikipedia):

```
0.50451,0.68607,−0.59517,−0.022801,0.60046,−0.13498,−0.08813,0.47377,−0.61798,−0.31012,−0.076666,1.493,−0.034189,−0.98173,0.68229,0.81722,−0.51874,−0.31503,−0.55809,0.66421,0.1961,−0.13495,−0.11476,−0.30344,0.41177,−2.223,−1.0756,−1.0783,−0.34354,0.33505,1.9927,−0.04234,−0.64319,0.71125,0.49159,0.16754,0.34344,−0.25663,−0.8523,0.1661,0.40102,1.1685,−1.0137,−0.21585,−0.15155,0.78321,−0.91241,−1.6106,−0.64426,−0.51042
```
---

Es una lista de 50 números. No podemos decir mucho mirando los valores. Pero visualicémoslo un poco para poder compararlo con otros vectores de palabras. Pongamos todos estos números en una fila y codifiquemos por colores las celdas según sus valores (rojo si están cerca de 2, blanco si están cerca de 0, azul si están cerca de -2):

![[king-colored-embedding.png|1700]]

Procederemos ignorando los números y solo observando los colores para indicar los valores de las celdas. Ahora comparemos "Rey" con otras palabras:

![[Sin título.png|800]]

Algunas cosas para señalar:

- Hay una columna roja recta a través de todas estas palabras diferentes. Son similares a lo largo de esa dimensión (y no sabemos qué codifica cada dimensión)
- Puedes ver cómo "mujer" y "niña" son similares entre sí en muchos lugares. Lo mismo con "hombre" y "niño"
- “niño” y “niña” también tienen lugares donde son similares entre sí, pero diferentes de “mujer” u “hombre”. ¿Podrían estar codificando una vaga concepción de la juventud?
- Todas menos la última palabra son palabras que representan personas. Podemos, por ejemplo, ver que la columna azul va hacia abajo y se detiene antes del embedding de "agua".
- Hay lugares claros donde "rey" y "reina" son similares entre sí y distintos de todos los demás. ¿Podrían estar codificando un concepto vago de realeza?

Otro ejemplo más que prueba lo poderosos que son estos embeddings es el concepto de las analogías. Podemos sumar y restar embeddings de palabras y llegar a resultados interesantes. El ejemplo más famoso es la fórmula: "rey" - "hombre" + "mujer":

![[king-analogy-viz.png|800]]

El vector resultante de "rey-hombre+mujer" no es exactamente igual a "reina", pero "reina" es la palabra más cercana de los 400 000 embeddings de palabras que tenemos en esta colección.

Algo importante que debe quedar claro es que, en contraste con los embeddings de personalidad que analizamos anteriormente, **_no sabemos que codifica cada dimensión del vector_**. Podemos hacer conjeturas y experimentos que nos permitan validar que estos vectores están modelando de alguna u otra forma la semántica, pero esta codificación de los datos es la que a la red le pareció la más eficiente durante el entrenamiento.


___

%%
tags:  #programación #pagmatpython #python  #embedding

Vínculos:  [[000-Menú Matemáticas Python 📃|Menú Matemáticas en python📃]]
%%