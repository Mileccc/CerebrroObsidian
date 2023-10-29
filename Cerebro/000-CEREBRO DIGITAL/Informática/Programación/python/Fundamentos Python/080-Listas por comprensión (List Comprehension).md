---
ID:: 080
tags:: #programación #pagfundamentospython #python   #comprensión #listas_por_comprensión

nombre:: "Listas por comprensión (List Comprehension)"
---
___
# Listas por comprensión (List Comprehension)
![](https://youtu.be/EVZ7HRUBDc4?t=2250)
___
Las **listas por comprensión** son una funcionalidad muy flexible de Python que permite crear listas de un modo más "descriptivo", basandose en la notación de definición de conjuntos.

---

Supongamos que necesitamos obtener una lista con los elementos de una lista original elevados al cuadrado.

Sin listas por comprensión haríamos...

![[Pasted image 20230814232401.png]]

En cambio, con listas por comprensión usamos esta expresión:

![[Pasted image 20230814232423.png]]

En las listas por comprensión también podemos incluir condicionales en una sola línea, vean la siguiente expresión:

![[Pasted image 20230814232442.png]]

![[Pasted image 20230814232458.png]]

Ahora vamos a generar una lista por comprensión sólo con los números donde el cuadrado sea menor a 15

![[Pasted image 20230814232521.png]]


La sintáxis para **filtrar** con condicionales es:

```
[(elemento) ( for x in (iterable) ) ( if condicion )]
```

Donde "elemento" es lo que vayamos a guardar en la lista. Incluyendo un **else**:


```
[(elemento) (if condicion else otro_elemento) ( for x in (iterable) )] 
```

Pueden hacerse loops anidados:

```
[i for i in range(x) for j in range(y)]
```


---

Otra forma de pensar la sintaxis es a partir de teoría de conjuntos. Por ejemplo: Un conjunto S definido por todos los números X / 4 que pertenecen a los Naturales y cumplen que su cuadrado es menor a 20
![[Pasted image 20230814232904.png]]

Con un loop for:

![[Pasted image 20230814232925.png]]

Con listas por comprensión:

![[Pasted image 20230814233001.png]]

![[Pasted image 20230814233021.png]]

![[Pasted image 20230814233036.png]]

O comprensiones anidadas:

```
[ [i for i in range(x) ] for j in range(y) ]
```

![[Pasted image 20230814233140.png]]

Además, el elemento que se genera puede ser de otro tipo, en este caso una tupla:

![[Pasted image 20230814233208.png]]



___

%%
tags:  #programación #pagfundamentospython #python   #comprensión #listas_por_comprensión

Vínculos:    [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%