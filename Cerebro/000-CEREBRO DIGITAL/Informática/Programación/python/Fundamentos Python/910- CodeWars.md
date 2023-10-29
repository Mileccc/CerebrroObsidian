---
ID: 910
"tags:": "#programación #pagfundamentospython #python"
"nombre:": CodeWars
---
___
# CodeWars
___
## 1- Función para eliminar vocales de una palabra dada


```python
print(eliminarVocales*("casita"))
```
$$\color{red}***CONSOLA***$$
![[Pasted image 20230904221602.png|100]]

___
### 1.1- Forma básica

```python
def eliminarVocales1(palabra):
    nueva_palabra=""
    for n in palabra :
        if n.lower() not in "aeiou":
            nueva_palabra += n
    return nueva_palabra
```

### 1.2- Directamente con un join

```python
def eliminarVocales2(palabra):
    return "".join(c for c in palabra if c.lower() not in "aeiou")
```

### 1.3- Usando replace y recorriendo con el ciclo las vocales y no la palabra

```python
def eliminarVocales3(palabra):
    for i in "aeiouAEIOU":
        palabra = palabra.replace(i,"")
    return palabra
```

### 1.4- Utilizando el módulo de expresiones regulares de python
**Uso de re.sub:**
re.sub es una función proporcionada por el módulo re que se utiliza para reemplazar patrones en una cadena de texto con otro texto o cadena vacía. En este caso, se está utilizando para reemplazar todas las vocales (mayúsculas o minúsculas) en la cadena string con una cadena vacía ''.
  
**Patrón de búsqueda '[aeiou]':**
El patrón de búsqueda `[aeiou]` representa un conjunto de caracteres que coincide con cualquier vocal minúscula ('a', 'e', 'i', 'o', 'u') en la cadena. El uso de `[aeiou]` dentro de corchetes indica que coincidirá con cualquiera de esos caracteres.
  
**Flag flags = re.IGNORECASE:**

La bandera re.IGNORECASE se utiliza para que la búsqueda sea insensible a mayúsculas y minúsculas. Esto significa que coincidirá tanto con vocales en mayúsculas como en minúsculas.

```python
import re

def eliminarVocales4(palabra):
    return re.sub('[aeiou]', '', palabra, flags = re.IGNORECASE)
```

### 1.5- Usando un ciclo while

```python
def eliminarVocales5(palabra):
    vocales = ["a", "A", "e", "E", "o", "O", "i", "I", "u", "U"]
    nueva_palabra = ""
    i = 0
    n = len(palabra)
    while i < n:
        if not palabra[i] in vocales:
            nueva_palabra += palabra[i]
        i += 1
    return nueva_palabra
```

### 1.6- Usando translate
**La función translate** se utiliza para realizar una traducción de caracteres en una cadena de texto. En este caso, se está utilizando para eliminar las vocales de la cadena string.

**La función ord():** se utiliza para obtener el valor numérico de las letras minúsculas y mayúsculas que deseamos eliminar.

```python
def eliminarVocales6(palabra):
    diccionario_traduccion = {ord('a'): None, ord('A'): None, ord('e'): None, ord('E'): None,
                        ord('i'): None, ord('I'): None, ord('o'): None, ord('O'): None,
                        ord('u'): None, ord('U'): None}
    return palabra.translate(diccionario_traduccion)
```

___
## 2- Filtrar una lista y devuelve otra lista con solo los valores numéricos

```python
print(filtrar_lista([1,"r",9,"45","T",12]))

#Para punto 2.5
print(filter_list([1,"r",9,"45","T",12]))
```
$$\color{red}***CONSOLA***$$
![[Pasted image 20230904222321.png|200]]

\color{red}
___
### 2.1- Con isinstance() y ciclo for

```python
def filtrar_lista(lista):
    nueva_lista=[]
    for n in lista:
        if isinstance(n, int) :
            nueva_lista.append(n)
    return nueva_lista
```

### 2.2- Igual pero con una lista pro comprensión

```python
def filtrar_lista1(lista):
    return [n for n in lista if isinstance(n, int)]
```

### 2.3- Usando type()

```python
def filtrar_lista2(lista):
  'return a new list with the strings filtered out'
  return [x for x in lista if type(x) is not str]
```

### 2.4- Usando lambda
***Uso de la función filter:***
La función filter() se utiliza para filtrar elementos de una secuencia (en este caso, una lista) en función de una función de filtro que se le proporciona. En este caso, la función filter se utiliza para filtrar los elementos de la lista lista que cumplan con la condición especificada en la función de filtro.

***Función de filtro con lambda:***
En el argumento de la función filter, se utiliza una expresión lambda (lambda x: isinstance(x, int)) como la función de filtro. Esta expresión lambda toma un elemento x de la lista y verifica si es de tipo int utilizando isinstance(x, int). Si la condición se cumple, es decir, si x es un entero, se incluye en la nueva lista resultante.

***Conversión a lista:***
La función filter devuelve un objeto iterable (un iterador) que contiene los elementos que cumplieron con la condición del filtro. Para convertir este iterador en una lista, se utiliza list(). Esto garantiza que la función filtrar_lista3 devuelva una lista con los elementos enteros de la lista original.

```python
def filtrar_lista3(lista):
  return list(filter(lambda x: isinstance(x, int), lista))
```

### 2.5- Con expresión lamba sin funcion

```python
filter_list = lambda l: [e for e in l if isinstance(e, int)]
```

___
## 3- Habitantes cada año
En un pueblo pequeño la población es `p0 = 1000`a principios de un año. La población aumenta regularmente en `2 percent`por año y además `50`nuevos habitantes al año vienen a vivir a la localidad. ¿Cuántos años necesita el pueblo para ver su población? mayor o igual a `p = 1200`habitantes?

```
At the end of the first year there will be: 
1000 + 1000 * 0.02 + 50 => 1070 inhabitants

At the end of the 2nd year there will be: 
1070 + 1070 * 0.02 + 50 => 1141 inhabitants (** number of inhabitants is an integer **)

At the end of the 3rd year there will be:
1141 + 1141 * 0.02 + 50 => 1213

It will need 3 entire years.
```

```
Examples:
nb_year(1500, 5, 100, 5000) -> 15
nb_year(1500000, 2.5, 10000, 2000000) -> 10
```


```python
print(nuevo_año*(1000,2,50,1200))
```
$$***CONSOLA***$$
![[Pasted image 20230904234030.png|100]]


___
### 3.1- Con un ciclo while

```python
def nuevo_año(p0,porciento,incremento,p):
    count = 0
    porciento/=100
    while p0 < p:
        p0=int(p0 + p0*porciento+incremento)
        count += 1
    return count
```

### 3.2- Con recursividad

