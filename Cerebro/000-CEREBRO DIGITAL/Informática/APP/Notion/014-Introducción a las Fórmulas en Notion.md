---
ID:: 014
-nombre:: "Introducción a las Fórmulas en Notion"
-tags:: #notion #guia #pagnotion  #fórmula #condicional 
---
___
# El menú Fórmula

Lo primero que tendremos que hacer para crear una fórmula será añadir, en nuestra base de datos, una nueva propiedad de tipo `Formula`.

Una vez tenemos esta propiedad creada y pinchamos en ese campo, se nos abrirá una ventana con una serie de secciones en el menú lateral. Estas secciones son:

- `Propiedades`. Un listado de todas las propiedades que estén creadas en tu base de datos. Con estas propiedades son con las que jugarás para ir montando tus fórmulas. Si te fijas, al pinchar en cualquiera de estas propiedades, automáticamente se insertarán en la barra destinada a escribir la fórmula, pero con la sintaxis adecuada. Ej: `prop("Fecha")`
- `Constants`: Constantes matemáticas que Notion incluye como _pi_ y _e_. Puedes hacer click en cualquier de ellas y se añadirán automáticamente a tu fórmula.e
- `Operadores`: Cálculos simples para ir añadiendo a tus fórmulas. Notion añade una ayudita visual al lado de cada uno de ellos para que sepas con qué tipo de propiedad funcionan.
- `Funciones`: Las funciones son fórmulas ya predefinidas, más complejas que los `Operadores` pero que nos permitirán realizar más acciones sobre nuestras propiedades.

Una vez sabemos qué hace, más o menos, cada una de estas secciones del menú lateral, vamos a ver cómo creamos nuestras propias fórmulas.

# De qué se compone una fórmula

Lo que viene a continuación toma como referencia, en gran medida, el artículo sobre Fórmulas de William Nutt 

A la hora de crear nuestras propias fórmulas, nos va a ser muy útil antes preguntarnos lo siguiente:

1. _¿Qué queremos hacer?_ Qué **acciones** u operaciones queremos realizar sobre nuestras propiedades. Aquí entran en juego los `Operators` como `add`, `substract` o `multiply`, y las `Functions` como `format`, `join`, etc...
2. _¿A qué queremos hacerlo?_ Los valores (también conocidos como **input values**) a los que queremos aplicar esas fórmulas. Aquí usaremos las `Properties` o, en ocasiones, valores literales (es decir, que escribiremos nosotros mismos)
3. _¿Cuándo queremos hacerlo?_ Las **condiciones** que deben cumplirse para que se desencadene la acción que queremos. Al ser una condición, nos valdremos de `if()` para formularla.
4. Qué hacer si la condición de arriba no se cumple.

Lo más normal será que nuestras fórmulas usen tanto **funciones** como **input values** o **condiciones**, así que vamos a ver una explicación de cada una.

## ¿Qué queremos hacer? → Acciones

Para definir las **acciones** que queremos que tengan lugar en nuestros **input values**, usaremos `Operadores` y `Funciones`

### Operadores

Los operadores pueden ser de 3 tipos, dos de los cuales definen acciones, y un 3º que usaremos para comparar. (Los operadores de comparación los veremos en el 3º paso, las condiciones para saber cuándo queremos que ocurra algo)

**Operadores aritméticos**

Para hacer operaciones matemáticas sencillas como:

- sumar (`+`)
- dividir (`/`)
- restar(`-`)
- multiplicar (`*`)
- calcular un porcentaje (`%`)

**Operadores de concatenación**

Concatenar se refiere a combinar o juntar dos cadenas de texto. En este caso, como hemos visto arriba, el caracter + nos permite juntar dos o más números para que nos de como resultado la suma de todos ellos. Sin embargo, este mismo caracter. situado entre dos cadenas de texto, las combina. Así:

`2 + 2` → `4`

`"Número de items: " + "5"` → `"Número de items: 5"`

👉🏻Al poner un número entre comillas, este deja de ser interpretado como un número y pasa a ser leído como una cadena de texto (a las cadenas de texto, en esta terminología, se las conoce como **strings)**

### Funciones

Las funciones nos ofrecen acciones predefinidas a realizar en una serie de **valores** (a los que llamábamos **input values**), conocidos como **argumentos**. Se declaran de la siguiente manera:

`function()`

Entre esos paréntesis será donde introduzcamos los **argumentos**, separados por comas. Por ejemplo:

`add(2, 2)`

La mayoría de las fórmulas aceptan un número específico de argumentos, aunque algunos son opcionales.

Además, dependiendo de la fórmula requerirá un **tipo de argumento** diferente, como `números` o `cadenas de texto`. Es importante tener esto en cuenta porque a veces puedes tener problemas con una fórmula en la que creas que está todo bien, simplemente porque estás pasándole un argumento del tipo equivocado. Lo veremos más adelante.

