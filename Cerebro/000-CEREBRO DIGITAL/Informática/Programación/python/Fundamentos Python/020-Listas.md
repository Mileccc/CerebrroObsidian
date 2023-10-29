---
ID:: 020
tags:: #programación #pagfundamentospython #python  #listas
nombre:: "Listas"
---
___

# Listas

![](https://youtu.be/-yqL1VUYvrw?t=2232)

Las listas son un conjunto de elementos ordenados. Estos elementos pueden ser de cualquier tipo, incluyendo otras listas. Veamos algunas operaciones con ellas.

![[Pasted image 20230811110611.png]]

### Indexing y slicing en listas
De la misma forma que con los strings en el contexto de la listas generalmente hablamos de **indexación** o acceso por índice a la acción de encontrar un valor según su posición en la lista.

Importantísimo (sí, ¡una vez más!): En Python el primer elemento se indexa con el valor 0. Es decir, si queremos el primer valor de una lista tenemos que llamar a la posición 0.
![[Pasted image 20230811110713.png]]

Además, el último elemento se indexa como -1, el siguiente -2 y así sucesivamente. Entonces para acceder al último elemento:
![[Pasted image 20230811110736.png]]

Además, podemos acceder a varios elementos en simultáneo, usando el **slicing** de la misma manera que con strings.

El slicing aplicado a una lista nos devuelve una **lista**.

Veamos algunos ejemplos:
![[Pasted image 20230811110814.png]]


### Otras operaciones y métodos

---

Agregar un nuevo elemento:
![[Pasted image 20230812184005.png]]

Sumamos otra lista:
![[Pasted image 20230812184053.png]]

Unir una lista con un separador dado:
![[Pasted image 20230812184154.png]]

El ejercicio 1 se podría haber resuelto usando .join así:

![[Pasted image 20230812184317.png]]

Borrado por valor:
![[Pasted image 20230812184400.png]]

Borrado por índice:
![[Pasted image 20230812184424.png]]


Devuelve un elemento y lo borra de la lista:
![[Pasted image 20230812184530.png]]


**Cantidad** de apariciones:
![[Pasted image 20230812184627.png]]

![[Pasted image 20230812184640.png]]

Largo de la lista:
![[Pasted image 20230812184719.png]]

Ordenar la lista:
![[Pasted image 20230812184749.png]]

Sumar el total:
![[Pasted image 20230812184815.png]]

Mínimo & Máximo:

![[Pasted image 20230812184854.png]]
![[Pasted image 20230812184907.png]]


Calcular el promedio de edad de la lista "edades":
![[Pasted image 20230812185534.png]]




___

%%
tags:  #programación #pagfundamentospython #python   #listas

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python]]
%%