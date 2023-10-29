---
ID:: 090
tags::  #programación #pagfundamentospython #python  #input #output #txt #abrir_archivo #leer_archivo
nombre:: "Input Output"
---
___
# Input Output

![](https://youtu.be/EVZ7HRUBDc4?t=2855)
___
Ahora veremos como abrir archivos usando Python base. Para hacerlo usaremos la sentencia **with** para definir un **contexto** del siguiente modo:

![[Pasted image 20230815184127.png]]

Lo que significa: con el archivo "corpus.txt" abierto en **modo** lectura ("r" de read) con el **alias** _inp_, definimos la variable contenido usando el método **.read()** para leer el archivo. Algunas aclaraciones:

- El método .read() es propio del objeto de input, que **en esta ocasión** llamamos _inp_. Otro método útil es **.readlines()** que nos permite iterar por renglones.
- La ruta al archivo puede ser **relativa** como en este caso, donde el archivo se encontraría en la misma carpeta que la notebook. También se puede dar el path completo, como podría ser "C:/Usuarios/Matías/Documentos/corpus.txt"

Existen varios modos de abrir un archivo, incluyendo:

![[Pasted image 20230815184301.png]]

Por ejemplo, para escribir en un archivo, haríamos:
![[Pasted image 20230815184326.png]]

![[Pasted image 20230815184411.png]]

![[Pasted image 20230815184433.png]]

En Python se puede pedir un input del usuario de la siguiente manera:

![[Pasted image 20230815184608.png]]


___

%%
tags:  #programación #pagfundamentospython #python   #input #output #txt #abrir_archivo #leer_archivo

Vínculos:    [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%