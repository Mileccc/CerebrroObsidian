---
ID:: 070
tags:: #programación #pagfundamentospython #python  #AttributeError #NameError #KeyError #SyntaxError #TypeError #IndexError #error
nombre:: "Errores"
---
___
# Errores
![](https://youtu.be/EVZ7HRUBDc4?t=1376)
___

## Tipos de errores

El **traceback** o **stack trace** nos muestra el camino del error: veremos más adelante que cuando tenemos funciones anidadas, vemos aquí como el error se propaga.

Las cosas a las que en principio les debemos prestar atención son:

1. El nombre del error, en este caso **TypeError**
2. La explicación dada en el último renglón: "'tuple' object doesn't support item deletion"
3. La flecha que nos indica la línea en la que ocurrió el error


Existen distintos tipos de errores en Python, pueden consultar la lista de todas las excepciones básicas acá: [https://docs.python.org/3/library/exceptions.html#bltin-exceptions](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fdocs.python.org%2F3%2Flibrary%2Fexceptions.html%23bltin-exceptions)

Sin embargo, las excepciones más frecuentes son:

_**AttributeError**_: cuando tratamos de llamar a una referencia que no existe.

_**NameError**:_ cuando se llama a una variable u otro nombre que no está definido en el ambiente en que estamos trabajando.

_**KeyError**:_ cuando queremos llamar a una llave que no existe, por ejemplo, en un diccionario.

_**SyntaxError**:_ cuando hay un problema de sintaxis, errores muy comunes al comienzo pueden ser que no se cerró una llave o corchete, que falta alguna coma o dos puntos.

_**TypeError**:_ cuando el tipo de soporta una determinada operación.

_**IndexError**:_ cuando el índice al que se quiere acceder no existe, generalmente debido a que se llama a un índice mayor al largo de la lista.


Veamos algunos ejemplos:

![[Pasted image 20230814230907.png]]

![[Pasted image 20230814230937.png]]


## Manejo de errores
Para anticipar y manejar los errores, podemos usar la clausula **try** y **except**
![[Pasted image 20230814231047.png]]

Si queremos ver qué excepción ocurrió, podemos usar la siguiente sintaxis:

![[Pasted image 20230814231114.png]]

También podemos especificar qué hacer para distintos tipos de error:

![[Pasted image 20230814231247.png]]



___

%%
tags:  #programación #pagfundamentospython #python   #AttributeError #NameError #KeyError #SyntaxError #TypeError #IndexError #error

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%