## ¿A qué queremos hacerlo? → Input Values

Como hemos visto, las acciones que podemos realizar gracias a los `Operadores` y `Funciones`, las realizaremos sobre una serie de **input values**. También hemos visto que, en el caso de las funciones, estos input values reciben el nombre de **argumentos**.

Estos **input values** pueden ser de 3 tipos; referencias a **Propiedades**, **valores literales** o **constantes**.

### Referencias a Propiedades

En la mayoría de las ocasiones, usaremos los valores las otras propiedades de nuestra base de datos como inputs. Es decir, haremos referencia a los valores de esas propiedades.

Para esto, Notion pone a nuestra disposición la funcion `prop()`. A esta fórmula debes pasarle el argumento, entre paréntesis, del nombre de la propiedad. Por ejemplo, en el caso de que quisiéramos multiplicar el valor de dos propiedades diferentes (**Precio** y **Cantidad**) , deberíamos hacer lo siguiente:

`prop("Precio") * prop("Cantidad")`

Pero si recuerdas, al pinchar en cada propiedad dentro de la ventana de fórmula, automáticamente se escribirá esa propiedad así que no tendrás que escribir todo eso, sino simplemente pulsar en la propiedad sobre la que quieras operar y su valor se rellenará automáticamente.

![image|800](https://assets.super.so/6f476e9c-8680-451e-b108-4cc5c7025a30/images/118cd619-2bbe-4731-aed7-b5a284460a68/funcion_prop().gif?w=1500)

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f9d7dd1f-a4bf-443c-8428-ad8e68dd1056/01._precio_total/w=3840,quality=80)

### Valores literales

En algunos casos, en vez de hacer referencia al valor de una propiedad existente en nuestra base de datos, querremos simplemente usar como argumento un valor fijo, como por ejemplo una **cadena de texto**, con la que operaríamos en cada uno de los registros de esa base de datos.

Por ejemplo, en una base de datos de libros, podríamos crear una propiedad para poder etiquetar cada libro con su autor. Para esto, deberíamos añadir el término "Autor: " a la propiedad de Autor de cada registro:

`add("Autor: ", prop("Autor"))`

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/51f3c682-1fec-4c3f-964c-962d450b29f2/02._autores/w=3840,quality=80)

### Constantes

Como dijimos arriba, Notion incluye referencias a **constantes matemáticas** como _pi_ y _e_ que puede que necesitemos usar en algún momento (aunque lo más probable es que no)

## ¿Cuándo queremos hacerlo? → Condiciones

En muchas ocasiones, querremos que una acción de nuestras fórmulas se ejecute sólo si se dan una serie de condiciones.

Para crear una **condición**, tenemos que usar la funcion `if()`, que necesita tres **argumentos**:

1. Una [expresión](https://aprendenotion.com/formulas-avanzadas#915661aba4a145bfb17f02e5bdd4e464) que comprueba si determinado valor es cierto (`true`) o falso (`false`). Para evaluar esto, normalmente nos valdremos de **operadores de comparación.**
2. El valor que queremos que nos devuelva si el resultado de esta comprobación es `true`.
3. El valor que queremos que nos devuelva si el resultado de esta comprobación es `false`.

### Operadores de comparación

Los operadores de comparación son otro tipo de operadores como los aritméticos que vimos arriba. Es decir, caracteres que se introducen entre valores. Pero en este caso, no los usaremos para realizar operaciones matemáticas sino para **comparar dos valores**. Por lo tanto, el valor que nos devolverán no será el resultado de ninguna operación aritmética, sino solamente `true` o `false`.

Por ejemplo, el operador == comprueba si dos valores son iguales:
`2 == 2 -> true`

Estos son los 6 operadores de comparación que existen en Notion:

![[Pasted image 20230804091534.png]]


Por ejemplo, podríamos tener en una tabla una serie de tareas con estado activo o inactivo y, en un campo de fórmula, simplemente pedir que marcara las activas con un color verde y las inactivas con uno rojo:

`if(prop("Status") == "activa", "🟢", "🔴")`

O, despedazándola todavía más:

1. Comprueba que el valor de `"Status"` es igual a `"activa"`
2. Si es `true`, devuelve el valor "🟢"
3. Si es `false`, devuelve el valor "🔴"

![](https://www.youtube.com/watch?v=6FLHs29zsUM)


___

Links:

%%
Vínculos:
[[000-Menú Notion📃|Menú Notion]] , [[008-Hacer cálculos, crear templates y enlazar bases de datos|Hacer cálculos, crear templates y enlazar bases de datos]]

tags:
#notion #guia #pagnotion  #fórmula #condicional
%%