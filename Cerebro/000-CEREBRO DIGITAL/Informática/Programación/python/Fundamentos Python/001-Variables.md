---
ID:: 001
tags:: #programación #pagfundamentospython #python   #variables #booleano #numérico #operadores #string #slicing #formateo #split
nombre:: "Variables"
---

___

# Curso Humai Python

![](https://youtu.be/-yqL1VUYvrw?t=543)


## Declarando variables

---

Existen distintos tipos de variables:

- **int**: entero
- **float**: punto flotante
- **string**: cadena de caracteres
- **bool**: booleano, 0, 1, True o False

Y estructuras de datos, como:

- **list**: lista de elementos (de cualquier tipo, incluida otra lista)
- **dict**: "diccionario", conjunto de pares llave:valor

Veamos un primer ejemplo:

![[Pasted image 20230811101309.png|400]]
### Numéricos

---

Declaramos dos variables de tipo numérico:
![[Pasted image 20230811101446.png]]
![[Pasted image 20230811101504.png]]

#### Operaciones numéricas - Divisiones

Devuelve la división:
![[Pasted image 20230811101722.png]]
Devuelve la parte entera de la división:
![[Pasted image 20230811101739.png]]

Devuelve el resto:
![[Pasted image 20230811101819.png]]

Otros ejemplos:
![[Pasted image 20230811101847.png]]
La **función** _type_ recibe de **argumento** una **variable** y **devuelve** su tipo:
![[Pasted image 20230811101920.png]]

Intentemos la siguiente suma...
![[Pasted image 20230811101953.png]]

Si **convertimos** el string "10" a tipo int:
![[Pasted image 20230811102045.png]]

Cada tipo de variable responde a ciertos **métodos**. Veamos las operaciones lógicas, que utilizan **booleanos**
### Booleanos
True , False

---

### Strings
Podemos acceder a ellos mediante **índices**. Los mismos funcionan para cualquier **iterable**, que es un objeto con muchos elementos que son accesibles secuencialmente. Podemos usar los índices para acceder a una posición determinada, pasándola entre corchetes \[posición]. Es IMPORTANTE mencionar que en Python la primera posición tiene el índice 0 (y no 1).
![[Pasted image 20230811104810.png]]
![[Pasted image 20230811104825.png]]

También podemos usar los índices para traer más de un elemento al mismo tiempo, usando el **slicing**. El slicing lleva tres parámetros: comienzo (start), final (stop) e intervalo o paso (step).

- El parámetro comienzo (start) indica la primera posición incluida en la selección, por default es 0.
    
- El parámetro final (stop) es la primera posición que NO va a estar incluída, por default se incluyen todos los elementos.
    
- El parámetro intervalo o paso (step), es optativo e indica el tamaño del paso entre seleccionar un elemento y el siguiente, por default el paso es 1. El paso también puede ser negativo, en este caso contamos desde el final hacia el comienzo, esto es muy útil para dar vuelta los strings...

```
[comienzo : final : intervalo] (en inglés es [start : stop : step] )
```
![[Pasted image 20230811105051.png]]
![[Pasted image 20230811105330.png]]

#### Algunos métodos de los strings
![[Pasted image 20230811105438.png]]
![[Pasted image 20230811105759.png]]


#### Formateo de variables
![[Pasted image 20230811105623.png]]



##### Ejercicios

1- Concatenar los string "hola" y "qué tal", separando ambos strings con un espacio (Tip: un espacio es: " ")
![[Pasted image 20230811110410.png]]
2- Guardar el resultado anterior en una variable y pasar el texto a mayúsculas.
![[Pasted image 20230811110422.png]]





___
%%
tags: #programación #pagfundamentospython #python   #variables #booleano #numérico #operadores #string #slicing #formateo #split

Vínculos:  [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python]]
%%

> [!failure]- Failure 
>   Error: You exceeded your current quota, please check your plan and billing det  ails.
>  

> [!failure]- Failure 
>   Error: You exceeded your current quota, please check your plan and billing det  ails.
>  

> [!failure]- Failure 
>   Error: You exceeded your current quota, please check your plan and billing det  ails.
>  

> [!failure]- Failure 
>   Error: You exceeded your current quota, please check your plan and billing det  ails.
>  

> [!failure]- Failure 
>   Error: You exceeded your current quota, please check your plan and billing det  ails.
>  

> [!failure]- Failure 
>   Error: You exceeded your current quota, please check your plan and billing det  ails.
>  
