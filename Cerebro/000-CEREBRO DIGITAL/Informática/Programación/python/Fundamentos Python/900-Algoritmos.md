---
ID:: 900
tags:: #programación #pagfundamentospython #python 
nombre:: "Algoritmos"
---
___
# Algoritmos
___
## 1- 100 tiradas de dado
Usando np.random.randint() guardar 100 tiradas de un dado en una lista
```python
import numpy as np
```

```python
tiradas = []
```

- **Forma 1**
```python
for x in range(0,100):
    tiradas.append(np.random.randint(1,7))
    
print(tiradas)
```

- **Forma 2**
```python
print([np.random.randint(1,7) for x in range(0,100)])
```

$$Resultado$$
![[Pasted image 20230817193107.png]]

#numpy #randint #np #dados

___
## 2- Buscar edad

Para cada paciente
- Buscar su edad en el diccionario
- Agregar la edad a edades
- Usar for
- indexar el diccionario
- agregar con .append()


Creamos las variables:
```python
pacientes = ["Pedro","Martin","Sofia"]
edades = []
nombres_edades = {
    "Pedro":20,
    "Martin":24,
    "Sofia":32,
    "Jaimito":19
}
```

Forma 1 :
```python
for x in nombres_edades.keys():
    if x in pacientes:
        edades.append(nombres_edades[x])
```

Forma 2:
```python
for p in pacientes:
    edad = nombres_edades[p]
    edades.append(edad)
```

```python
print(edades)
```
$$Resultado$$
![[Pasted image 20230817183601.png]]

#append #keys #diccionario #buscar_edad

