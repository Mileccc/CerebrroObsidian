---
ID:: 016
-nombre:: "Tipos de valores en las fórmulas de Notion"
-tags:: #notion #guia #pagnotion  #fórmula  #datos #tipos #date #boolean #string #number #function
---
___
# Tipos de valores en  Notion
Cuando trabajemos con fórmulas, tendremos que tener presentes los tipos de valores que podemos usar con ellas. En los ejemplos anteriores hemos visto la mayoría, como son **números**, **texto** o **valores true/false**, pero ahora haremos un repaso general de todos los que podemos usar.

## Números

Un valor numérico, que puede ser íntegro o contener decimales, y tanto positivo como negativo. Los valores dentro de la propiedad `Number` en Notion son de tipo numérico, por lo que cuando hagamos referencia a esa propiedad en una función, tendremos que tener en cuenta que nos devolverá un valor **numérico**.

### Convertir un valor numérico a una cadena de texto → `format()`

Si lo que necesitamos es que un número sea interpretado como una **cadena de texto**, podremos convertirlo usando la función `format()`.

Si por ejemplo quisiéramos crear un campo que indique la edad, seguido del número de años, tendríamos que concatenar ambos valores con la función `add()`. El problema es que uno es de tipo **texto** y el otro de tipo **numérico**, por lo que tendríamos que convertir el número en una cadena de texto. Nuestra fórmula quedaría así:

`add("Edad: ", format(prop("Edad")))`

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/90b952bb-4a9d-4a47-9a36-0fb64e36d16a/07._edad/w=3840,quality=80)

## Cadenas de texto (string)

Un **string** o **cadena de texto** es uno o más caracteres que representan texto.

Puesto que en Notion puedes escribir números tanto en una propiedad de `Texto` como en una propiedad de `Number`, dependiendo de donde introduzcas esas cifras serán interpretadas como **texto** (si están en una propiedad `Text`) o como **número** (si están en una propiedad `Number`)

Esto puede llevar a confusiones o a que tus fórmulas no se ejecuten correctamente. Para evitarlo, asegúrate de que siempre que introduzcas caracteres numéricos, lo hagas en la propiedad `Number` ya que haciéndolo en una de `Text` te impedirá usarlos en ningún cálculo.

Cuando vayas a usar una cadena de texto o **string** en una fórmula, recuerda introducir siempre los caracteres entre comillas para que sean interpretados como cadenas de texto. Así, `"26"` es un **string**, mientras que `26` es un **número.**

### Convertir una cadena de texto a un número

En otras ocasiones, es posible que lo que necesites sea convertir una propiedad de tipo **texto** en una **numérica**, porque por ejemplo necesites hacer cálculos y que ambas propiedades sean de tipo numérico. Para eso existe la función `toNumber()` que, como bien indica, convierte cadenas de texto en número.

`toNumber("2")` → `2`

Así, para sumar una propiedad numérica y una de texto, deberíamos hacer:

`2 + toNumber("2")` → `4`

## Booleanos (valores de `true` o `false`)

Un valor de los conocidos como tipo `boolean` o booleanos son valores que sólo pueden ser **true** o **false**. Como vimos en la sección de **Condicionales** con la formula `if()`, cuando usamos **operadores de comparación** para comprobar si se cumple una condición, el valor que nos devolverá esta fórmula será de este tipo.

En Notion, los valores booleanos se representan como **checkbox** en nuestras bases de datos. Es decir, si nuestra fórmula devuelve un valor booleano, en ese campo se mostrará como un checkbox. Marcado si el valor es **true**, desmarcado si el valor es **false**.

Para entenderlo, un pequeño ejemplo:

Pongamos que queremos comprobar si el precio total de alguno de los items que queremos comprar está en nuestro presupuesto, que es de 20€.

Usaríamos la fórmula que ya usamos previamente, que nos devolvía el precio total de los items y, con un operador de comprobación, comprobaríamos si este precio es de 20 o menos. Si lo es, se marcará como dentro de nuestro presupuesto:

**Precio total:** `add(prop("Precio"), multiply(prop("Precio"), prop("IVA")))`

**En presupuesto?**: `if(prop("Precio total") <= 20, true, false)`

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0708a3e4-3d37-4688-8962-887a63afd8b3/08._en_presupuesto/w=3840,quality=80)

## Date

Como hemos visto en otras lecciones, el valor `date` se crea siempre que uses una propiedad de `Date`, ya sea esta misma o las otras dos propiedades que incluyen fecha como `Created Time` o `Last Edited Time`

Todas estas propiedades también podrán ser utilizadas como **argumentos** de funciones en una fórmula. Adicionalmente, escribiendo en un campo de fórmula la función `now()`, nos devolverá la fecha y hora exactas.


___

Links:

%%
Vínculos:
[[000-Menú Notion📃|Menú Notion]] ,  [[014-Introducción a las Fórmulas en Notion|Introducción a las Fórmulas en Notion]]

tags:
#notion #guia #pagnotion  #fórmula  #datos #tipos #date #boolean #string #number #function
%%