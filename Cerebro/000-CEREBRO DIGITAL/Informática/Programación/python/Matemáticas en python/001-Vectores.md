---
ID: 1
"tags:": 
nombre: Vectores
---
___

# Vectores

![](https://www.youtube.com/watch?v=Wxj0u0vqUk0)

<a href="https://colab.research.google.com/github/institutohumai/cursos-python/blob/master/MatematicasParaIA/1_Vectores/vectores.ipynb"> <img src='https://colab.research.google.com/assets/colab-badge.svg' /> </a>

# **Vectores**
El concepto de vector tiene dos significados ligeramente diferentes si lo observamos desde el punto de vista de la matemática o desde el punto de vista de la computación. Cuando hacemos ciencia de datos, solemos tomarnos la libertad de llamar vectores a ciertas estructuras de datos que, si lo analizamos estrictamente desde el sentido matemático, no lo son. Sin embargo, desde un sentido práctico, son tan similares que resulta beneficioso estudiar los conceptos y las operaciones asociadas a los vectores matemáticos para poder aplicarlos sobre estas estructuras de datos computacionales. 



## Definición matemática
En matemática, un vector es un **segmento de recta orientado**, que depende de un **sistema de coordenadas**, en el cual se puede llevar adelante un importante número de operaciones. 

Los vectores son muy usados en física para representar a las llamadas **magnitudes vectoriales**, que son aquellas que están dotadas no sólo de intensidad, sino de **dirección**, como es el caso de la fuerza, la velocidad o el desplazamiento. Ese rasgo de contar con dirección es el que distingue a las magnitudes vectoriales de las escalares.

Todo vector tiene las siguientes características geométricas:

* **Dirección**: la dirección de un vector corresponde a la dirección de la recta que contiene el vector o cualquier recta paralela a ella. Dicho con otras palabras, la dirección de un vector es la línea recta sobre la que está situado.
*  **Sentido**: el sentido de un vector es la orientación de dicho vector, lo indica su flecha.
* **Módulo**: el módulo de un vector es su longitud, y corresponde al valor numérico del vector. Por lo tanto, cuanto mayor sea el vector significa que más grande es la magnitud vectorial que representa.
* **Punto de aplicación**: el punto de aplicación de un vector es el origen de dicho vector.

![caracteristicas-de-un-vector.webp](data:image/webp;base64,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)

\
Acabamos de ver que los vectores se representan gráficamente mediante flechas, pero también se los puede representar numéricamente mediante sus **componentes** (o coordenadas). Por ejemplo, la velocidad de un cohete es un vector tridimensional: su magnitud es la rapidez del cohete y su dirección es (con suerte) hacia arriba. Supongamos que el cohete sube con un ligero ángulo: tiene una velocidad vertical de 5000 m/s, y también una ligera velocidad hacia el este de 10 m/s, y una ligera velocidad hacia el norte de 50 m/s. s. La velocidad del cohete se puede representar mediante el siguiente vector:

**velocidad** 
$= \begin{pmatrix}
10\\
50\\
5000
\end{pmatrix}$

Nota: por convención, los vectores generalmente se presentan en forma de columnas. Además, los nombres de los vectores suelen estar en **minúsculas** para distinguirlos de las matrices (de las que hablaremos más adelante) y **en negrita** (cuando sea posible) para distinguirlos de valores escalares simples.

\
##  Definición en computación
En computación se le suele llamar vector a los arreglos unidimensionales que son un tipo de datos estructurado que está formado por una colección **finita y ordenada** de datos **del mismo tipo**. 

Los vectores computacionales son muy usados en machine learning, sobre todo para representar **observaciones** y **predicciones**. Por ejemplo, supongamos que construimos un sistema de aprendizaje automático para clasificar videos en 3 categorías (bueno, spam, clickbait) según lo que sabemos sobre ellos. Para cada video, podríamos un vector que representa lo que sabemos sobre él, como:

**video** $= \begin{pmatrix}
10.5 \\
5.2 \\
3.25 \\
7.0
\end{pmatrix}$

Este vector podría representar un video que dura 10,5 minutos, pero solo el 5,2% de los espectadores miran más de un minuto, obtiene un promedio de 3,25 vistas por día y se marcó 7 veces como spam. Como puede ver, cada componente puede tener un significado diferente.

Según este vector, nuestro sistema de aprendizaje automático puede predecir que existe un 80 % de probabilidad de que sea un video no deseado, un 18 % de que sea clickbait y un 2 % de que sea un buen video. Esto podría representarse como el siguiente vector:

**probabilidades_de_clase** $= \begin{pmatrix}
0,80 \\
0.18 \\
0.02
\end{pmatrix}$



## Vectores en python
En python, un vector se puede representar de muchas maneras, la más simple es una lista de números de python normal:


```python
[10.5, 5.2, 3.25, 7.0]
```




    [10.5, 5.2, 3.25, 7.0]



Dado que planeamos hacer una gran cantidad de cálculos científicos, es mucho mejor usar `ndarray` de NumPy, que proporciona muchas implementaciones convenientes y optimizadas de operaciones matemáticas esenciales en vectores (para obtener más detalles sobre NumPy, consulte [NumPy tutorial](tools_numpy.ipynb)). Por ejemplo:


```python
import numpy as np
video = np.array([10.5, 5.2, 3.25, 7.0])
video
```




    array([10.5 ,  5.2 ,  3.25,  7.  ])



El tamaño de un vector se puede obtener usando el atributo `size`:


```python
video.size
```




    4



El iésimo elemento (en la posición i) de un vector $\textbf{v}$ se anota como $\textbf{v}_i$.

Tenga en cuenta que los índices en matemáticas generalmente comienzan en 1, pero en programación generalmente comienzan en 0. Entonces, para acceder a $\textbf{video}_3$ programáticamente, escribiríamos:


```python
video[2]  # 3rd element
```




    3.25



## Graficar vectores
Para graficar vectores usaremos matplotlib, así que comencemos importándolo (para obtener detalles sobre matplotlib, consulte el [tutorial de matplotlib](tools_matplotlib.ipynb)):


```python
%matplotlib inline
import matplotlib.pyplot as plt
```

### Vectores 2D
Vamos a crear un par de vectores 2D muy simples para graficar:


```python
u = np.array([2, 5])
v = np.array([3, 1])
```

Cada uno de estos vectores tiene 2 elementos, por lo que se pueden representar gráficamente fácilmente en un gráfico 2D, por ejemplo, como puntos:


```python
x_coords, y_coords = zip(u, v)
plt.scatter(x_coords, y_coords, color=["r","b"])
plt.axis([0, 9, 0, 6])
plt.grid()
plt.show()
```


    
![png](output_15_0.png)
    


Los vectores también se pueden representar como flechas. Vamos a crear una pequeña función de conveniencia para dibujar  flechas bonitas:


```python
def plot_vector2d(vector2d, origin=[0, 0], **options):
    return plt.arrow(origin[0], origin[1], vector2d[0], vector2d[1],
              head_width=0.2, head_length=0.3, length_includes_head=True,
              **options)
```

Ahora dibujemos los vectores **u** y **v** como flechas:


```python
plot_vector2d(u, color="r")
plot_vector2d(v, color="b")
plt.axis([0, 9, 0, 6])
plt.grid()
plt.show()
```


    
![png](output_19_0.png)
    


### Vectores 3D
Dibujar vectores 3D también es relativamente sencillo. Primero vamos a crear dos vectores 3D:


```python
a = np.array([1, 2, 8])
b = np.array([5, 6, 3])
```

Ahora vamos a trazarlos usando `Axes3D` de matplotlib:


```python
from mpl_toolkits.mplot3d import Axes3D

subplot3d = plt.subplot(111, projection='3d')
x_coords, y_coords, z_coords = zip(a,b)
subplot3d.scatter(x_coords, y_coords, z_coords)
subplot3d.set_zlim3d([0, 9])
plt.show()
```


    
![png](output_23_0.png)
    


Es un poco difícil visualizar exactamente dónde están estos dos puntos en el espacio, así que agreguemos algunas líneas verticales y horizontales. Crearemos una pequeña función de conveniencia para trazar una lista de vectores 3D con líneas verticales adjuntas:


```python
def plot_vectors3d(ax, vectors3d, z0, **options):
    for v in vectors3d:
        x, y, z = v
        ax.plot([x,x], [y,y], [z0, z], color="gray", linestyle='dotted', marker=".")
        ax.plot([0,x], [y,y], [z, z], color="gray", linestyle='dotted', marker=".")
    x_coords, y_coords, z_coords = zip(*vectors3d)
    ax.scatter(x_coords, y_coords, z_coords, **options)

subplot3d = plt.subplot(111, projection='3d')
subplot3d.set_zlim([0, 9])
plot_vectors3d(subplot3d, [a,b], 0, color=("r","b"))
plt.show()
```


    
![png](output_25_0.png)
    


## Norma
La norma de un vector $\textbf{u}$, anotada $\left \Vert \textbf{u} \right \|$, es una medida de la longitud (también conocida como la magnitud) de $\textbf{u}$. Hay múltiples normas posibles, pero la más común (y la única que discutiremos aquí) es la norma euclidiana, que se define como:

$\left \Vert \textbf{u} \right \| = \sqrt{\sum_{i}{\textbf{u}_i}^2}$

Podríamos implementar esto fácilmente en Python puro, recordando que $\sqrt x = x^{\frac{1}{2}}$


```python
def vector_norm(vector):
    squares = [element**2 for element in vector]
    return sum(squares)**0.5

print("||", u, "|| =")
vector_norm(u)
```

    || [2 5] || =
    




    5.385164807134504



Sin embargo, es mucho más eficiente usar la función `norm` de NumPy, disponible en el módulo `linalg` (**Lin**ear **Alg**ebra):


```python
import numpy.linalg as LA
LA.norm(u)
```




    5.385164807134504



Tracemos un pequeño diagrama para confirmar que la longitud del vector $\textbf{v}$ es de hecho $\approx5.4$:


```python
radius = LA.norm(u)
plt.gca().add_artist(plt.Circle((0,0), radius, color="#DDDDDD"))
plot_vector2d(u, color="r")
plt.axis([0, 8.7, 0, 6])
plt.grid()
plt.show()
```


    
![png](output_31_0.png)
    


¡Se ve bien!

## Adición
Se pueden sumar vectores del mismo tamaño. La suma se realiza *elemento a elemento*:


```python
w = np.array([4, 2])
print(" ", u)
print("+", v)
print("+", w)
print("-"*10)
u + v + w
```

      [2 5]
    + [3 1]
    + [4 2]
    ----------
    




    array([9, 8])



Veamos cómo se ve gráficamente la suma de vectores:


```python
plot_vector2d(u, color="r")
plot_vector2d(v, color="b")
plot_vector2d(v, origin=u, color="b", linestyle="dotted")
plot_vector2d(u, origin=v, color="r", linestyle="dotted")
plot_vector2d(u+v, color="g")
plt.axis([0, 9, 0, 7])
plt.text(0.7, 3, "u", color="r", fontsize=18)
plt.text(4, 3, "u", color="r", fontsize=18)
plt.text(1.8, 0.2, "v", color="b", fontsize=18)
plt.text(3.1, 5.6, "v", color="b", fontsize=18)
plt.text(2.4, 2.5, "u+v", color="g", fontsize=18)
plt.grid()
plt.show()
```


    
![png](output_36_0.png)
    


La suma de vectores es **conmutativa**, lo que significa que $\textbf{u} + \textbf{v} = \textbf{v} + \textbf{u}$. Puedes verlo en la imagen anterior: siguiendo $\textbf{u}$ *luego* $\textbf{v}$ lleva al mismo punto que siguiendo $\textbf{v}$ *luego* $\textbf{u} $

La suma de vectores también es **asociativa**, lo que significa que $\textbf{u} + (\textbf{v} + \textbf{w}) = (\textbf{u} + \textbf{v}) + \textbf{ w}$.

Si tiene un polígono definido por una cantidad de puntos (vectores) y suma un vector $\textbf{v}$ a todos estos puntos, entonces todo el polígono se desplaza $\textbf{v}$. Esto se llama [traslación geométrica](https://en.wikipedia.org/wiki/Translation_%28geometry%29):


```python
t1 = np.array([2, 0.25])
t2 = np.array([2.5, 3.5])
t3 = np.array([1, 2])

x_coords, y_coords = zip(t1, t2, t3, t1)
plt.plot(x_coords, y_coords, "c--", x_coords, y_coords, "co")

plot_vector2d(v, t1, color="r", linestyle=":")
plot_vector2d(v, t2, color="r", linestyle=":")
plot_vector2d(v, t3, color="r", linestyle=":")

t1b = t1 + v
t2b = t2 + v
t3b = t3 + v

x_coords_b, y_coords_b = zip(t1b, t2b, t3b, t1b)
plt.plot(x_coords_b, y_coords_b, "b-", x_coords_b, y_coords_b, "bo")

plt.text(4, 4.2, "v", color="r", fontsize=18)
plt.text(3, 2.3, "v", color="r", fontsize=18)
plt.text(3.5, 0.4, "v", color="r", fontsize=18)

plt.axis([0, 6, 0, 5])
plt.grid()
plt.show()
```


    
![png](output_39_0.png)
    


Finalmente, restar un vector es como sumar el vector opuesto.


```python
plot_vector2d(w, color="r")
plot_vector2d(v, origin=w, color="b", linestyle="dotted")
plot_vector2d(-v, origin=w, color="b", linestyle="dotted")
plot_vector2d(w+v, color="g")
plot_vector2d(w-v, color="g")
plt.axis([0, 8, 0, 4])
plt.text(1.6, 1, "w", color="r", fontsize=18)
plt.text(5, 2.5, "v", color="b", fontsize=18)
plt.text(2, 1.5, "-v", color="b", fontsize=18)
plt.text(4, 1.5, "u+v", color="g", fontsize=18)
plt.text(0.25, 0.5, "u-v", color="g", fontsize=18)
plt.grid()
plt.show()
```


    
![png](output_41_0.png)
    


## Multiplicación por un escalar
Los vectores se pueden multiplicar por escalares. Todos los elementos del vector se multiplican por ese número, por ejemplo:


```python
result = 1.5 * u
print("1.5 *", u, "=", result)
```

    1.5 * [2 5] = [3.  7.5]
    

Gráficamente, la multiplicación por escalar da como resultado cambiar la escala de una figura, de ahí el nombre *escalar*. La distancia desde el origen (el punto en coordenadas iguales a cero) también se multiplica por el escalar. Por ejemplo, ampliemos la escala por un factor de `k = 2.5`:


```python
k = 2.5
t1c = k * t1
t2c = k * t2
t3c = k * t3

plt.plot(x_coords, y_coords, "c--", x_coords, y_coords, "co")

plot_vector2d(t1, color="r")
plot_vector2d(t2, color="r")
plot_vector2d(t3, color="r")

x_coords_c, y_coords_c = zip(t1c, t2c, t3c, t1c)
plt.plot(x_coords_c, y_coords_c, "b-", x_coords_c, y_coords_c, "bo")

plot_vector2d(k * t1, color="b", linestyle=":")
plot_vector2d(k * t2, color="b", linestyle=":")
plot_vector2d(k * t3, color="b", linestyle=":")

plt.axis([0, 9, 0, 9])
plt.grid()
plt.show()
```


    
![png](output_45_0.png)
    


Como puedes suponer, dividir un vector por un escalar es equivalente a multiplicar por su inverso multiplicativo:
$\dfrac{\textbf{u}}{\lambda} = \dfrac{1}{\lambda} \times \textbf{u}$

La multiplicación por escalar es **conmutativa**: $\lambda \times \textbf{u} = \textbf{u} \times \lambda$.

También es **asociativa**: $\lambda_1 \times (\lambda_2 \times \textbf{u}) = (\lambda_1 \times \lambda_2) \times \textbf{u}$.

Finalmente, es **distributiva** sobre la suma de vectores: $\lambda \times (\textbf{u} + \textbf{v}) = \lambda \times \textbf{u} + \lambda \times \textbf{ v}$.

## Vectores nulos, unitarios y normalizados
* Un **vector nulo** es un vector lleno de ceros.
* Un **vector unitario** es un vector con una norma igual a 1.
* El **vector normalizado** de un vector no nulo $\textbf{u}$, anotado $\hat{\textbf{u}}$, es el vector unitario que apunta en la misma dirección que $\textbf{u}$. Es igual a: $\hat{\textbf{u}} = \dfrac{\textbf{u}}{\left \Vert \textbf{u} \right \|}$




```python
plt.gca().add_artist(plt.Circle((0,0),1,color='c'))
plt.plot(0, 0, "ko")
plot_vector2d(v / LA.norm(v), color="k")
plot_vector2d(v, color="b", linestyle=":")
plt.text(0.3, 0.3, "$\hat{u}$", color="k", fontsize=18)
plt.text(1.5, 0.7, "$u$", color="b", fontsize=18)
plt.axis([-1.5, 5.5, -1.5, 3.5])
plt.grid()
plt.show()
```


    
![png](output_49_0.png)
    


## Producto escalar
### Definición
El producto punto (también llamado *producto escalar*) de dos vectores $\textbf{u}$ y $\textbf{v}$ es una operación útil que surge con bastante frecuencia en álgebra lineal. Se anota $\textbf{u} \cdot \textbf{v}$, o a veces $⟨\textbf{u}|\textbf{v}⟩$ o $(\textbf{u}|\textbf{v}) $, y se define como:

$\textbf{u} \cdot \textbf{v} = \left \Vert \textbf{u} \right \| \times \left \Vert \textbf{v} \right \| \times cos(\theta)$

donde $\theta$ es el ángulo entre $\textbf{u}$ y $\textbf{v}$.

Otra forma de calcular el producto escalar es:

$\textbf{u} \cdot \textbf{v} = \sum_i{\textbf{u}_i \times \textbf{v}_i}$

### En python
El producto punto es bastante simple de implementar:


```python
def dot_product(v1, v2):
    return sum(v1i * v2i for v1i, v2i in zip(v1, v2))

dot_product(u, v)
```




    11



Pero NumPy proporciona una implementación *mucho* más eficiente con la función `dot`:


```python
np.dot(u,v)
```




    11



De manera equivalente, puede usar el método `dot` de `ndarray`s:


```python
u.dot(v)
```




    11



**Precaución**: el operador `*` realizará una multiplicación *elemento a elemento*, *NO* un producto escalar:


```python
print("  ",u)
print("* ",v, "(NOT a dot product)")
print("-"*10)

u * v
```

       [2 5]
    *  [3 1] (NOT a dot product)
    ----------
    




    array([6, 5])



### Propiedades principales
* El producto escalar es **conmutativo**: $\textbf{u} \cdot \textbf{v} = \textbf{v} \cdot \textbf{u}$.
* El producto escalar solo se define entre dos vectores, no entre un escalar y un vector. Esto significa que no podemos encadenar productos punto: por ejemplo, la expresión $\textbf{u} \cdot \textbf{v} \cdot \textbf{w}$ no está definida ya que $\textbf{u} \cdot \textbf{ v}$ es un escalar y $\textbf{w}$ es un vector.
* Esto también significa que el producto escalar **NO es asociativo**: $(\textbf{u} \cdot \textbf{v}) \cdot \textbf{w} ≠ \textbf{u} \cdot (\textbf{ v} \cdot \textbf{w})$ ya que ninguno está definido.
* Sin embargo, el producto escalar es **asociativo con respecto a la multiplicación escalar**: $\lambda \times (\textbf{u} \cdot \textbf{v}) = (\lambda \times \textbf{u}) \cdot \textbf{v} = \textbf{u} \cdot (\lambda \times \textbf{v})$
* Finalmente, el producto escalar es **distributivo** sobre la suma de vectores: $\textbf{u} \cdot (\textbf{v} + \textbf{w}) = \textbf{u} \cdot \textbf{v } + \textbf{u} \cdot \textbf{w}$.

### Cálculo del ángulo entre vectores
Uno de los muchos usos del producto escalar es calcular el ángulo entre dos vectores no nulos. Mirando la definición del producto escalar, podemos deducir la siguiente fórmula:

$\theta = \arccos{\left ( \dfrac{\textbf{u} \cdot \textbf{v}}{\left \Vert \textbf{u} \right \| \times \left \Vert \textbf{v } \right \|} \right ) }$

Tenga en cuenta que si $\textbf{u} \cdot \textbf{v} = 0$, se sigue que $\theta = \dfrac{π}{2}$. En otras palabras, si el producto escalar de dos vectores no nulos es cero, significa que son ortogonales.

Usemos esta fórmula para calcular el ángulo entre $\textbf{u}$ y $\textbf{v}$ (en radianes):


```python
def vector_angle(u, v):
    cos_theta = u.dot(v) / LA.norm(u) / LA.norm(v)
    return np.arccos(np.clip(cos_theta, -1, 1))

theta = vector_angle(u, v)
print("Angle =", theta, "radians")
print("      =", theta * 180 / np.pi, "degrees")
```

    Angle = 0.8685393952858895 radians
          = 49.76364169072618 degrees
    

Nota: debido a pequeños errores de coma flotante, `cos_theta` puede estar ligeramente fuera del intervalo $[-1, 1]$, lo que haría que `arccos` fallara. Es por eso que recortamos el valor dentro del rango, usando la función `clip` de NumPy.

### Proyectar un punto sobre un eje
El producto escalar también es muy útil para proyectar puntos en un eje. La proyección del vector $\textbf{v}$ sobre el eje de $\textbf{u}$ viene dada por esta fórmula:

$\textbf{proj}_{\textbf{u}}{\textbf{v}} = \dfrac{\textbf{u} \cdot \textbf{v}}{\left \Vert \textbf{u} \right \| ^2} \times \textbf{u}$

Lo cual es equivalente a:

$\textbf{proj}_{\textbf{u}}{\textbf{v}} = (\textbf{v} \cdot \hat{\textbf{u}}) \times \hat{\textbf{u}}$




```python
u_normalized = u / LA.norm(u)
proj = v.dot(u_normalized) * u_normalized

plot_vector2d(u, color="r")
plot_vector2d(v, color="b")

plot_vector2d(proj, color="k", linestyle=":")
plt.plot(proj[0], proj[1], "ko")

plt.plot([proj[0], v[0]], [proj[1], v[1]], "b:")

plt.text(1, 2, "$proj_u v$", color="k", fontsize=18)
plt.text(1.8, 0.2, "$v$", color="b", fontsize=18)
plt.text(0.8, 3, "$u$", color="r", fontsize=18)

plt.axis([0, 8, 0, 5.5])
plt.grid()
plt.show()
```


    
![png](output_63_0.png)
    


# Ejemplo: Embeddings

###Embedding de personalidad: ¿Cómo somos?

En una escala de 0 a 100, ¿qué tan introvertido/extrovertido eres (donde 0 es el más introvertido y 100 es el más extrovertido)? ¿Alguna vez ha realizado una prueba de personalidad como la prueba de los Cinco Grandes Rasgos de la Personalidad? Si no lo has hecho, estas son pruebas que te hacen una lista de preguntas, y luego te califican en una serie de ejes, siendo la introversión/extraversión uno de ellos.

Imaginemos que Jay obtuvo una puntuación de 38/100 en el rasgo introversión/extraversión. Podemos graficar eso de esta manera:
![](http://jalammar.github.io/images/word2vec/introversion-extraversion-100.png)

Supongamos que, además de ese, también contemplamos otro de los 5 rasgos y que las escalas de 0 a 100 son reemplazadas por una escala de -1 a 1. Así obtendríamos un vector que represente a Jay de la siguiente manera: 

![](http://jalammar.github.io/images/word2vec/two-traits-vector.png)

Ahora podemos decir que este vector representa parcialmente la personalidad de Jay. La utilidad de tal representación viene cuando compararlo con otras dos personas. Digamos que lo atropella un autobús y necesita ser reemplazado por alguien con una personalidad similar. En la siguiente figura, ¿cuál de las dos personas se parece más a Jay?

![](http://jalammar.github.io/images/word2vec/personality-two-persons.png)

Podemos ver que la persona n° 1 es más parecida a Jay porque gráficamente su vector está más "cerca" al de Jay. Ahora supongamos que tenemos un vector con los 5 rasgos... el análisis gráfico no es una opción. Sin embargo, podemos calcular la similaridad a través del ángulo entre los vectores (que se calcula utilizando el coseno como ya vimos) para obtener una métrica que facilite la comparación.

![](http://jalammar.github.io/images/word2vec/embeddings-cosine-personality.png)

Seguimos viendo que la persona más parecida es la n°1, pero ahora tenemos una métrica para saber cuán mejor reemplazo es con respecto a la otra persona. En los ejercicios asociados a esta clase se puede jugar con un dataset que contiene los vectores asociados a personas reales para ver la utilidad práctica de este concepto.



###Embedding de palabras: ¿Cómo codificamos el significado?

Para que las palabras sean procesadas por modelos de aprendizaje automático, necesitan alguna forma de representación numérica que los modelos puedan usar en sus cálculos. Ahora que entendemos el poder de representación de los vectores, podemos proceder a observar ejemplos de vectores de palabras entrenados (también llamados embeddings de palabras) y comenzar a observar algunas de sus propiedades interesantes.

Word2Vec fue el primer algoritmo en demostrar que podemos usar un vector para representar correctamente las palabras de una manera que capturara las relaciones semánticas o de significado. Por ejemplo, al analizar estos vectores podemos saber si las palabras son similares u opuestas (analizando la dirección y el sentido del vector), o que un par de palabras como “Estocolmo” y “Suecia” tienen entre ellas la misma relación que tienen “El Cairo” y “Egipto” (analizando las distancias entre los vectores), o también relaciones sintácticas o basadas en la gramática (por ejemplo, la relación entre “tenía” y “tengo” es la misma que entre “era” y “es”).

Este es un embedding para la palabra "rey" (vector GloVe entrenado en Wikipedia):

$$[ 0.50451 , 0.68607 , -0.59517 , -0.022801, 0.60046 , -0.13498 , -0.08813 , 0.47377 , -0.61798 , -0.31012 , -0.076666, 1.493 , -0.034189, -0.98173 , 0.68229 , 0.81722 , -0.51874 , -0.31503 , -0.55809 , 0.66421 , 0.1961 , -0.13495 , -0.11476 , -0.30344 , 0.41177 , -2.223 , -1.0756 , -1.0783 , -0.34354 , 0.33505 , 1.9927 , -0.04234 , -0.64319 , 0.71125 , 0.49159 , 0.16754 , 0.34344 , -0.25663 , -0.8523 , 0.1661 , 0.40102 , 1.1685 , -1.0137 , -0.21585 , -0.15155 , 0.78321 , -0.91241 , -1.6106 , -0.64426 , -0.51042 ] $$



Es una lista de 50 números. No podemos decir mucho mirando los valores. Pero visualicémoslo un poco para poder compararlo con otros vectores de palabras. Pongamos todos estos números en una fila y codifiquemos por colores las celdas según sus valores (rojo si están cerca de 2, blanco si están cerca de 0, azul si están cerca de -2):

![](http://jalammar.github.io/images/word2vec/king-colored-embedding.png)

Procederemos ignorando los números y solo observando los colores para indicar los valores de las celdas. Ahora comparemos "Rey" con otras palabras:

![imagen.png](data:image/png;base64,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)

Algunas cosas para señalar:

* Hay una columna roja recta a través de todas estas palabras diferentes. Son similares a lo largo de esa dimensión (y no sabemos qué codifica cada dimensión)
* Puedes ver cómo "mujer" y "niña" son similares entre sí en muchos lugares. Lo mismo con "hombre" y "niño"
* “niño” y “niña” también tienen lugares donde son similares entre sí, pero diferentes de “mujer” u “hombre”. ¿Podrían estar codificando una vaga concepción de la juventud?
* Todas menos la última palabra son palabras que representan personas. Podemos, por ejemplo, ver que la columna azul va hacia abajo y se detiene antes del embedding de "agua".
* Hay lugares claros donde "rey" y "reina" son similares entre sí y distintos de todos los demás. ¿Podrían estar codificando un concepto vago de realeza?



Otro ejemplo más que prueba lo poderosos que son estos embeddings es el concepto de las analogías. Podemos sumar y restar embeddings de palabras y llegar a resultados interesantes. El ejemplo más famoso es la fórmula: "rey" - "hombre" + "mujer":

![](http://jalammar.github.io/images/word2vec/king-analogy-viz.png)

El vector resultante de "rey-hombre+mujer" no es exactamente igual a "reina", pero "reina" es la palabra más cercana de los 400 000 embeddings de palabras que tenemos en esta colección.

Algo importante que debe quedar claro es que, en contraste con los embeddings de personalidad que analizamos anteriormente, ***no sabemos que codifica cada dimensión del vector***. Podemos hacer conjeturas y experimentos que nos permitan validar que estos vectores están modelando de alguna u otra forma la semántica, pero esta codificación de los datos es la que a la red le pareció la más eficiente durante el entrenamiento. Para mayor información sobre los embeddings pueden consultar [este artículo](http://jalammar.github.io/illustrated-word2vec/) en el cual estuvo basado esta sección de la clase, o también asistir al curso de NLP de humai donde estaremos explicando estos temas con mayor detalle.

# Ejemplo: Regresión Lineal Simple

La regresión lineal simple permite definir un modelo de recta que mejor se ajusta a una nube de puntos dada. 

![](http://prepa8.unam.mx/academia/colegios/matematicas/paginacolmate/applets/eyp/Applets_Geogebra/rectamincuad_i_archivos/image003.jpg)

Es decir, dada una serie de observaciones de una variable independiente $x$ podemos encontrar una función lineal (una recta) para encontrar el valor de una variable dependiente $y$.

$$ y = \beta_0 + \beta_1 x + e$$

donde $\beta_0$ es la ordenada al origen de la recta, $\beta_1$ es la pendiente de la recta y $e$ es la distancia del punto a la recta.

El error de nuestro modelo está dado por el valor $e$ que es la diferencia entre el valor observado o real de la variable dependiente ($y$) y el valor predicho por la recta estimada ($\hat{y}$). Por lo tanto:

$$ \hat{y} = \beta_0 + \beta_1 x$$

$$ e = y - \hat{y} $$





Supongamos que tenemos $n$ observaciones para las variables $x$ e $y$ y para cada observación queremos calcular con nuestro modelo una predicción del valor de la variable dependiente $\hat{y}$. Nos conviene replantear las variables y las predicciones como vectores de la siguiente manera.

$$ \boldsymbol{x} = [x_1, x_2,...,x_n]$$
$$ \boldsymbol{y} = [y_1,y_2,...,y_n]$$
$$ \boldsymbol{\hat{y}} = [\hat{y}_1,\hat{y}_2,...,\hat{y}_n]$$

Y luego reformular las fórmulas anteriores usando operaciones entre vectores.

$$ \boldsymbol{\beta_0} = [\beta_0,  \beta_0, ..., \beta_0]$$
$$ \boldsymbol{\hat{y}} = \boldsymbol{\beta_0} + \beta_1 x$$




Los valores de las variables $\boldsymbol{x}$  e $\boldsymbol{y}$ ya los tenemos en nuestra nube de puntos para la que queremos calcular la recta. Lo que variará en la ecuación de la recta que seleccionemos serán los coeficientes del modelo, $\beta_0$ y $\beta_1$ . \
¿Y qué coeficientes nos interesan? Lógicamente, aquellos con los que el el error sea lo menor posible. Dicho de otra forma, queremos la ecuación con un valor de la suma de residuos lo más bajo posible.

Sin embargo, el error $e$ debe ser reformulado ya que ahora tanto $\boldsymbol{\hat{y}}$ como $\boldsymbol{y}$ son vectores.

$$ \boldsymbol{e} = \boldsymbol{y}-\boldsymbol{\hat{y}}$$
$$ e = \sum_{i=1}^{n}\boldsymbol{e}_{i}$$

Ademas este error $e$ tiene otro problema y es que en ocasiones $\boldsymbol{e}_{i}$ será positivo (cuando $y$ sea mayor que $ \hat{y}$) y en otras será negativo (cuando $ \hat{y}$ sea mayor que $y$). Por lo tanto, elevaremos cada resta al cuadrado para eliminar el problema del signo o, lo que es equivalente.

$$ \boldsymbol{e} = (\boldsymbol{y}-\boldsymbol{\hat{y}})$$
$$ e = \sum_{i=1}^{m}\boldsymbol{e}_{i}^2$$

Algo equivalente es hacer el producto punto del vector $e$ consigo mismo.

$$e=\boldsymbol{e} \cdot \boldsymbol{e}$$


Al definir el error como la suma de los cuadrados de las diferencias entre los valores observados y predichos, el problema de encontrar los $\beta_0$ y $\beta_1$ óptimos se transforma en encontrar los **"mínimos cuadrados"**. Estos $\beta_0$ y $\beta_1$  óptimos se pueden encontrar utilizando derivadas que es un concepto que veremos dentro de algunas clases. Lo importante es que la fórmula para encontrarlos es la siguiente: 

$$\beta_1 = \frac{\sum_{i=1}^{n}(x_i-\bar{x})(y_i-\bar{y})}{\sum_{i=1}^{n}(x_i-\bar{x})^2}$$

$$\beta_0 = \bar{y} - \beta_1\bar{x}$$

La fórmula de $\beta_1$ puede parecer algo compleja, pero si la analizamos en detalle podemos convertirla en productos escalares ya que son sumas de productos indexados.

$$\boldsymbol{\bar{x}} = [\bar{x},\bar{x},...,\bar{x}]$$
$$\boldsymbol{\bar{y}} = [\bar{y},\bar{y},...,\bar{y}]$$
$$\beta_1 = \frac{(\boldsymbol{x}-\boldsymbol{\bar{x}})\cdot(\boldsymbol{y}-\boldsymbol{\bar{y}})}{(\boldsymbol{x}-\boldsymbol{\bar{x}})\cdot(\boldsymbol{x}-\boldsymbol{\bar{x}})}$$

$$\beta_0 = \bar{y} - \beta_1\bar{x}$$

### Práctica

Supongamos que tenemos la siguiente nube de puntos


```python
x = np.array([180, 157, 162,167,178,178,182,188])
y = np.array([56,61,67,72,70,72,83,92])
f, ax = plt.subplots(1)
ax.scatter(x, y)
ax.set_xlim(xmin=140, xmax=200)
ax.set_ylim(ymin=40, ymax=100)
plt.show(f)
```


    
![png](output_83_0.png)
    


Programemos las fórmulas de la regresión lineal y grafiquemos la recta encontrada.


```python
#recordá que el broadcasting se activa cuando operamos un vector con un escalar
#operando el escalar con cada elemento del vector
b1_num = (x - x.mean()).dot(y - y.mean())
b1_den = (x - x.mean()).dot(x - x.mean())
b1 = b1_num/b1_den
b0 = y.mean() - b1*x.mean()
y_hat = b0 + b1*x #nuestra predicción

#Graficamos
f, ax = plt.subplots(1)
ax.scatter(x, y)
ax.plot(x, y_hat, 'go--', linewidth=2)
ax.set_xlim(xmin=140, xmax=200)
ax.set_ylim(ymin=40, ymax=100)
plt.show(f)
```


    
![png](output_85_0.png)
    



```python
e_vec = y - y_hat
e = np.dot(e_vec,e_vec)
e
```




    603.5033950617287






___

%%
tags:  #programación #pagmatpython #python  #numpy #vectores #matplotlib #adición #norma #módulo

Vínculos:   [[000-Menú Geometría📃|Menú Geometría analítica📃]], [[030-Transformaciones, congruencia y semejanza|Transformaciones, congruencia y semejanza]] , [[000-Menú Matemáticas Python 📃|Menú Matemáticas en python📃]]
%%