___
## 3-Palíndromo
![](https://www.youtube.com/watch?v=gPN294xBbdc)
Un palíndromo es una palabra o frase que se lee de igual manera en ambos sentidos. Por ejemplo, Ana. Otro ejemplo es un expresidente argentino de la década del 90.

Hay distintas formas de resolver este problema, vamos a ver primero dos formas que hacen uso de la versatilidad de Python y luego una manera algo más compleja pero que nos va a permitir pensar el problema desde otra óptica.

---

Vamos a definir tres funciones llamadas es_palindromo y para testear su funcionamiento vamos a chequear que:

1- es_palindromo("ana") == True

2- es_palindromo("barrilete cósmico") != True

3- es_palindromo("yo hago yoga hoy") == True

4- es_palindromo("arriba la birra") == True

5- es_palindromo("arriba la barra") != True

```python
texto_1 = "ana"
texto_2 = "barrilete cosmico"
texto_3 = "yo hago yoga hoy"
texto_4 = "arriba la birra"
texto_5 = "arriba la barra"
```

### Slicing
1- Una manera de resolver el problema es recordar que un string es un iterable y que, por lo tanto, lo podemos recorrer en sentido inverso. De esta manera podemos tener un código compacto.
```python
# Recordemos el slicing:
texto_1[::-1]
```
$$Consola$$
![[Pasted image 20230818095938.png]]

```python
# ¿Qué pasa en este ejemplo?
texto_3[::-1]
```
$$Consola$$
![[Pasted image 20230818100010.png]]

___

### Replace
En los palíndromos (al menos acá) nos interesa el sonido, con lo cual vamos a _omitir los espacios_ en el análisis.
```python
# Opción 1: usar slicing
def es_palindromo(texto):
    texto = texto.replace(" ", "")
    # vean cómo podemos hacer slicing por un string, en sentido inverso, recorriendo la lista de atrás para adelante.
    return texto == texto[::-1]
```

### Assert 

```python
# assert nos permite controlar que una condición se cumpla, si no da True devuelve un AssertionError con el mensaje de la derecha
assert es_palindromo(texto_1) == True, "falló el test"
assert es_palindromo(texto_2) != True, "falló el test"
assert es_palindromo(texto_3) == True, "falló el test"
assert es_palindromo(texto_4) == True, "falló el test"
assert es_palindromo(texto_5) != True, "falló el test"
```

### Reversed
Python cuenta con una serie de funciones built-in entre las cuales se encuentra **reversed**. Esta función devuelve un iterable con el input (que puede ser cualquier secuencia) con su orden reverso.

```python
def es_palindromo(texto):
	texto = texto.replace(" ", "")
	return texto == "".join(reversed(texto))
```

#reversed #assert #replace #slicing #palindromo

___

## 4- Secuencia de Fibonacci
![](https://youtu.be/gPN294xBbdc?t=653)

La secuencia de Fibonacci es la famosa secuencia que se define como:

$$F_{0}=0$$
$$F_{1}=1$$
$$F_{n}=F_{n-1}+F_{n-2} \quad \text{para} \quad n>1$$

![[Pasted image 20230818110355.png|600]]

Esto nos da como resultado:

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

Ahora bien, ¿Cómo podemos programar un algoritmo que compute esta serie hasta el número de Fibonacci en la posición n? Noten, que para obtener el número de Fibonacci _n_ debemos antes computar el n-1 y el n-2, es decir, para tener un valor de la secuencia de Fibonacci debemos computar los previos. Cuando una función requiere llamarse a sí misma para poder realizar un cómputo decimos que la función es _recursiva_.

Entonces, tratemos de encarar el problema "traduciendo" la definición de la secuencia a código Python...

### Función de Fibonacci

```python
# Opción 1: solución recursiva.
def F_n(n):
    # sigamos la definición de la secuencia de Fibonacci
    if n == 0: # Si n es 0 entonces devuelvo 0
        return 0
    if n == 1:
        return 1 # Si n es 1 entonces devuelvo 1
    else:
        return F_n(n-1) + F_n(n-2) # En cualquier otro caso devuelvo la suma de los dos números de Fibonacci preivos
```

La recursividad es esta propiedad por la cual una función se llama a sí misma. Toda función recursiva necesita tener un punto de corte, para ponerle un fin a esta llamada. De lo contrario vamos a tener un error.

---

Más adelante vamos a ejecutar varias veces la función F_n, generando la lista de valores de Fibonacci... ¿Qué creen que va a pasar?

---

Pero antes, vamos a charlar un poco más sobre recursividad. Como dijimos, se necesita un punto de corte, de lo contrario veamos qué pasa...

```python
def F_n_2(n): # borro las condiciones
    return F_n_2(n-1) + F_n_2(n-2)
```

Ejecuten la siguiente celda y vean que vamos a obtener el error:
**RecursionError**: maximum recursion depth exceeded

```python
---------------------------------------------------------------------------
RecursionError                            Traceback (most recent call last)
<ipython-input-23-48749e03940f> in <module>
----> 1 F_n_2(5)
---
1 frames
---
... last 1 frames repeated, from the frame below ...
<ipython-input-22-92343644e179> in F_n_2(n)
      1 def F_n_2(n): # borro las condiciones
----> 2     return F_n_2(n-1) + F_n_2(n-2)
RecursionError: maximum recursion depth exceeded
```

Ahora sí, vamos a generar la serie de Fibonacci
```python
[F_n(i) for i in range(10)]
```
$$Consola$$
![[Pasted image 20230818103632.png]]

#### Comprobación del tiempo de ejecución de Fibonacci

```python
%timeit [F_n(i) for i in range(10)]
```
$$Consola$$
![[Pasted image 20230818103949.png]]

```python
%timeit [F_n(i) for i in range(33)]
```
$$Consola$$
![[Pasted image 20230818104153.png]]

¿Qué notan o qué opinan de la solución recursiva? ¿Qué creen que necesitamos hacer para resolver este problema?

### Fibonacci con While
```python
# Opción 2: armamos loop while que va a iterar n veces, donde n es la cantidad de elementos de la secuencia
def fibo(n):
    """
    Inicializo a y b. En este caso "a" sería F_n-2 (F_0 al inicializarse)
    y "b" F_n-1 (F_1 al inicializarse)
    """
    a, b = 0, 1
    secuencia = [a, b]
    if n == 0:
        return a
    elif n == 1:
        return b
    n_actual = 2 # número de iteración
    while n_actual < n:
        n_actual += 1 # sumo 1 a la iteración actual
        a, b = b, a + b # Este truquito es importante!
        secuencia.append(b) # guardo el nuevo b
    return secuencia
```

```python
fibo(10)
```
$$Consola$$
![[Pasted image 20230818105057.png]]

#### Comprobación del tiempo de ejecución de Fibonacci

```python
%timeit fibo(10)
```
$$Consola$$
![[Pasted image 20230818105248.png]]

```python
%timeit fibo(33)
```
$$Consola$$
![[Pasted image 20230818105330.png]]



#timeit #fibonacci #while #recursividad #recursión #comando_mágico #sin_variable_auxiliar

___

## 5- Merge sorted array
![](https://youtu.be/gPN294xBbdc?t=1275)

___

Este algoritmo consiste en combinar dos listas ordenadas en una tercera lista, también ordenada.

La forma más eficiente de resolver este problema, es ir eliminando los elementos más chicos y guardándolos en una variable de resultado. Mientras recorremos los elementos y los vamos removiendo de la lista se pueden dar 3 situaciones:

- Que las dos listas tengan elementos, en cuyo caso hay que elegir el menor.
- Que sólo la primera lista tenga elementos, en cuyo caso hay que elegir el menor de la primera lista.
- Que sólo la segunda lista tenga elementos, en cuyo caso hay que elegir el menor de la segunda lista.

Como las listas vinieron ordenadas, elegir el menor es fácil. Alcanza con consultar la posición con el índice 0. Para leer y a continuación eliminar el primer elemento de cada lista, vamos a usar el método pop con el índice 0.

### pop
```python
# Ejemplo de uso de pop
a = [2,9]
a.pop(0)
```
$$Consola$$
![[Pasted image 20230819181344.png]]
```python
# El método pop() devolvió el valor de la posición 0 y continuación lo borró de la lista
a
```
$$Consola$$
![[Pasted image 20230819181433.png]]


```python
a.pop(0)
```
$$Consola$$
![[Pasted image 20230819181540.png]]

```python
# Después de invocar 2 veces el método pop(), la lista a queda vacía.
a
```
$$Consola$$
![[Pasted image 20230819181616.png]]

### Combinar Listas vacías
Ahora resolvamos el problema de combinar listas ordenadas:

```python
def merge_sorted(lista_1,lista_2):
    resultado = []
    while len(lista_1) > 0 or len(lista_2) > 0: # mientras alguna lista tenga valores
        # Vamos a recorrer las listas hasta que no queden más elementos en ninguna.
        if len(lista_1) > 0: # si la primera lista tiene valores
            if len(lista_2) > 0:
                # Este es el caso donde quedan elementos en las dos listas.
                # Aquí elegimos el menor de los primeros elementos
                if lista_1[0] <= lista_2[0]:
                    resultado.append(lista_1.pop(0))
                else:
                    resultado.append(lista_2.pop(0))
            else:
                # Este es el caso donde lista_1 todavía tiene elementos pero lista_2 no
                resultado.append(lista_1.pop(0))
        else:
            # Si no quedan elementos en la lista_1 pero seguimos dentro del while loop,
            # es porque quedan elementos en la lista2
            resultado.append(lista_2.pop(0))
    return resultado
```

```python
lista1 = [0,3,5,8,9]
lista2 = [4,5,6]
```

```python
merge_sorted(lista1,lista2)
```
$$Consola$$
![[Pasted image 20230819182044.png]]

#pop #append #combinar_listas

___

## 6- Ordenando listas
![](https://youtu.be/gPN294xBbdc?t=1789)

___
En el caso anterior vimos cómo juntar dos listas ordenadas. Ahora, vamos a ver cómo ordenar una lista. Para eso hay muchos algoritmos:

```
- Selection Sort (Fuerza Bruta)
- Bubble Sort
- Merge Sort
- Quicksort
- Timsort
- Insertion Sort
```

Hay lindas animaciones que nos muestran como funcionan: 
![](https://www.youtube.com/watch?v=ZZuD6iUe3Pc)

Cada una de ellas elige distintos enfoques para ordenar la lista con diferentes técnicas algorítmicas (iterativas o recursivas). Eso logra que cada uno de ellos tenga distintas complejidades algorítmicas y sean mas rápidos unos que otros.

### Selection sort
Vamos empezar programando la estrategia del `Selection Sort`, la misma consta de una técnica de fuerza bruta que lo que hace es ir recorriendo la lista buscando el mínimo elemento en cada paso e ir guardándolo en una nueva lista ordena. Los pasos serían:

1- Empezar a recorrer la lista hasta quedarme con el valor mínimo.

2- Guardar ese mínimo en una nueva lista ordenada y sacarlo de la lista original (lista modificada).

3- Volver a realizar el primer y segundo paso sobre la lista sin ese valor (la lista modificada).

```python
def selection_sort(lista):
    # Inicializamos una lista_ordenada donde iremos poniendo los elementos ordenados
    n = len(lista)
    lista_ordenada = []

    # Vamos a recorrer la lista, puede ser útil saber la longitud
    while len(lista_ordenada) < n:
        # Necesitamos un valor para comenzar a comparar
        minimo = lista[0]
        indice_minimo = 0
        # Empezamos a recorrer la lista
        for (i,elemento) in enumerate(lista):
            # Vamos a comparar cada uno con el mínimo, si es menor, tenemos nuevo mínimo!
            if elemento < minimo :
              minimo = elemento
              indice_minimo = i
        # Agregamos el mínimo y lo sacamos de la lista
        lista_ordenada.append(minimo)
        lista.pop(indice_minimo)
        
    return lista_ordenada
```

```python
lista_1 = [1,3,5,1,32,9,0,-1]
```

```python
selection_sort(lista_1)
```
$$Consola$$
![[Pasted image 20230819190334.png]]

¿Porqué usamos un While? ¿Se podría cambiar por un For? ¡Sí! Y también podemos agregarle un parámetro booleano que nos permita elegir si lo queremos en orden ascendiente o descendiente. Observen que paso con la lista original:

```python
lista_1
```
$$Consola$$
![[Pasted image 20230819190455.png]]

Desapareció! Esto es porque las modificaciones las hicimos sobre la misma lista. Si no queremos perderla vamos a necesitar crear una copia nueva y para eso podemos hacerlo usando el método `copy()`.
___

### Bubble sort

Veamos un ejemplo con otro enfoque, vamos a programar el Bubble Sort... ¡y me van a ayudar ustedes! Tomamos la imagen y nos inspiramos de este blog (donde pueden encontrar otros algoritmos): [https://realpython.com/sorting-algorithms-python/#the-insertion-sort-algorithm-in-python](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Frealpython.com%2Fsorting-algorithms-python%2F%23the-insertion-sort-algorithm-in-python) 

La idea del algoritmo es la siguiente... vamos a hacer una recorrida por la lista de izquierda a derecha y comparar un par de valores adyacentes, por ejemplo, el primero contra el segundo, si el primero es mayor al segundo los damos vuelta, y si no no hacemos nada. Luego, tomamos el valor en la segunda posición y el valor en la tercera posición y los comparamos... así sucesivamente hasta el final. Al cabo de la primera "pasada" el valor más alto va a estar a la derecha de todo. Luego, empezamos otra vez desde el comienzo. Sin embargo, como ya acomodamos el valor más alto podemos frenar una posición antes. Y así, damos tantas pasadas sobre la lista como sea necesario hasta que no haya ni un cambio de lugar en toda la recorrida.

Veamos qué pasa con el 8 en la imagen de abajo... Primero comparamos el 8 con el 2, como el 8 es mayor los cambiamos de lugar. Ahora comparamos el valor en la 2da posición (que es el 8, no el 2, porque los dimos vuelta) y en la 3era posición, como el 8 es mayor al 6 los cambiamos de lugar, y así hasta el final. Como el 8 es el valor más alto termina a la derecha del todo. En la siguiente pasada no va a ser necesario volver a chequear contra este valor.

Entonces, pensemos qué vamos a necesitar:

1- Por un lado necesitamos saber en qué iteración nos encontramos. Como máximo vamos a hacer tantas pasadas como el largo de la lista. Vamos a hacer un loop desde el comienzo hasta el último elemento.

2- Por otra parte, necesitamos saber si en esta "pasada" ya modificamos algún lugar o no, para saber cuándo frenar el algoritmo.

3- Vamos a iterar desde el primer valor hasta el último que corresponde a esta iteración (recuerden que en cada iteración ya ordenamos el valor más alto). Para esto vamos a usar el índice que nos da el loop del punto 1.

4- Un punto de corte, cuando en una 'pasada' no haya cambio o ya no queden 'pasadas'.

![[python-sorting-algorithms-bubble-sort.webp|300]]

```python
def bubble_sort(lista):

    # n igual al largo de la lista
    n = len(lista)
    # Vamos a realizar una 'pasada' por cada elemento que tenemos en la lista.
    for i in range(n):
        # Creamos una variable que sirve como 'flag' para indicar si tuvimos que ordenar o no en la pasada actual
        # Esto lo podemos usar para terminar el algoritmo antes, ya que si no tuvimos que cambiar nada
        # en una pasada, tampoco lo vamos a tener que hacer en la siguiente
        ordenado = True
        # Vamos a comenzar recorriendo la lista de IZQUIERDA a DERECHA pero no hasta el final
        # Recordemos que con cada 'pasada' vamos a haber encontrado el valor más alto aún sin ordenar
        # Con lo cual, vamos a recorrer la lista desde el comienzo hasta el final menos los valores que ya ordenamos antes
        # Tip: recuerden que el índice de una lista tiene como máximo el valor de la longitud - 1 porque arranca en 0
        for j in range(n-i-1): # argumento de la función range()
  
            if lista[j] > lista[j+1]: # si el valor de la IZQUIERDA es mayor al de la derecha
                # Si es mayor, entonces vamos a intercambiar la posición del valor de la derecha con el de la izquierda
                # cambiar el valor de la izquierda por el de la derecha
                lista[j], lista[j+1] = lista[j+1], lista[j]
                # Como tuvimos que ordenar un par de elementos entonces tenemos que cambiar el flag
                # cambiar ordenado a False
                ordenado = False

        # Si no tuvimos que ordenar, salimos del loop
        if ordenado:
            # frenar loop
            break

    return lista
```

```python
lista_1 = [1,3,5,1,32,9,0,-1]
```

```python
bubble_sort(lista_1)
```
$$Consola$$
![[Pasted image 20230819192228.png]]

#bubble_sort #sort #selection_sort #ordenar_listas #merge_sort #quicksort #timsort #insertion_sort

___
Probemos cual es más rápido! ¿Cuál creen?
```python
lista_1 = [1,3,5,1,32,9,0,-1]
```

```python
%timeit selection_sort(lista_1)
```
$$Consola$$
![[Pasted image 20230819192349.png]]

```python
%timeit bubble_sort(lista_1)
```
$$Consola$$
![[Pasted image 20230819192358.png]]

#timeit
___
## 7-Experimento sencillo de tiempo de reacción
![](https://youtu.be/8Sm7ipi8C8M?t=4272)

___
Crear una función tomar_experimento que ejecute una prueba de tiempo de reacción. Para esto, recibe como argumento "rango_pausa", que es el rango de segundos máximo que puede demorar entre un estímulo y el siguiente.

Usando:
  - La función **time.time()** para devolver el tiempo en segundos
  - La función **random.random()** para generar un número aleatorio entre 0 y 1 y variar el tiempo de pausa.
  - La función **time.sleep(s)** para hacer una pausa de s segundos.
  - Y la función **input()** para aguardar una entrada del usuario, bloqueando la ejecución hasta que ingrese la tecla ENTER.

Pasos Pseudocódigo:
- Para cada trial en n trial:
    - prender cronometro
    - decirle al usuario que aprete ENTER
    - medir cuanto tiempo tardó
    - esperar un tiempo aleatorio
    - guardar el tiempo en una lista

```python
import time
import random

n_trials = 4
tiempo_max = 5
datos = []

for n in range(n_trials):
    #Tomamos tiempo inicial
    t0=time.time()
    #Mostramos estímulo y esperamos respuesta
    input("Acepta ENTER")
    #Tomamos tiempo final
    t1=time.time()
    #Tomamos tiempo demorado total en segundos
    tiempo_demorado = t1-t0
    #Agregamos tiempo que se tardó a la lista datos
    datos.append(tiempo_demorado)
    #Definimos el tiempo (en segundos) a esperar
    tiempo_a_esperar = random.random() * tiempo_max
    #Pausamos durante ese tiempo
    time.sleep(tiempo_a_esperar)

print(datos)
```
$$Consola$$
![[Pasted image 20230822080625.png]]

#tiempo_reacción #sleep #espera #time #random #input #demora
___
## 8- Experimento avanzado tiempo de reacción ,análisis de datos , clases, docx, etc
![](https://www.youtube.com/watch?v=31fjtQqmuIc&list=PLISuMnTdVU-xW46IijNsPg8ljPfz-1s7F&index=5)

En esta clase vamos a utilizar un diseño de POO para crear una batería de experimentos:

- Tiempo de Reacción
- Cuestionario

Para eso, tendremos una clase Sujeto que contendrá un id de sujeto, una clase abstracta **Experimento** de la cual heredarán las de **Tiempo de Reacción** y **Cuestionario**, y una clase para generar un **Reporte** de los resultados automáticamente.

Instalamos la librería necesaria para poder manipular archivos de Word:
```python
!pip install python-docx
```

Empezamos creando una clase para definir el _sujeto_ del experimento.

```python
class Sujeto():
    '''Clase para un Sujeto experimental.
    info contiene datos por ejemplo sociodemográficos previos
    en resultados guardaremos los resultados de las pruebas'''
    def __init__(self, sujeto_id, info: dict):
        self.id = sujeto_id
        self.info = info
        self.resultados = dict()
    def __repr__(self):
        # Funcion mágica para mostrar los datos del sujeto
        # el :<20 hace un relleno de máximo 20 espacios
        s = f'Datos de ID {self.id:<20}\n\n'
        for k, v in self.info.items():
            s += f"{k:<20} {v:<20}\n"
        for k, v in self.resultados.items():
            s += f"{k:<20} {v:<20}\n"
        return s
```

_**\_\_repr\_\_**_ sirve como el toString en JAVA
Con _**:<20**_ indicamos que el bloque de texto va a ocupar 20 espacios

Veamos como funciona nuestra clase.

```python
# Instanciamos
info = {'edad':22, 'fecha_nacimiento':'01-01-1998', 'años_educacion':6}
sujeto = Sujeto('123456789', info)
```

```python
print(sujeto)
```
$$Consola$$
![[Pasted image 20230825102211.png]]

Una vez que ya contamos con sujeto. Definimos una clase para la realización del experimento.

La clase tendrá tres métodos:

> - **instrucción**: dará una pauta sobre como realizar el experimento.
> - **corregir_datos**: toma los datos crudos y calcula un resultado
> - **tomar_experimento**: realizará el experimento.

```python
class Experimento():
    def __init__(self, sujeto: Sujeto, consigna='atencion!', nombre='Experimento'):
        self.nombre = nombre
        self.sujeto = sujeto
        self.consigna = consigna
        self.datos = []
    def instruccion(self):
        print(self.consigna)
    def corregir_datos(self):
        pass
    def tomar_experimento(self):
        pass
```

```python
exp = Experimento(sujeto)
```

```python
exp.nombre
```
$$Consola$$
![[Pasted image 20230825102456.png]]


### Tiempo de Reacción

---

Para tomar el experimento se utilizarán dos modulos/librerias: **time** y **random**.

> - **time**, nos va a ayudar a calcular el tiempo durante nuestro experimento.
> - **random**, nos va a permitir generar números aleatorios.

#### Ejercicio:

Crear una función _tomar_experimento_ que ejecute una prueba de tiempo de reacción. Para esto, recibe como argumento "rango_pausa", que es el rango de segundos máximo que puede demorar entre un estímulo y el siguiente.

Usando:

- La función **time.time()** para devolver el tiempo actual en segundos
- La función **random.random()** para generar un número aleatorio entre 0 y 1 y variar el tiempo de pausa
- La función **time.sleep(s)** para hacer una pausa de _s_ segundos
- Y la función **input()** que aguarda una entrada del usuario, bloqueando la ejecución hasta que ingresa la tecla _ENTER_.

---

Pista en pseudocódigo:

```
Dado un entero "n_trials"
Hacer "n_trials" veces:  
	Tomar un tiempo 0  
	Aguardar input  
	Tomar un tiempo 1  
	Calcular diferencia entre tiempos  
	Agregar diferencia a la lista  
	Hacer una pausa random de tiempo
```

```python
import time
import random
```

```python
def tomar_experimento(n_trials, rango_pausa=10):
    datos = []
    for n in range(n_trials):
	    t0 = time.time()
	    pausa = random.random() * rango_pausa
	    time.sleep(pausa)
	    print("Apreta ENTER!")
	    input()
	    t1 = time.time() - t0 - pausa
	    datos.append(t1)
```

```python
tomar_experimento(3, 2)
```
$$Consola$$
![[Pasted image 20230825105654.png]]



Creamos una clase que tendrá la función anterior como un método y además otras funciones como el promedio , la varianza y una funcion para agregar estos datos al diccionario que teníamos vacío en la clase experimento.
```python
class TiempoDeReaccion(Experimento):
    '''Hereda la clase Experimento'''
    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
    def corregir_datos(self):
        mu = sum(self.datos) / len(self.datos)
        var = sum([(x - mu)**2 for x in self.datos]) / len(self.datos)
        self.sujeto.resultados['MediaReaccion'] = mu
        self.sujeto.resultados['VarianzaReaccion'] = var
    # COMPLETAR
    # Usar la función tomar_experimento, esta vez con self en los argumentos
    # y guardar el resultado en self.datos
    # Al final del experimento, llamar a la función "corregir_datos"
    def tomar_experimento(self, n_trials, rango_pausa=10):
        for n in range(n_trials):
	        t0 = time.time()                        #Tiempo inicial
	        pausa = random.random() * rango_pausa   #Rango de pausa
	        time.sleep(pausa)                       #Esperar tiempo aleatorio
	        self.instruccion()                      #Repetir consigna
	        input()                                 #Esperar reacción
	        t1 = time.time() - t0 - pausa           #Cálculo diferencia de tiempo
	        self.datos.append(t1)                   #Guardar dato en la lista
	    self.corregir_datos()                       #Corregir datos
```

### Utilizando nuestra clase

```python
# Generar un str random como ID
import random

sujeto_id = str(random.random())[2:]
sujeto_id
```
$$Consola$$
![[Pasted image 20230825111136.png]]

#### Instanciar sujeto
```python
info = {"edad":"32", "fecha_nacimiento":"01-01-1998","años_educacion":12}
sujeto = Sujeto(sujeto_id,info)
```

#### Instanciar tiempo de reacción
```python
tr = TiempoDeReaccion(sujeto, nombre="Tiempo de Reaccion",consigna="¡Apreta ENTER!")
```

#### Llamar método tomar experimento
```python
tr.tomar_experimento(n_trials=2, rango_pausa=3)
```
$$Consola$$
![[Pasted image 20230827224839.png]]

### ¿Qué datos contiene?
#### Llamamos un atributo
```python
tr.datos
```
$$Consola$$
![[Pasted image 20230827225103.png]]

```python
sujeto
```
$$Consola$$
![[Pasted image 20230827225152.png]]


### Cuestionario
Generamos un cuestionario de ejemplo. Cada pregunta debe estar separada en un renglón( es decir por un caracter de newline, generalmente \n)

#### Creamos un txt con el cuestionario
```python
with open("cuestionario.txt", "w") as out:
    out.write(
        '''
        1. Me siento calmado.
        2. Estoy tenso.
        3. Estoy contrariada.
        4. Me siento a gusto.
        '''
    )
```

### Creamos una clase Cuestionario

```python
class Cuestionario(Experimento):
    '''
    Otro caso de prueba que hereda de experimento. Esta vez la inicialización
    incluye cargar las preguntas en el atributo self.preguntas
    '''
    def __init__(self,path_cuestionario,*args,**kwargs):
        super().__init__(*args, **kwargs)
        self.cargar_preguntas(path_cuestionario)
  
    def cargar_preguntas(self,path):
        #Completar
        #Función que lee el txt y guarda cada renglón en self.preguntas
        with open(path, "r") as f:
            preguntas = f.read().split("\n") #Separamos por renglón
        self.preguntas = preguntas
  
    def corregir_datos(self):
        self.sujeto.resultados[f"Total{self.nombre}"] = sum(self.datos)
  
    def tomar_experimento(self):
        #Completar
        #Dar la instrucción
        #Tomar cada pregunta con input()
        #Convertir la entrada a entero
        self.instruccion()
        for pre in self.preguntas:
            respuesta = input(pre)
            self.datos.append(int(respuesta))
        self.corregir_datos()
```


### Usamos la clase para tomar el cuestionario
```python
consigna = '''Aparecerán abajo algunas expresiones que las personas usan para describirse.
Lea cada frase y presione el número que indique cómo se siente ahora mismo, siendo
0 = NO, 1 = POCO, 2 = BASTANTE, 3 = MUCHO. '''
  
stai = Cuestionario('cuestionario.txt', sujeto, consigna = consigna, nombre='Cuestionario')
```

```python
stai.tomar_experimento()
```
$$Consola$$
![[Pasted image 20230829191416.png]]


```python
sujeto
```
$$Consola$$
![[Pasted image 20230829191435.png]]


### Generando reporte
Una vez realizado el ejercicio vamos a generar una clase para realizar el reporte del experimento.

La clase Reporte va a generar un documento que contendrá:

    Un método para analizar los datos resultado del experimento;

    Un método para crear gráficos a partir de los resultados.

    Un método para para generar el informe final

Para los gráficos vamos a usar matplotlib, que tiene métodos como "plot" donde recibe listas de números y genera un objeto "Figura". En este tema de visualización se ahonda en el curso de Análisis de Datos. La función sns.set() simplemente aplica un estilo.

#### Programa de ejemplo de plt para mostrar la frecuencia de aparición de los números de la lista
```python
import matplotlib.pyplot as plt
import seaborn as sns
sns.set()
  
# Pequeño ejemplo de matplotlib
plt.hist([1,2,3,6,4,1,2,3,2,4])
```
$$Consola$$
![[Pasted image 20230829191550.png]]



### Usamos la librería docx para aprovechar el documento
```python
from docx import Document
from docx.shared import Cm
```


### Creamos la clase Reporte
```python
class Reporte():
    '''Esta clase va a generar un reporte para un Sujeto a partir de un Experimento'''
    def __init__(self, sujeto: Sujeto, experimento: Experimento, img_path = 'tmp.png'):
        self.suj = sujeto
        self.exp = experimento
        self.img_path = img_path

    def crear_graficos(self):
        '''Genera un gráfico de lineas y un histograma para
        los datos de los experimentos'''
        fig, ax = plt.subplots(1,2, figsize=(11,4))
        ax[0].plot(self.exp.datos)
        ax[0].set_ylabel('Error (ms)')
        ax[0].set_xlabel('Trials')
        sns.distplot(self.exp.datos, ax=ax[1])
        ax[1].set_ylabel('Frequencia')
        ax[1].set_xlabel('Error (ms)')
        return ax

    def generar_reporte(self):
        '''Función que genera un documento de Word en base a los datos
        de Sujeto y Experimento. Ver más en:
        https://python-docx.readthedocs.io/en/latest/
        '''
        # Instanciamos un Documento
        documento = Document()
        # Agregamos un Titulo
        documento.add_heading(f'Informe de Resultados', 0)
        # Info del sujeto
        p = documento.add_paragraph(f'Sujeto ID: ')
        p.add_run(f'{self.suj.id}').bold = True
        # Agregamos una lista de items iterando
        # el diccionario de info del Sujeto
        for k, v in self.suj.info.items():
            documento.add_paragraph(f'{k}= {v}',
                                   style='List Bullet')
        # Agregamos resultados, hay distintos estilos disponibles
        p = documento.add_paragraph(f'Resultados de {self.exp.nombre}',
                                   style='Intense Quote')
        # COMPLETAR
        # iterar los resultados en self.suj.resultados
        # agregando otra lista de items
        for k,v in self.suj.resultados.items():
            documento.add_paragraph(f"{k}={v}",
                                    style="List Bullet")
        # Agregamos los gráficos
        ax = self.crear_graficos()
        plt.savefig(self.img_path) # usamos esta ruta provisorialmente
        plt.close() # para no mostrar el plot y solo guardarlo
        documento.add_picture(self.img_path, width=Cm(14))

        # Guardamos el archivo docx
        fp = f'reporte_{self.suj.id}.docx'
        documento.save(fp)
        return fp
```



### Instanciamos un Reporte
```python
rep = Reporte(sujeto, tr)
```


### Generamos un reporte
```python
fp = rep.generar_reporte()
```
$$Consola$$
![[Pasted image 20230829191817.png]]

### Descargamos el doc en colab
```python
from google.colab import files
  
files.download(fp)
```


### Así seria la función de descarga para Jupyter Note Book
```python
from IPython.display import display, FileLink
  
# Muestra un enlace para descargar el archivo
display(FileLink(fp, result_html_prefix="Haz clic para descargar: "))
```
$$Consola$$
![[Pasted image 20230829191918.png]]

#espaciado_fijo #repr #tostring #docx #word
___
## 9- Función que pasa a mayúsculas las letras que son una vocal, dada una palabra

**VERSIÓN 1**: Creando una lista y añadiendo las letras a esta, y al final convertimos la lista a un string y sustituimos las "," por espacios
```python
nueva_palabra=[]
  
def palabra_a_mayus(palabra: str):

    for n in palabra:
        if n.isalpha():
            if n in "aeiou":
                nueva_palabra.append(n.upper())
            else:
                nueva_palabra.append(n.lower())
        else:
            nueva_palabra.append(n.lower())
    return "".join(nueva_palabra)

palabra_a_mayus("cartilago")
```
$$Consola$$
![[Pasted image 20230902185751.png]]


**VERSIÓN 2**: Concatenando cada palabra a un nuevo String directamente 
```python
nueva_palabra=""
  
def palabra_a_mayus(palabra:str):
    global nueva_palabra
    for n in palabra.lower():
        if n in "aeiou":
            nueva_palabra += n.upper()
        else:
            nueva_palabra += n
    return nueva_palabra
  
palabra_a_mayus("CARTILAGO")
```
$$Consola$$
![[Pasted image 20230902185751.png]]

___



































___
%%
tags:  #programación #pagfundamentospython #python  

Vínculos:  [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%