```python
def nuevo_año1(p0, porciento, incremento, p, years = 0):
    if p0 < p:
        return nuevo_año1(p0 + int(p0 * porciento / 100) + incremento, porciento, incremento, p, years + 1)
    return years
```

### 3.3- Con recursividad y comprensión

```python
def nuevo_año2(p0, porciento, incremento, p, i=0):
    return i if p0>=p else nuevo_año2(int(p0+p0*(porciento/100)+incremento), porciento, incremento, p, i+1)
```

### 3.4- Usar floor() para redondear a la baja

```python
from math import floor

def nuevo_año3(p0, porciento, incremento, p):
    i = 1
    mult = 1 + porciento / 100.0
    prev = p0
    while (prev < p):
        ne = floor((prev * mult + incremento))
        prev = ne
        i += 1
    return (i - 1)
```

___

## 4- Invertir palabra
___
### 4.1- Forma básica sin función

```python
palabra = "Probando una palabara"
nueva_palabra = ""
  
for n in palabra[::-1]:
    nueva_palabra += n
```

### 4.2- Función básica con for
```python
def inversa(palabra):
    nueva_palabra=""
    for n in palabra[::-1]:
        nueva_palabra += n
    return nueva_palabra
```



### 4.3- Usando una lista por comprensión y join
```python
def inversa1(palabra):
    letras_invertidas = [n for n in palabra[::-1] ]
    nueva_palabra = "".join(letras_invertidas)
    return nueva_palabra
```


### 4.4- Usando reverse
```python
def inversa2(palabra):
    lista_palabras = list(palabra)
    lista_palabras.reverse()
    nueva_palabra = "".join(lista_palabras)
    return nueva_palabra
```


### 4.5- Usando while
```python
def inversa3(palabra):
    nueva_palabra = ""
    i = len(palabra) - 1
    while i >= 0:
        nueva_palabra += palabra[i]
        i -= 1
    return nueva_palabra
```

### 4.6- Usando recursión
```python
def inversa4(palabra):
    if len(palabra) == 0:
        return palabra
    else:
        return inversa4(palabra[1:]) + palabra[0]
```

![[Pasted image 20230907131811.png]]

### Usando lambda función reduce de la biblioteca functools
```python
from functools import reduce
  
def inversa5(palabra):
    return reduce(lambda x, y: y + x, palabra)
```
![[Pasted image 20230907132711.png]]


### Consola
```python
print(inversa("Probando una palabra"))
print(inversa1("Probando una palabra"))
print(inversa2("Probando una palabra"))
print(inversa3("Probando una palabra"))
print(inversa4("Probando una palabra"))
print(inversa5("Probando una palabra"))
```
$$Consola$$
![[Pasted image 20230907131154.png]]


## 5- Invertir solo letras sin alterar el orden de las palabras en la frase

### 5.1- split(), lista por comprensión, join()
```python
def invertir_palabras(frase):
    palabras = frase.split()  # Dividir la frase en palabras
    palabras_invertidas = [palabra[::-1] for palabra in palabras]  # Invertir cada palabra
    frase_invertida = " ".join(palabras_invertidas)  # Unir las palabras invertidas en una frase
    return frase_invertida
```

### 5.2-  Lo mismo pero todo a la vez por comprensión
```python
def invertir_palabras2(frase):
    return ' '.join(s[::-1] for s in frase.split(' '))
```

### 5.3- Usando una lista y añadiendo los caracteres
```python
def invertir_palabras3(frase):
  #go for it
  newStr = []
  for i in frase.split(' '):
      newStr.append(i[::-1])
  return ' '.join(newStr)
```


### 5.4- Biblioteca re y funcion lambda
```python
import re
  
def invertir_palabras4(frase):
  return re.sub(r'\S+', lambda w: w.group(0)[::-1], frase)
```



### 5.5- Con función lambda
```python
def invertir_palabras5(frase):
  return " ".join(map(lambda word: word[::-1], frase.split(' ')))
```





### 5.6- Con biblioteca re
```python
import re
  
def invertir_palabras6(frase):
  return ''.join(word[::-1] for word in re.split(r'(\s+)', frase))
```




### CONSOLA
```python
print(invertir_palabras("double  spaces"))
print(invertir_palabras2("double  spaces"))
print(invertir_palabras3("double  spaces"))
print(invertir_palabras4("double  spaces"))
print(invertir_palabras5("double  spaces"))
print(invertir_palabras6("double  spaces"))
```
$$Consola$$
![[Pasted image 20230907143929.png]]

___
## 6- Crear lista a partir de 2 lista suprimiendo en A los elementos de B
Tu objetivo en este kata es implementar una función de diferencia, que resta una lista de otra y devuelve el resultado. Debería eliminar todos los valores de la lista a, que están presentes en la lista b manteniendo su orden.

```python
array_diff([1,2],[1]) == [2]
```

Si un valor está presente en b, todas sus apariciones deben eliminarse del otro:

```python
array_diff([1,2,2,2,3],[2]) == [1,3]
```

***SOLUCIÓN:***
```python
print(array_diff([1,2,2],[1]))
print(array_diff([1,2,2,2,3],[2]))
print(array_diff([2],[1,2,2,2,3]))
print(array_diff([],[1,2]))
```
$$CONSOLA$$
![[Pasted image 20230908110833.png]]

### 1- Lista por comprensión

```python
def array_diff(a, b):
    return [x for x in a if x not in b]
```



### 2- Usando función filter
```python
def array_diff(a, b):
    return list(filter(lambda x: x not in b, a))
```


### 3- Usando while
```python
def array_diff(a, b):
    for n in b:
        while(n in a):
            a.remove(n)
    return a
```

***OTRAS FORMAS INTERESANTES SIN EL MISMO RESULTADO***

### 4- Usando Conjuntos y Diferencia de Conjuntos:
Si a tiene 2 elementos repetidos no serviría
```python
def array_diff(a, b):
    set_a = set(a)
    set_b = set(b)
    diff = set_a - set_b
    return list(diff)
```



### 5- Forma básica con for anidados
En esta versión elimina de la lista mayor los elementos de la lista menor
```python
def array_diff(a, b):
    lista_final=[]
    if (len(a) > len(b)) & len(b) != 0 :
        for i in a:
            count=0
            for j in b:
                if i == j:
                    count +=1
            if count == 0:
                lista_final.append(i)
        return lista_final        
  
    elif (len(b) > len(a)) & len(a) != 0 :
        for i in b:
            count=0
            for j in a:
                if i == j:
                    count +=1
            if count == 0:
                lista_final.append(i)
        return lista_final  
    elif len(a)==0:
        lista_final = b
        return lista_final
    else:
        lista_final = a
        return lista_final
```

___
## 7- Mostrar texto según cadena entregada de una lista

