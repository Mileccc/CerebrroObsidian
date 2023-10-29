---
ID: 130
"tags:": 
nombre: Expresiones regulares (Regex)
---
___
# Expresiones regulares (Regex)
___
## 1- Pildorasinformaticas 
### 1.1- Funciones básicas
![](https://www.youtube.com/watch?v=qpwn3gRtxCo)

- **search()** ---> Busca un texto en una cadena, 1º arg texto a buscar, 2º arg cadena donde buscar.
- **start()** ---> número de índice donde empieza el texto
- **end()**   ---> número de índice donde acaba el texto
- **span()** ---> Devuelve una tupla con la posición inicial y final del texto encontrado
- **findall()** ---> Devuelve una lista con todas las coincidencias repetidas en la cadena

___
### 1.2- Metacaracteres
#### Anclas

![](https://www.youtube.com/watch?v=V8316ao08tQ)

- ``^`` Marca si se pone al inicio de una palabra que devolvera todo lo que comience por lo indicado
- ``$`` Lo mismo que el anterior pero devolvera aquellas palabras que terminen con lo indicado

#### Clases de caracteres
- ``[]`` Los caracteres que se coloque dentro serán patrones de búsqueda en un texto.

___
### 1.3- Rangos
![](https://www.youtube.com/watch?v=Q4vXCQd1zwc)

- ``[a-z]`` Devuelve todas las palabras que contengan los caracteres comprendidos en el rango entre los 2 caracteres alrededor del guion ( distingue entre mayus y minus)
- ``[^a-z]`` Si delante de un rango usamos ``^`` negará el rango indicado

___
### 1.4- match y search
![](https://www.youtube.com/watch?v=u3WBRgpxQcc)

- **match()**:  Busca coincidencias siempre al comienzo de una cadena de texto
    - Comodín ``.`` --->  Se usa para que pueda contener cualquier caracter en la posición del punto.
```python
re.match(".ara",nombre, re.IGNORECASE)
```
 - ``\d`` ---> Para saber si comienza por un número
```python
re.match("\d", cadena)
```

- **search()**: A diferencia de match() busca en toda la cadena de texto y no solo al principio



















___
























___

%%
tags:  #programación #pagfundamentospython #python  

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%