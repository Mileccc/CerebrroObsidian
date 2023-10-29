---
ID:: 030
tags:: #programación #pagfundamentospython #python   #diccionarios #values #dict #keys #items 
nombre:: "Diccionarios"
---
___
# Diccionarios
![](https://youtu.be/-yqL1VUYvrw?t=2975)


Los diccionarios consisten en estructuras que contienen pares de una **llave** y un **valor**. Los elementos NO están ordenados, con lo cual no se puede acceder por posición ni slicing.

Veamos un ejemplo:
![[Pasted image 20230812190450.png]]

Sin embargo, sí podemos acceder a un elemento por su llave. Accedemos al valor de "Abraham"
![[Pasted image 20230812190517.png]]

¿Qué pasa si tratamos un diccionario como una lista?
![[Pasted image 20230812190547.png]]

Tenemos un error, tratemos de interpretarlo: KeyError se refiere a que no existe una llave (Key) a la que se trató de acceder. En este caso la llave que se trató de acceder es 0.


### Métodos de los diccionarios

Traer todo el diccionario
```python
print(diccionario) 
```

```python
{'Pedro': 20, 'Martin': 24, 'Sofia': 32, 'Jaimito': 19}
```


___
Traer un objeto tipo dict con solamente las claves
```python
print(diccionario.keys())
```

```python
dict_keys(['Pedro', 'Martin', 'Sofia', 'Jaimito'])
```


___  

Traer un objeto tipo dict con solamente los valores
```python
diccionario.values() 
```

```python
dict_values([20, 24, 32, 19])
```


___
  
Trae un objeto tipo dict con todo , a diferencia de llamar al diccionario sin método no
devuelve un diccionario , si no un objeto de tipo dict con una lista de tuplas
```python
diccionario.items() 
```

```python
dict_items([('Pedro', 20), ('Martin', 24), ('Sofia', 32), ('Jaimito', 19)])
```


___


Y utilizar los mismos métodos para borrar y extraer como en las listas:
![[Pasted image 20230812190935.png]]

Los diccionarios tienen longitud, de la misma forma que las listas y string:
![[Pasted image 20230812191014.png]]



___

%%
tags:  #programación #pagfundamentospython #python   #diccionarios #values #dict #keys #items 
Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%