Seguramente conoces el sistema de "me gusta" de Facebook y otras páginas. Las personas pueden dar "me gusta" a publicaciones de blogs, imágenes u otros elementos. Queremos crear el texto que debe mostrarse junto a dicho elemento. Implementa la función que reciba un array que contiene los nombres de las personas que dieron "me gusta" a un elemento. Debe devolver el texto de visualización tal como se muestra en los ejemplos: 
```
[]                                    --> "no one likes this" 
["Peter"]                             --> "Peter likes this" 
["Jacob", "Alex"]                     --> "Jacob and Alex like this" 
["Max", "John", "Mark"]               --> "Max, John and Mark like this" 
["Alex", "Jacob", "Mark", "Max"]      --> "Alex, Jacob and 2 others like this" 
```
Nota: Para 4 o más nombres, el número en "and 2 others" simplemente aumenta.

```python
print(likes([]))
print(likes(["Peter"]))
print(likes(["Jacob", "Alex"]))
print(likes(["Max", "John", "Mark"]))
print(likes(["Alex", "Jacob", "Mark", "Max"]))
print(likes(["Alex", "Jacob", "Mark", "Max","Adan"]))
```
$$Consola$$
![[Pasted image 20230909194419.png]]
### Con if anidados

```python
def likes(names):
    if len(names) == 0:
        return "no one likes this"
    elif len(names) == 1:
        return f"{names[0]} likes this"
    elif len(names) == 2:
        return f"{names[0]} and {names[1]} like this"
    elif len(names) == 3:
        return f"{names[0]}, {names[1]} and {names[2]} like this"
    else:
        return f"{names[0]}, {names[1]} and {len(names)-2} others like this"
```


### Con un diccionario , funcion min() y formateo de texto
La función ``min()`` en el contexto de este código se utiliza para determinar cuál de dos valores es el más pequeño y devolver ese valor.

```python
def likes(names):
    n = len(names)
    return {
        0: 'no one likes this',
        1: '{} likes this',
        2: '{} and {} like this',
        3: '{}, {} and {} like this',
        4: '{}, {} and {others} others like this'
    }[min(4, n)].format(*names[:3], others=n-2)
```

___
## 8- Recibir un numero y mostrar sus cuadrados de sus unidades
Bienvenido. En este kata, se te pide elevar al cuadrado cada dígito de un número y concatenarlos. 

Ejemplo #1, si ejecutamos 9119 a través de la función, saldrá 811181, porque $9^2$ es 81 y $1^2$ es 1. (81-1-1-81) Ejemplo #2: Una entrada de 765 devolverá/debería devolver 493625 porque $7^2$ es 49, $6^2$ es 36 y $5^2$ es 25. (49-36-25) 

Nota: La función acepta un número entero y devuelve un número entero.

### 8.1- for básico y cast de str ,int

```python
def square_digits(num):
    cadena=""
    for n in str(num):
        cadena += str(int(n)**2)
    return int(cadena)
```


### 8.2- Con un join y for x comprension
```python
def square_digits(num):
    return int("".join(str(int(n)**2) for n in str(num)))
```


### 8.3- Con while
```python
def square_digits(num):
    result = 0  
    multiplier = 1  
    while num:  
        digit = num % 10 
        result += digit ** 2 * multiplier  
        multiplier *= (10, 100)[digit > 3]
        num //= 10  
    return result  
```


### 8.4- Con recursividad
```python
def square_digits_recursive(num):
    if num < 10:
        return num ** 2
    else:
        last_digit = num % 10
        rest_of_num = num // 10
        squared_last_digit = last_digit ** 2
        return int(str(square_digits_recursive(rest_of_num)) + str(squared_last_digit))
```


```python
print(square_digits(725))
print(square_digits(9119))
```
$$Consola$$
![[Pasted image 20230910232737.png]]

___
## 9- Correr ceros al final de una lista
___
Escribe un algoritmo que tome una matriz y mueva todos los ceros hasta el final, preservando el orden de los demás elementos.

```
move_zeros([1, 0, 1, 2, 0, 1, 3]) # returns [1, 1, 2, 1, 3, 0, 0]
```

### 1- Sustituir en la misma Linea mientras se recorre con un ciclo
```python
def move_zeros(lst):
    count = 0
    n = len(lst)
    for i in range(n):
        if lst[i] != 0:
            lst[count], lst[i] = lst[i], lst[count]
            count += 1
    return lst
```


### 2- Crear una lista contando los 0 y otra lista solo con los numeros sin cero, luego unirlas

```python
def move_zeros(lst):
    # Filtrar los ceros y los no ceros
    ceros = [0] * lst.count(0)
    no_ceros = [num for num in lst if num != 0]
    # Combinar la lista de no ceros con la lista de ceros al final
    lst = no_ceros + ceros
    return lst
```

### 3- Parecido al anterior

```python
def move_zeros(lst):
    # Filtrar todos los elementos que no son cero
    non_zeros = [x for x in lst if x != 0]
    # Contar cuántos ceros hay en la lista original
    num_zeros = len(lst) - len(non_zeros)
    # Agregar los ceros al final de la lista
    lst = non_zeros + [0] * num_zeros
    return lst
```

### 4- Por compresión

```python
def move_zeros(arr):
    l = [i for i in arr if i!=0]
    return l+[0]*(len(arr)-len(l))
```

### 5- Con una funcion lambda

```python
def move_zeros(array):
    return sorted(array, key=lambda x: x==0 and type(x) is not bool)
```


### RESULTADO

```python
print(move_zeros([1, 2, 0, 1, 0, 1, 0, 3, 0, 1]))
```
$$Consola$$
![[Pasted image 20230911232812.png]]


___

## 10- Voltear solo palabras mayores de 5
Escriba una función que tome una cadena de una o más palabras y devuelva la misma cadena, pero con las palabras de cinco o más letras invertidas (como el nombre de este Kata). Las cadenas pasadas consistirán únicamente en letras y espacios. Los espacios se incluirán únicamente cuando esté presente más de una palabra. Ejemplos:

```
spinWords( "Hey fellow warriors" ) => returns "Hey wollef sroirraw" 
spinWords( "This is a test") => returns "This is a test" 
spinWords( "This is another test" )=> returns "This is rehtona test"
```

### 1- Forma básica con for , split, slicing y join

```python
def spin_words(sentence):
    nueva_palabra=[]
    lista_palabras = sentence.split(" ")
    for palabra in lista_palabras:
        if len(palabra)>= 5:
            palabra = palabra[::-1]
        nueva_palabra.append(palabra)
    return " ".join(nueva_palabra)
```

### 2- Igual pero con compresión

```python
def spin_words(sentence):
    return " ".join([palabra[::-1] if len(palabra)>=5 else palabra for palabra in sentence.split(" ")])
```

