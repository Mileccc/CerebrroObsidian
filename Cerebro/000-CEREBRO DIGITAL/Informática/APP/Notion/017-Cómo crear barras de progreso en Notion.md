---
ID:: 017
-nombre:: "Cómo crear barras de progreso en Notion"
-tags:: #notion #guia #pagnotion  #if_comprimido #barra_de_progreso #funciones #slice
---
___
# Cómo crear barras de progreso en Notion
Para crear nuestras barras de progreso en Notion, necesitaremos un par de cosas:

1. Mínimo dos bases de datos relacionadas entre sí. Usaremos esta relación para sacar el porcentaje de tareas asociadas a un proyecto que estén completadas. Gracias a este porcentaje, podremos luego "pintar" nuestra barra de progreso. Aquí es donde entra el segundo elemento:
2. Funciones. Para que funcione la barra de progreso, vamos a necesitar 4 funciones diferentes, que te explico a continuación: `if()` como condicional, `slice()` para pintar la barra, `round()`para redondear las cifras y `format()` para convertir números a cadenas de texto. Te las explico todas a continuación 👇🏻

## if()

Con if() lo que hacemos es comprobar si se cumple una condición concreta. Para que funcione, necesitaremos tres argumentos:

1. Una [[015-Expresiones y condiciones anidadas|Expresiones y condiciones anidadas]] que comprueba si determinado valor es cierto (`true`) o falso (`false`). Para evaluar esto, normalmente nos valdremos de [[014-Introducción a las Fórmulas en Notion#Operadores de comparación|Operadores de comparación]]
2. El valor que queremos que nos devuelva si el resultado de esta comprobación es `true`.
3. El valor que queremos que nos devuelva si el resultado de esta comprobación es `false`.

`[comparación] ? [que ocurre si es true] : [que ocurre si es false]`

```javascript
(prop("Completadas") >= 1) ? "✅" : (----------)
```

## slice()

La función slice() nos devuelve el segmento que le indiquemos de un string que le hayamos introducido previamente. Coge tres argumentos:

1. El string original
2. El punto de origen, siendo el primer carácter 0
3. El punto final (opcional)

Ejemplo:

`slice("manzana, pera, sandía, kiwi", 9, 21)` → `pera, sandía`

(Ha contado el número de caracteres, empezando de 0 hasta llegar al número 9 (p) y, a partir de ese, ha cogido todos los que había entre el número 9 y el 21 (a)

Usaremos esta función doblemente.

1. Primero para que **se vaya pintando la barra de progreso rellena** en función del porcentaje completado
2. Después, **a esa parte rellena le sumaremos la parte que esté vacía**, usando de nuevo la función para indicarle cuánto de vacía tiene que estar (restándole el porcentaje completado)

### round()

Esta función redondea un numero decimal a su íntegro más cercano

Ejemplo: `round(1.3)` → `1`

### format()

Esta función convierte un número `number` en un texto `string`

Ejemplo: `format(20)` → `"20"`

Recuerda que, en ocasiones, necesitaremos que **un número sea interpretado como texto** para poder hacer cosas especiales como **concatenar cadenas de texto**. En este caso, necesitaremos concatenar **una cifra con un símbolo %** y, para eso, necesitamos que ambas sean cadenas de texto. De ahí que vayamos a usar esta función.

## Elegir los caracteres que darán "vida" a nuestra barra de progreso

- Completado → █
- Sin completar → ░

Necesitas **ambos estados** para que la fórmula funcione ya que a uno le "asignaremos" un porcentaje de tareas completadas 0% (░)y, al otro, 100% (█).

## Crear la barra de progreso paso a paso

Una vez tenemos todos nuestros elementos bien configurados, que —te recuerdo— son los siguientes:

- Dos bases de datos relacionadas entre sí y con una propiedad de `Rollup` en una de ellas que coja el **porcentaje** de acciones completadas de la otra. Esto nos dará el porcentaje necesario para realizar nuestra fórmula. En este ejemplo yo llamo a ese campo " **Completadas**"
- Nuestros caracteres elegidos.

La fórmula al completo es esta:

```javascript
(prop("Completadas") >= 1) ? "✅" : (slice("▓▓▓▓▓▓▓▓▓▓", 0, round(prop("Completadas") * 10)) + slice("░░░░░░░░░░", 0, round((1 - prop("Completadas")) * 10)) + " " + if(prop("Completadas") == 0, "0", format(round(prop("Completadas") * 100))) + "%")
```

Y ahora iremos desmenuzándola para entender lo que hace cada cosa:

### **Qué ocurre si el porcentaje es del 100% → check (**✅**)**

En primer lugar tenemos un condicional que comprueba que **el valor del campo "Completadas" es mayor o igual a 1** ( 1 = 100% || 0,5 = 50% etc).

Si es así (es decir, si el porcentaje de Completadas es del 100%) le diremos que nos muestre un check (✅).

```javascript
(prop("Completadas") >= 1) ? "✅" : (----------)
```

### **Qué ocurre si el porcentaje es menor al 100% → barra de progreso**

Si no se cumple esa condición (es decir, que el porcentaje de acciones completadas sea menor del 100% y, por lo tanto, no haya llegado a 1) le damos una instrucción, que será la de que pinte la barra de progreso. Esta instrucción se compone de dos partes, ya que por un lado tendrá que pintar la parte rellena y, a continuación, **concatenarle** la parte vacía.

**Pintando la parte rellena de la barra**

Para representar la parte rellena del progreso tenemos la siguiente parte de la fórmula:

`(slice("▓▓▓▓▓▓▓▓▓▓", 0, round(prop("Completadas") * 10))`

Usamos la funcion **slide()**, indicándole que el string inicial es `▓▓▓▓▓▓▓▓▓▓`

El punto inicial es **0** (es decir, el principio del string)

El punto final es una expresión. Por un lado estamos **multiplicando el porcentaje por 10 para que nos de un número decimal entre 1 y 10**. A ese resultado, le aplicaremos la función round() para que nos lo redondee.

Lo que estamos diciendo es: "del string `▓▓▓▓▓▓▓▓▓▓`, quiero que me pintes desde el carácter 0 hasta el carácter que sea el resultado de **multiplicar el porcentaje de tareas completadas**  **10** .

`80%` → `8` 
`33%` → `3`

...etc

**Pintando la parte vacía de la barra**

Para representar la parte vacía de la barra usaremos la siguiente parte de la fórmula:

`slice("░░░░░░░░░░", 0, round((1 - prop("Completadas")) * 10)) +`

En este caso, estaremos haciendo exactamente lo mismo que para ver la parte rellena pero, en este caso, el punto final del string vendrá dado por el resultado de **restar el porcentaje de tareas completadas a 1**. Es decir, si tenemos un 80% de tareas completadas, el resultado de esta expresión nos daría -7 (1-8)

Esto básicamente lo que hace es sacar la parte no rellena y pintarla.

Ahora lo que tenemos que hacer es "**pegar**" la parte rellena a la parte no rellena, para lo que necesitaremos **concatenarlas**. Esto lo hacemos simplemente añadiendo ese símbolo de `+` al final.

Ya tenemos nuestra barra de progreso completada, pero solo muestra la representación visual. Para que podamos ver también cómo se traduce eso en un porcentaje numérico, necesitaremos un par de cosas más.

**Mostrar el porcentaje en números**

Puesto que, como recordamos, los caracteres que forman la barra de progreso son un `string`, necesitaremos que el resto del porcentaje sea también un string para poder concatenarlos. Para esto, escribiremos esta última linea:

```javascript
" " + if(prop("Completadas") == 0, "0", format(round(prop("Completadas") * 100))) + "%")
```

Fíjate primero en el **if()**. Aquí lo que decimos es que si "Completadas" es 0 (es decir, que no hayamos realizado ninguna acción aún) nos aparezca un número 0.

Si no:

- **Multiplica el porcentaje por 100** para que devuelva un número entre **1 y 100** (esto es nuestro porcentaje final)
- Usa la función **round()** para eliminar cualquier decimal de más que se genere.
- Convierte todo lo anterior a una cadena de texto `string` con la funcion **format()**
- Finalmente, con el operador `+` añadimos el último carácter, el símbolo `%`.

Antes de eso, verás que hay una cadena de texto vacía `" "`. Esto básicamente lo que hace es generar el espacio entre la barra de progreso y el porcentaje.



![](https://www.youtube.com/watch?v=gNcAJhuLrZU)

___

Links:

%%
Vínculos:
[[000-Menú Notion📃|Menú Notion]] , [[015-Expresiones y condiciones anidadas|Expresiones y condiciones anidadas]], [[014-Introducción a las Fórmulas en Notion|Introducción a las Fórmulas en Notion]]

tags:
#notion #guia #pagnotion  #if_comprimido #barra_de_progreso #funciones #slice
%%