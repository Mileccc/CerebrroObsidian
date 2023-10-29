---
ID:: 015
-nombre:: "Expresiones y condiciones anidadas"
-tags:: #notion #guia #pagnotion  #fórmula #condicional #anidados
---
___
# Expresiones y condiciones anidadas

## Anidar inputs, operadores y funciones

Es muy normal que en nuestras fórmulas usemos **funciones**, **operadores** e **input values** dentro de otras funciones. Esto se conoce como anidado o **nesting**.

Cuando combinamos inputs, operadores y/o funciones de manera que devuelvan un sólo valor, se conoce como **expresión**. Las expresiones pueden ser tan sencillas o complejas como queramos, siempre y cuando devuelvan un sólo valor.

Esto implica que los argumentos de una **función** (recuerda, es valores que introducíamos entre los paréntesis) no tienen por qué ser sólo una referencia a una **propiedad** o un **valor literal**, como decíamos arriba; **cualquier expresión puede ser a su vez un argumento** siempre y cuando devuelva un valor único y éste sea del tipo correcto.

Por ejemplo, la sencilla fórmula `add(100, 20)` nos devolverá el resultado de sumar 100 y 20.

Pero podríamos convertirla en una expresión más complicada:

`add(100, mutiply (10,2))`

En este caso, el segundo argumento es el resultado de una **función**; la función `mutiply()` a la que hemos pasado como argumentos `10` y `2`, para que los multiplique.

Ambas operaciones darán como resultado lo mismo: `120`.

Un ejemplo algo más complicado, por ejemplo, lo encontraríamos al introducir como valores las referencias a otras propiedades:

Si quisiéramos, por ejemplo, calcular el precio total de un ítem aplicándole un IVA diferente, haríamos lo siguiente:

`add(prop("Precio"),multiply(prop("Precio"),prop("IVA")))`

En el que, primero, multiplicaríamos el Precio por el IVA → `multiply(prop("Precio"), prop("IVA"))`

y, ese resultado, lo sumaríamos al Precio → `add(prop("Precio"),multiply(prop("Precio"),prop("IVA")))`

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/29ea951a-7e62-4a67-975f-cd9c68aeb761/03._precio_con_iva/w=3840,quality=80)

## Condiciones anidadas

El fenómeno de anidado lo encontraremos sobre todo con las funciones de tipo `if()`. Es decir, las funciones que nos sirven para comprobar si se cumple una condición o no. Si se cumple, veremos el segundo argumento y, si no, veremos el tercero:

`if( 2 == 1, "Igual", "No es igual" )` → `"No es igual"`

Pero lo más frecuente es que lo que queramos sea que nos devuelva uno u otro resultado dependiendo del primer argumento.

Un uso muy común de este tipo de estructuras sería el de marcar como check una propiedad si esta se encuentra en estado "Completado"

`if(prop("Status") == "completada", true, false)`

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/07c8ad1f-2893-43d3-8cc2-5f956d91bb2a/04._tareas_completadas/w=3840,quality=80)

También podemos usar las funciones `and()` y `or()` para comprobar dos expresiones diferentes y si ambas se cumplen.

Por ejemplo, en la fórmula de abajo estaríamos comprobando si un producto está tanto "Pagado" como "Enviado", en cuyo caso aparecería como "Completado". En caso contrario, el mensaje que aparecería sería "En progreso"

`if(and(prop("Pagado"), prop("Enviado")), "Completado", "En Progreso")`

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/91caf1ac-82b1-470d-950b-f2eadd8d9478/05._estado_final/w=3840,quality=80)

Por último, es posible que a veces queramos mayor granularidad que un **true** o **false**, sino poder hacer diferentes cosas si más condiciones se cumplen.

Por ejemplo, podríamos comprobar si el estado de ánimo de cada día es "feliz", "apático" o "infeliz" y que nos represente con un emoji cada uno de ellos:

`if(prop("Mood") == "feliz", "😀", if(prop("Mood") == "apático", "😕", "😩"))`

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1a4c05b3-4145-4861-8b4a-592e0535df19/06._moods/w=3840,quality=80)

Esto se traduciría en:

Si "`Mood`" es "`feliz`", muestra "😀";

Si lo anterior no se cumple, una de dos; si "`Mood`" es "`normal`", muestra "😕"

Si no se cumple ninguna de las anteriores, muestra "😩"



![](https://www.youtube.com/watch?v=kx8Ciyu7jzk)

___

Links:

%%
Vínculos:
[[000-Menú Notion📃|Menú Notion]] , [[008-Hacer cálculos, crear templates y enlazar bases de datos|Hacer cálculos, crear templates y enlazar bases de datos]] , [[014-Introducción a las Fórmulas en Notion|Introducción a las Fórmulas en Notion]]

tags:
#notion #guia #pagnotion  #fórmula #condicional #anidados
%%