### 3- Con re y lambda
En la línea de retorno (return), utilizamos re.sub() para reemplazar patrones en la cadena sentence. La función re.sub() toma tres argumentos:
  
    El primer argumento es un patrón de expresión regular que queremos buscar en la cadena.
    El segundo argumento es una función o una cadena que reemplazará las coincidencias encontradas por el patrón.
    El tercer argumento es la cadena en la que queremos buscar y reemplazar.
  
El patrón de expresión regular que usamos es r"\w{5,}". Aquí hay una descripción del patrón:
  
    \w: Coincide con cualquier carácter alfanumérico (letras y números) y el guión bajo _.
    {5,}: Esto indica que el patrón \w debe aparecer al menos 5 veces seguidas.
  
El segundo argumento de re.sub() es una función lambda (lambda w: w.group(0)[::-1]). Esta función toma una coincidencia encontrada (w) y la invierte usando la técnica de "slicing" ([::-1]). En otras palabras, esta función toma palabras de al menos 5 caracteres y las invierte.
  
El tercer argumento de re.sub() es la cadena sentence en la que queremos buscar y reemplazar.

```python
import re
  
def spin_words(sentence):
    # Your code goes here
    return re.sub(r"\w{5,}", lambda w: w.group(0)[::-1], sentence)
```

### SOLUCIÓN
```python
print(spin_words("Hey fellow warriors"))
print(spin_words("This is a test"))
print(spin_words("This is another test"))
```
$$Consola$$
![[Pasted image 20230912183646.png]]


___
## 11- Conteo de caracteres en una palabra a un diccionario

La idea principal es contar todos los caracteres que aparecen en una cadena. Si tiene una cadena como ``aba``, entonces el resultado debería ser ``{'a': 2, 'b': 1}``. ¿Qué pasa si la cadena está vacía? Entonces el resultado debería ser un objeto literal vacío, ``{}``.

### 1- Forma básica con for y keys()
```python
def count(s):
    diccionario= {}
    for posicion in range(len(s)):
        if s[posicion] in diccionario.keys():
            diccionario[s[posicion]]+=1
        else:
            diccionario[s[posicion]]=1
    return diccionario
```


### 2- Con compresión y count()
```python
def count(s):
    return {char: s.count(char) for char in s}
```

### 3- Usando la función Counter()
Función especializada en contar los caracteres de una palabra que regresa un diccionario en el que las claves son los caracteres únicos y los valores las frecuencias de esos valores

```python
from collections import Counter
  
def count(string):
    return Counter(string)
```

### 4- Usando get()
```python
def count(string):
    counter = {}
    for char in string:
        counter[char] = counter.get(char, 0) + 1
    return counter
```

### SOLUCIÓN

```python
print(count("aba"))
print(count("onomatopella"))
print(count("La casa del arbol"))
```
$$Consola$$
![[Pasted image 20230912191646.png]]



___
## 12- Validador de coordenadas

Vives en la ciudad de Cartesia, donde todas las carreteras están dispuestas en una cuadrícula perfecta. Llegaste diez minutos antes a una cita, por lo que decidiste aprovechar para dar un pequeño paseo. La ciudad proporciona a sus ciudadanos una aplicación generadora de caminatas en sus teléfonos: cada vez que presiona el botón, le envía una serie de cadenas de una letra que representan instrucciones para caminar (por ejemplo, ``['n', 's', 'w', 'e']``). Siempre caminas solo una cuadra por cada letra (dirección) y sabes que te toma un minuto atravesar una cuadra de la ciudad, así que crea una función que devolverá si la caminata que te da la aplicación te llevará exactamente diez minutos (¡No querrás llegar temprano ni tarde!) y, por supuesto, lo devolverá a su punto de partida. Devuelve falso en caso contrario.


Nota: siempre recibirá una matriz válida que contiene una variedad aleatoria de letras de dirección (solo ``'n', 's', 'e' ``o`` 'w'``). Nunca le dará una matriz vacía (¡eso no es un paseo, es quedarse quieto!).

___
***SOLUCIÓN***
En primer lugar, debemos comprender el problema. Luego veremos cuáles son sus entradas y, por supuesto, qué tipo de salida quiere de nosotros. 

Si lees el problema dos o tres veces, verás algunas cosas, como las que debemos tener en cuenta. 

- La caminata tiene que ser de 10 minutos. 
- Necesitas regresar al punto de partida. 
- Cada elemento de la lista (cada letra) o bloque individual representa un minuto 

Convirtamos estas instrucciones en código y hagamos pequeños segmentos del código completo de la solución: 
Entonces,

```python
if len(walk) == 10 #True  
else # False
```

Crearemos dos variables y las inicializaremos en 0 para rastrear nuestra caminata, ns (Norte-Sur) y ew (Este-Oeste).

```python
ns = 0
ew = 0
```

Por cada cuadra que caminemos, incrementaremos y disminuiremos respectivamente en 1

```python
if we move in n direction then ns += 1  
if we move in s direction (coming back) then ns -= 1
if we move in e direction then ew += 1  
if we move in w direction (coming back) then ew -= 1
```

Y finalmente comprobaremos si volvimos a nuestra misma posición o no.

```python
if ns == 0 and ew == 0 #True  
else #False
```

Combinemos todo esto:

```python
def is_valid_walk(walk):  
    ns, ew = 0, 0  
    if len(walk) == 10:  
        for i in walk:  
            if i == 'n': ns+=1  
            if i == 's': ns-=1  
            if i == 'w': ew+=1  
            if i == 'e': ew-=1  
    else:  
        return False  
    return ns == 0 and ew == 0
```


### 1- Forma básica

```python
def is_valid_walk(walk):  
    ns, ew = 0, 0  
    if len(walk) == 10:  
        for i in walk:  
            if i == 'n': ns+=1  
            if i == 's': ns-=1  
            if i == 'w': ew+=1  
            if i == 'e': ew-=1  
    else:  
        return False  
    return ns == 0 and ew == 0
```


### 2- Con count()

```python
def is_valid_walk(walk):
    ns, ew = 0, 0

    return len(walk) == 10 and (walk.count("n")-walk.count("s")) == 0 and (walk.count("e")-walk.count("w") == 0)
```





### SOLUCIÓN

```python
print(is_valid_walk(["n","n","n","n","n","s","s","s","s","s"]))
print(is_valid_walk(["s","w","n","e","w","s","e","s","w","s"]))
print(is_valid_walk(["s","e","s","e","s","n","n","n","w","w"]))
```
$$Consola$$
![[Pasted image 20230914121625.png]]


___
## 13- Confirmar 2 productos de fibonacci
Dado un número, digamos prod (para producto), buscamos verificar dos números de Fibonacci F(n) y F(n+1) 

```
productFib(714) # should return (21, 34, true), 
                # since F(8) = 21, F(9) = 34 and 714 = 21 * 34

productFib(800) # should return (34, 55, false), 
                # since F(8) = 21, F(9) = 34, F(10) = 55 and 21 * 34 < 800 < 34 * 55
-----
productFib(714) # should return [21, 34, true], 
productFib(800) # should return [34, 55, false], 
-----
productFib(714) # should return {21, 34, 1}, 
productFib(800) # should return {34, 55, 0},        
-----
productFib(714) # should return {21, 34, true}, 
productFib(800) # should return {34, 55, false}, 
```


### 1- Manera extendida

```python
def productFib(prod):
    # Inicializar los primeros dos números de Fibonacci
    fib1 = 0
    fib2 = 1
  
    # Iterar hasta encontrar un producto mayor o igual a 'prod'
    while fib1 * fib2 < prod:
        # Calcular el siguiente número de Fibonacci
        fib1, fib2 = fib2, fib1 + fib2
  
    # Comprobar si el producto es igual a 'prod'
    if fib1 * fib2 == prod:
        return [fib1, fib2, True]  # Devolver el resultado y True si es igual
    else:
        return [fib1, fib2, False]  # Devolver el resultado y False si es menor
```


### 2- Manera comprimida

```python
def productFib(prod):
  a, b = 0, 1
  while prod > a * b:
    a, b = b, a + b
  return [a, b, prod == a * b]
```

### SOLUCIÓN

```python
print(productFib(15))
print(productFib(54))
print(productFib(764))
print(productFib(714))
```
$$Consola$$
![[Pasted image 20230914125245.png]]

___
## 14- Extraer dominio de correo
Escriba una función que, cuando se le proporcione una URL como una cadena, analice solo el nombre de dominio y lo devuelva como una cadena. Por ejemplo:

```
* url = "http://github.com/carbonfive/raygun" -> domain name = "github"
* url = "http://www.zombie-bites.com"         -> domain name = "zombie-bites"
* url = "https://www.cnet.com"  
```


### 1- Versión simple con if y split()

```python
def domain_name(url):
    dominio = []
    if "www." in url:
        dominio = url.split(".")
        return dominio[1]
    elif "://" in url:
        dominio = url.split("//")
        dominio = dominio[1]
        dominio = dominio.split(".")
        return dominio[0]
    else:
        dominio = url.split(".")
        return dominio[0]
```


### 2- Igual al anterior pero comprimido

```python
def domain_name(url):
    if "www." in url:
        return url.split("www.")[1].split(".")[0]
    elif "://" in url:
        return url.split("://")[1].split(".")[0]
    else:
        return url.split(".")[0]
```

### 3- Aún mas comprimido

```python
def domain_name(url):
    return url.split("//")[-1].split("www.")[-1].split(".")[0]
```


### 4- Usando el modulo re (función que trabaja con expresiones regulares)

```python
import re
def domain_name(url):
    return re.search('(https?://)?(www\d?\.)?(?P<name>[\w-]+)\.', url).group('name')
```

### 5- Usando replace y find

```python
def domain_name(url):
    url = url.replace('www.','')
    url = url.replace('https://','')
    url = url.replace('http://','')
    return url[0:url.find('.')]
```

### SOLUCIÓN

```python
print(domain_name("http://github.com/carbonfive/raygun"))
print(domain_name("http://www.zombie-bites.com" ))
print(domain_name("https://www.cnet.com" ))
```
$$Consola$$
![[Pasted image 20230915111909.png]]

___
## 15- Seleccionar las tres palabras más repetidas
Escriba una función que, dada una cadena de texto (posiblemente con puntuación y saltos de línea), devuelva una matriz de las 3 palabras más frecuentes, en orden descendente del número de apariciones.

- Una palabra es una cadena de letras (de la A a la Z) que contiene opcionalmente uno o más apóstrofes (') en ASCII.
- Los apóstrofes pueden aparecer al principio, en medio o al final de una palabra ('abc, abc', 'abc', ab'c son todos válidos)
- Cualquier otro carácter (por ejemplo, #, \, /, . ...) no forma parte de una palabra y debe tratarse como un espacio en blanco.
- Las coincidencias no deben distinguir entre mayúsculas y minúsculas y las palabras del resultado deben estar en minúsculas.
- Los empates podrán romperse arbitrariamente.
- Si un texto contiene menos de tres palabras únicas, entonces se deben devolver las 2 palabras principales o la 1 primera, o una matriz vacía si un texto no contiene palabras.

#### Ejemplo
```
top_3_words("In a village of La Mancha, the name of which I have no desire to call to
mind, there lived not long since one of those gentlemen that keep a lance
in the lance-rack, an old buckler, a lean hack, and a greyhound for
coursing. An olla of rather more beef than mutton, a salad on most
nights, scraps on Saturdays, lentils on Fridays, and a pigeon or so extra
on Sundays, made away with three-quarters of his income.")

# => ["a", "of", "on"]

top_3_words("e e e e DDD ddd DdD: ddd ddd aa aA Aa, bb cc cC e e e")
# => ["e", "ddd", "aa"]

top_3_words("  //wont won't won't")
# => ["won't", "wont"]
```


### 1- Usando  all() y sorted()

```python
def top_3_words(text):
    palabras = text.split(" ")
    diccionario = {}
  
    for palabra in palabras:
        palabra = palabra.lower()
        if all(caracter.isalpha() or caracter == "'" for caracter in palabra):
            if palabra not in diccionario:
                diccionario[palabra] = 1
            else:
                diccionario[palabra] += 1
  
    # Función personalizada para obtener el valor de una clave en el diccionario
    def obtener_valor(clave):
        return diccionario[clave]
  
    # Ordenar el diccionario por valores en orden descendente usando la función personalizada
    diccionario_ordenado = sorted(diccionario, key=obtener_valor, reverse=True)
  
    # Obtener solo las palabras de las tres más repetidas
    palabras_mas_repetidas = diccionario_ordenado[:3]
    return palabras_mas_repetidas
```

### 2- Con modulo Counter y regex

```python
# use the Counter module
from collections import Counter
# use the regex module
import re
  
def top_3_words(text):
    # count the input, pass through a regex and lowercase it
    c = Counter(re.findall(r"[a-z']+", re.sub(r" '+ ", " ", text.lower())))
    # return the `most common` 3 items
    return [w for w,_ in c.most_common(3)]
```


### 3- Parecido al anterior

```python
import re
from collections import Counter
  
def top_3_words(text):
    words = re.findall(r"[a-z']*[a-z]+[a-z']*", text.lower())
    top_3 = Counter(words).most_common(3)
    return [tup[0] for tup in top_3]
```


### 4- Igual a los anteriores pero mas comprimido y con lambda

```python
import re
from collections import Counter
  
top_3_words=lambda t:[w for w,c in Counter(re.findall("'*[a-z][a-z']*",t.lower())).most_common(3)]
```


### 5- con un set() , join() y sorted()

```python
def top_3_words(text):
    if set(text.strip())=={"'"}:
        return []
    text = ''.join(i if i.isalpha() or i=="'" else ' ' for i in text.lower()).split()
    text = sorted(list(set(text)), key=text.count, reverse=True)
    return text[:3]
```

### 6- Dándole muchas vueltas con metodología de básicos

```python
def top_3_words(s):
    must_remove = ";/_?,.:!-"
    s = s.lower()
    words = {}
    for symbol in must_remove:
        s = s.replace(symbol, " ")
    s = [x for x in s.split() if x.replace("'", "") != ""]
    s1 = list(set(s))
    for w in s1:
        v = s.count(w)
        words[w] = v
    tuples = []
    x = ""
    m = 0
    index = 0
    l = len(words)
    while index < 3 and index < l:
        for k in words.keys():
            if words[k] > m:
                m = words[k]
                x = k
        tuples.append((x, m))
        del words[x]
        index += 1
        m = 0
    tuples.sort(key = lambda tup: tup[1], reverse = True)
    result = []
    for t in tuples:
        result.append(t[0])
    return result
```

### 7- Con join(), Counter y isalnum()

```python
from collections import Counter
  
def top_3_words(text):
    s = ''.join(t if t.isalnum() or t == "'" else ' ' for t in text.lower())
    return [i for i, _ in Counter(i for i in s.split() if len(i) != i.count("'")).most_common(3)]
```


### 8- all() , filter(), counts

```python
def top_3_words(text):
    for c in text:
        if not (c.isalpha() or c=="'"):
            text = text.replace(c,' ')
    words,counts,out = [],[],[]
    for word in list(filter(None,text.lower().split())):
        if all([not c.isalpha() for c in word]):
            continue
        if word in words:
            counts[words.index(word)] += 1
        else:
            words.append(word); counts.append(0)
    while len(words)>0 and len(out)<3:
        out.append(words.pop(counts.index(max(counts))).lower())
        counts.remove(max(counts))
    return out
```



### CONSOLA

```python
print(top_3_words("e e e e DDD ddd DdD: ddd ddd aa aA Aa, bb cc cC e e e"))

print(top_3_words("e e e e DDD ddd DdD: ddd ddd won't" "wont"))

print(top_3_words("e 'e' e e DDD aA' Aa, bb cc cC e'' e e"))```
$$Consola$$
![[Pasted image 20230918230436.png]]

___

## 16- Cifrado con ROT13
```
How can you tell an extrovert from an introvert at NSA?  
```

``Va gur ryringbef, gur rkgebireg ybbxf ng gur BGURE thl'f fubrf.``

Encontré este chiste en USENET, pero el remate está confuso. ¿Quizás puedas descifrarlo? 

Según Wikipedia, ROT13 se utiliza con frecuencia para ocultar chistes en USENET.

Para esta tarea sólo debes sustituir caracteres. No espacios, ni puntuación, ni números, etc.

Ejemplos de prueba:

```
"EBG13 rknzcyr." -> "ROT13 example."

"This is my first ROT13 excercise!" -> "Guvf vf zl svefg EBG13 rkprepvfr!"
```

### 1- Usando append, chr() y ord()

```python
def rot13(message):
    nueva_palabra = []
    for i in message:
        if i.isalpha():
            if i.isupper():
                nueva_palabra.append(chr(((ord(i) - ord('A') + 13) % 26) + ord('A')))
            elif i.islower():
                nueva_palabra.append(chr(((ord(i) - ord('a') + 13) % 26) + ord('a')))
        else:
            nueva_palabra.append(i)
    return "".join(nueva_palabra)
```

### 2- Usando lo mismo pero en vez de append una funcion interna
```python
def rot13(message):
    def decode(c):
        if 'a' <= c <= 'z':
            base = 'a'
        elif 'A' <= c <= 'Z':
            base = 'A'
        else:
            return c
        return chr((ord(c) - ord(base) + 13) % 26 + ord(base))
    return "".join(decode(c) for c in message)
```


### 3- Utilizando str con maketrans para crear una tabla de traduccion y translate para aplicarla
```python
import string
  
def rot13(message):
    first = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz'
    trance = 'NOPQRSTUVWXYZABCDEFGHIJKLMnopqrstuvwxyzabcdefghijklm'
    return message.translate(str.maketrans(first, trance))
```


### 4- Usando la librería especializada para decodificar
```python
def rot13(message):
    import codecs
    return codecs.encode(message, 'rot_13')
```



### 5- usando un diccionario , zip y get
```python
def rot13(message):
    PAIRS = dict(zip("abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ",
        "nopqrstuvwxyzabcdefghijklmNOPQRSTUVWXYZABCDEFGHIJKLM"))
    return "".join(PAIRS.get(c, c) for c in message)
```



### 6- Parecido al punto 3
```python
from string import ascii_lowercase as abc
from string import ascii_uppercase as ABC
  
def rot13(message):
    abc_message = abc + ABC
    abc_cipher = abc[13:] + abc[:13] + ABC[13:] + ABC[:13]
    return message.translate(str.maketrans(abc_message, abc_cipher))
```



### 7- Usando una funcion lambda
```python
def rot13(message):
    return ''.join(map(lambda c: chr(ord(c)+13) if c.isalpha() and c.lower() <= 'm' else
                                 chr(ord(c)-13) if c.isalpha() else c, message))
```



### SOLUCIÓN
```python
mensaje_cifrado = "Va gur ryringbef, gur rkgebireg ybbxf ng gur BGURE thl'f fubrf."
mensaje_descifrado = rot13(mensaje_cifrado)
print(mensaje_descifrado)
```

``In the elevators, the extrovert looks at the OTHER guy's shoes.``


___

## 16- Convertir a números Romanos y de números romanos

Escribe dos funciones que conviertan un número romano a un valor entero y viceversa. Se probarán múltiples valores de números romanos para cada función.

Los números romanos modernos se escriben expresando cada dígito por separado, comenzando con el dígito más a la izquierda y omitiendo cualquier dígito con un valor de cero. En números romanos, _1990_ se representa como: ``1000=M, 900=CM, 90=XC``; lo que resulta en **MCMXC**. _2008_ se escribe como ``2000=MM, 8=VIII;`` o **MMVIII**. _1666_ utiliza cada símbolo romano en orden descendente: **MDCLXVI**.

Rango de entrada: ``1 <= n < 4000``

En este kata, el ``4`` debe representarse como ``IV``, NO como ``IIII`` (el "cuatro del relojero").

### Examples

```
to roman:
2000 -> "MM"
1666 -> "MDCLXVI"
1000 -> "M"
 400 -> "CD"
  90 -> "XC"
  40 -> "XL"
   1 -> "I"

from roman:
"MM"      -> 2000
"MDCLXVI" -> 1666
"M"       -> 1000
"CD"      -> 400
"XC"      -> 90
"XL"      -> 40
"I"       -> 1
```

#### Help

|Symbol|Value|
|--:|:--|
|I|1|
|IV|4|
|V|5|
|X|10|
|L|50|
|C|100|
|D|500|
|M|1000|



```python
class RomanConverter:
    @staticmethod
    def to_roman(n):
        val = [
            1000, 900, 500, 400,
            100, 90, 50, 40,
            10, 9, 5, 4, 1
        ]
        syms = [
            "M", "CM", "D", "CD",
            "C", "XC", "L", "XL",
            "X", "IX", "V", "IV",
            "I"
        ]
        roman_num = ''
        i = 0
        while  n > 0:
            for _ in range(n // val[i]):
                roman_num += syms[i]
                n -= val[i]
            i += 1
        return roman_num
  
    @staticmethod
    def from_roman(s):
        val_dict = {
            'I': 1, 'V': 5, 'X': 10, 'L': 50,
            'C': 100, 'D': 500, 'M': 1000
        }
        result = 0
        prev_value = 0
        for c in s[::-1]:
            value = val_dict[c]
            if value < prev_value:
                result -= value
            else:
                result += value
            prev_value = value
        return result
  
# Ejemplos
print(RomanConverter.to_roman(2347))  # Output: "MM"
print(RomanConverter.from_roman("MMVII"))  # Output: 2000
```


## 17- Cifrado y descifrado

### 1- Usando append, chr() y ord()

```python
def rot13(message):
    nueva_palabra = []
    for i in message:
        if i.isalpha():
            if i.isupper():
                nueva_palabra.append(chr(((ord(i) - ord('A') + 13) % 26) + ord('A')))
            elif i.islower():
                nueva_palabra.append(chr(((ord(i) - ord('a') + 13) % 26) + ord('a')))
        else:
            nueva_palabra.append(i)
    return "".join(nueva_palabra)
```

  

### 2- Usando lo mismo pero en vez de append una funcion interna

```python
def rot13(message):
    def decode(c):
        if 'a' <= c <= 'z':
            base = 'a'
        elif 'A' <= c <= 'Z':
            base = 'A'
        else:
            return c
        return chr((ord(c) - ord(base) + 13) % 26 + ord(base))
    return "".join(decode(c) for c in message)
```

  

### 3- Utilizando str con maketrans para crear una tabla de traduccion y translate para aplicarla

```python
import string
  
def rot13(message):
    first = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz'
    trance = 'NOPQRSTUVWXYZABCDEFGHIJKLMnopqrstuvwxyzabcdefghijklm'
    return message.translate(str.maketrans(first, trance))
```

  

### 4- Usando la libreria especializada para decodificar

```python
def rot13(message):
    import codecs
    return codecs.encode(message, 'rot_13')
```

  

### 5- usando un diccionario , zip y get

```python
def rot13(message):
    PAIRS = dict(zip("abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ",
        "nopqrstuvwxyzabcdefghijklmNOPQRSTUVWXYZABCDEFGHIJKLM"))
    return "".join(PAIRS.get(c, c) for c in message)
```

  

### 6- Parecido al punto 3

```python
from string import ascii_lowercase as abc
from string import ascii_uppercase as ABC
  
def rot13(message):
    abc_message = abc + ABC
    abc_cipher = abc[13:] + abc[:13] + ABC[13:] + ABC[:13]
    return message.translate(str.maketrans(abc_message, abc_cipher))
```

  

### 7- Usando una funcion lambda

```python
def rot13(message):
    return ''.join(map(lambda c: chr(ord(c)+13) if c.isalpha() and c.lower() <= 'm' else
                                 chr(ord(c)-13) if c.isalpha() else c, message))
```


```python
mensaje_cifrado = "Va gur ryringbef, gur rkgebireg ybbxf ng gur BGURE thl'f fubrf."
mensaje_descifrado = rot13(mensaje_cifrado)
print(mensaje_descifrado)
```

    In the elevators, the extrovert looks at the OTHER guy's shoes.


___
## 18- Credit Card Mask

Por lo general, cuando compras algo, te preguntan si tu número de tarjeta de crédito, número de teléfono o respuesta a tu pregunta más secreta aún son correctos. Sin embargo, dado que alguien podría mirar por encima de tu hombro, no quieres que se muestre en tu pantalla. En su lugar, lo enmascaramos.

Tu tarea es escribir una función llamada ``maskify``, que cambie todos los caracteres excepto los últimos cuatro por '#'.

**Ejemplos (entrada --> salida):**

```
"4556364607935616" --> "############5616"
"64607935616" --> "#######5616"
"1" --> "1"
"" --> ""
  
// "What was the name of your first pet?"
"Skippy" --> "##ippy"
"Nananananananananananananananana Batman!" --> "####################################man!"
```

  

### 1- Versión larga básica

```python
def maskify(cc):
    cc=str(cc)
    if len(cc) <= 4:
        return cc
    nueva_cadena="#"*(len(cc)-4) # Crea una cadena de '#' del mismo tamaño que la parte a enmascarar
    return nueva_cadena+cc[-4:] # Concatena la parte enmascarada con los últimos 4 caracteres de cc
```

  

### 2- Misma versión anterior pero reducida

```python
def maskify(cc):
    return "#"*(len(cc)-4) + cc[-4:]
```

  

### 3- Usando .format

:: El símbolo : indica que se va a aplicar un formato.

#: El símbolo # indica que se va a rellenar el campo con el carácter especificado (en este caso, #) si es necesario para alcanzar el ancho de campo deseado.

>: El símbolo > indica que el valor (en este caso, message) debe alinearse a la derecha en el ancho de campo especificado. Esto significa que los caracteres adicionales (si es necesario rellenar) se colocarán a la izquierda del valor.


```python
def maskify(cc):
    return '{message:#>{fill}}'.format(message=cc[-4:], fill=len(cc))
```

### RESULTADO
```python
print(maskify(242343254534534))
print(maskify("Skippy"))
print(maskify("1"))
print(maskify(""))
```

    ###########4534
    ##ippy
    1


___

## 19- Contando duplicados


Escriba una función que devuelva el recuento de caracteres alfabéticos y dígitos numéricos distintos que no distinguen entre mayúsculas y minúsculas y que aparecen más de una vez en la cadena de entrada. Se puede suponer que la cadena de entrada contiene sólo alfabetos (tanto mayúsculas como minúsculas) y dígitos numéricos.

### 1- Forma larga

 

```python
def duplicate_count(text):
    lista_sin_repetidos=[]
    lista_completa=[]
    conteo=0
    for i in text.lower():
        if i not in lista_sin_repetidos:
            lista_sin_repetidos.append(i)
        lista_completa.append(i)
    for j in lista_sin_repetidos:
        if lista_completa.count(j)>=2:
            conteo+=1
    return conteo
```

  

### 2- Lista por compresion y con tupla
```python
def duplicate_count(s):
  return len([c for c in set(s.lower()) if s.lower().count(c)>1])
```

  
### 3- Usando tuplas

```python
def duplicate_count(text):
    seen = set()
    dupes = set()
    for char in text:
        char = char.lower()
        if char in seen:
            dupes.add(char)
        seen.add(char)
    return len(dupes)
```


```python
print(duplicate_count("abcde"))
print(duplicate_count("aabbcde"))
print(duplicate_count("aabBcde"))
print(duplicate_count("indivisibility"))
print(duplicate_count("Indivisibilities"))
print(duplicate_count("aA11"))
print(duplicate_count("ABBA"))
```

    0
    2
    2
    1
    2
    2
    2

___
## 20- Alternar caracteres en opuestos


El ácido desoxirribonucleico (ADN) es una sustancia química que se encuentra en el núcleo de las células y lleva las "instrucciones" para el desarrollo y funcionamiento de los organismos vivos.

En las cadenas de ADN, los símbolos "A" y "T" son complementarios entre sí, como "C" y "G". Su función recibe un lado del ADN (cadena, excepto Haskell); necesitas devolver el otro lado complementario. La cadena de ADN nunca está vacía o no hay ADN en absoluto (nuevamente, excepto en Haskell).

Example: (input --> output)

```

"ATTGC" --> "TAACG"

"GTAT" --> "CATA"

```

  

### 1- Usando IFs
```python
def DNA_strand(dna):
    nueva_cadena=""
    for j in dna:
        if j == "A":
            nueva_cadena+="T"
        elif j== "T":
            nueva_cadena+="A"
        elif j== "C":
            nueva_cadena+="G"
        elif j== "G":
            nueva_cadena+="C"
  
    return nueva_cadena
```

  

### 2- Usando replace()
```python
def DNA_strand(dna):
    nueva_cadena=""
    nueva_cadena=dna.replace("A","#")
    nueva_cadena=nueva_cadena.replace("T","A")
    nueva_cadena=nueva_cadena.replace("#","T")
  
    nueva_cadena=nueva_cadena.replace("C","#")
    nueva_cadena=nueva_cadena.replace("G","C")
    nueva_cadena=nueva_cadena.replace("#","G")
    return nueva_cadena
```

  

### 3- Usando maketras() y translate()
```python
import string
def DNA_strand(dna):
    return dna.translate(string.maketrans("ATCG","TAGC"))
```

  

### 4- Usando un diccionario i .join
```python
pairs = {'A':'T','T':'A','C':'G','G':'C'}
def DNA_strand(dna):
    return ''.join([pairs[x] for x in dna])
```



  ### SOLUCIÓN
```python
print(DNA_strand("ATTGC"))
print(DNA_strand("GTAT"))
```

    TAACG
    CATA

___
## 21- ¿La cadena termina con?
Complete la solución para que devuelva verdadero si el primer argumento (cadena) pasado termina con el segundo argumento (también una cadena).
  
Ejemplos:

```
solution('abc', 'bc') # returns true
solution('abc', 'd') # returns false
```

  
  

### 1- Con if de forma básica

```python
def solution(text, ending):
    conteo_ending = len(ending)
    if text[(-conteo_ending):] == ending:
        return True
    else:
        return False
```

  

### 2- Igual pero haciendo el código por compresión

```python

def solution(text, ending):

    return True if text[-len(ending):] == ending else False

```

  

### 3- Usando el método .endswith()

```python
def solution(text, ending):
    return text.endswith(ending)
```

  

### 4- Comparación con in

```python
def solution(string, ending):
    return ending in string[-len(ending):]
```

  

### 5- Con lambda

```python
solution = lambda s,e: not e or s[-len(e):] == e
```


### SOLUCIÓN

```python
print(solution("abc","bc"))
print(solution("abc","d"))
```

    True
    False


___
## 22- Eliminar vocales de String

Los trolls están atacando tu sección de comentarios.

Una forma común de lidiar con esta situación es eliminar todas las vocales de los comentarios de los trolls, neutralizando la amenaza.

Tu tarea es escribir una función que tome una cadena y devuelva una nueva cadena con todas las vocales eliminadas.

Por ejemplo, la cadena "This website is for losers LOL!" se convertiría en "Ths wbst s fr lsrs LL!".

Nota: para este kata, la 'y' no se considera una vocal.

### 1- Usando un ciclo for y un condicional if

```python
def disemvowel(string_):
    vocales = ["a","e","i","o","u"]
    nuevo_string=""
    for caracter in string_:
        if caracter.lower() not in vocales:
            nuevo_string+=caracter
    return nuevo_string
```

  

### 2- Igual pero con una lista por compresion y join
```python
def disemvowel(string_):
    vocales = ["a", "e", "i", "o", "u"]
    return ''.join([caracter for caracter in string_ if caracter.lower() not in vocales])
```

  

### 3- Con replace
```python
def disemvowel(s):
    for i in "aeiouAEIOU":
        s = s.replace(i,'')
    return s
```


### 4- Con expresiones regulares
```python
import re
def disemvowel(string):
    return re.sub('[aeiou]', '', string, flags = re.IGNORECASE)
```

  

### 5- Con translate
```python
def disemvowel(string):
    return string.translate(None, 'aAeEuUoOiI')
```

  

### CONSOLA
```python
print(disemvowel("This website is for losers LOL!"))
```
    Ths wbst s fr lsrs LL!





Para validar un PIN con una expresión regular en Python, puedes usar el módulo `re`. Aquí tienes un ejemplo de cómo hacerlo:

```python
import re

def validate_pin(pin):
    return bool(re.fullmatch(r'^\d{4}$|^\d{6}$', pin))

print(validate_pin("1234"))  # Debería devolver True
print(validate_pin("12345"))  # Debería devolver False
print(validate_pin("a123"))  # Debería devolver False
```

Explicación de la expresión regular `r'^\d{4}$|^\d{6}$'`:

- `^` y `$` son anclas que indican el inicio y el final de la cadena, respectivamente.
- `\d` representa cualquier dígito del 0 al 9.
- `{4}` y `{6}` indican que queremos exactamente 4 o 6 dígitos.
- `|` es el operador OR, que permite coincidir con 4 o 6 dígitos.

La función `re.fullmatch()` verificará si toda la cadena coincide con la expresión regular. Retorna un objeto de coincidencia si encuentra una coincidencia y `None` en caso contrario. Utilizamos `bool()` para convertir el resultado a un valor booleano (`True` o `False`).














___

%%
tags:  #programación #pagfundamentospython #python 

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%