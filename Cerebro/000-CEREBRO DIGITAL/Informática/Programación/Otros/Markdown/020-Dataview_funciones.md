---
ID:: 020
tags:: #código #programación #metadatos #markdown #funciones #dataview #obsidian

Vínculos:: [[000-Menú_Markdown]]
 
---
# Funciones

Las funciones de visualización de datos proporcionan formas más avanzadas de manipular datos. Puede usar funciones **en [comandos de datos](https://blacksmithgu.github.io/obsidian-dataview/queries/data-commands/)** (excepto DESDE) para filtrar o agrupar o usarlas **como [información adicional](https://blacksmithgu.github.io/obsidian-dataview/queries/query-types/)** como columnas de TABLA o salida adicional para consultas de LISTA para ver sus datos bajo una nueva luz.

## Cómo funcionan las funciones

Las funciones son otra forma de [expresión](https://blacksmithgu.github.io/obsidian-dataview/reference/expressions/) y se pueden usar en cualquier lugar donde se pueda usar una expresión. Una función siempre te devuelve un nuevo valor y sigue este formato:

`functionname(parameter1, parameter2)`

Los parámetros son nuevamente [expresiones](https://blacksmithgu.github.io/obsidian-dataview/reference/expressions/) y puede usar literales, campos de metadatos o incluso otra función como parámetro. Encontrará qué [tipo de datos](https://blacksmithgu.github.io/obsidian-dataview/annotation/types-of-metadata/) deben tener sus parámetros en la documentación de esta página. Preste atención a la información dentro de los corchetes de función. Parámetros entre corchetes, es decir `link(path, [display])`significa que son _opcionales_ y se pueden omitir. Obtenga más información sobre el comportamiento predeterminado de cada función en su explicación.

## Llamar a funciones en listas de valores

La mayoría de las funciones se pueden aplicar a valores individuales (como `number`, `string`, `date`, etc.) O a listas de aquellos valores. Si se aplica una función a una lista, también devuelve una lista después de aplicar la función a cada elemento. en la lista. Por ejemplo:

`lower("YES") = "yes" lower(["YES", "NO"]) = ["yes", "no"]  replace("yes", "e", "a") = "yas" replace(["yes", "ree"], "e", "a") = ["yas", "raa"]`

Esta llamada "vectorización de funciones" no se mencionará explícitamente en las siguientes definiciones y es posible implícitamente para una amplia gama de estas funcionalidades.

## Constructores

Constructores que crean valores.

### `object(key1, value1, ...)`

Crea un nuevo objeto con las claves y valores proporcionados. Las claves y los valores deben alternarse en la llamada, y las claves deben siempre ser cadenas/texto.

`object() => empty object object("a", 6) => object which maps "a" to 6 object("a", 4, "c", "yes") => object which maps a to 4, and c to "yes"`

### `list(value1, value2, ...)`

Crea una nueva lista con los valores dados en ella.

`list() => empty list list(1, 2, 3) => list with 1, 2, and 3 list("a", "b", "c") => list with "a", "b", and "c"`

### `date(any)`

Analiza una fecha de la cadena, la fecha o el objeto de enlace proporcionados, si es posible, y de lo contrario devuelve un valor nulo.

`date("2020-04-18") = <date object representing April 18th, 2020> date([[2021-04-16]]) = <date object for the given page, refering to file.day>`

### `date(text, format)`

Analiza una fecha de texto a luxon `DateTime`con el formato especificado. Tenga en cuenta que es posible que los formatos localizados no funcionen. Utiliza [fichas de Luxon](https://moment.github.io/luxon/#/formatting?id=table-of-tokens) .

`date("12/31/2022", "MM/dd/yyyy") => DateTime for Decemeber 31th, 2022 date("210313", "yyMMdd") => DateTime for March 13th, 2021 date("946778645000", "x") => DateTime for "2000-01-02T03:04:05"`

### `dur(any)`

Analiza una duración a partir de la cadena o duración proporcionada y devuelve un valor nulo en caso de error.

`dur(8 minutes) = <8 minutes> dur("8 minutes, 4 seconds") = <8 minutes, 4 seconds> dur(dur(8 minutes)) = dur(8 minutes) = <8 minutes>`

### `number(string)`

Extrae el primer número de la cadena dada y lo devuelve si es posible. Devuelve nulo si no hay números en el cadena.

`number("18 years") = 18 number(34) = 34 number("hmm") = null`

### `string(any)`

Convierte cualquier valor en una representación de cadena "razonable". Esto a veces produce resultados menos bonitos que usar directamente el valor en una consulta: es principalmente útil para forzar fechas, duraciones, números, etc. en cadenas para manipulación.

`string(18) = "18" string(dur(8 hours)) = "8 hours" string(date(2021-08-15)) = "August 15th, 2021"`

### `link(path, [display])`

Construya un objeto de enlace a partir de la ruta o el nombre del archivo dado. Si se proporciona con dos argumentos, el segundo argumento es el mostrar el nombre del enlace.

`link("Hello") => link to page named 'Hello' link("Hello", "Goodbye") => link to page named 'Hello', displays as 'Goodbye'`

### `embed(link, [embed?])`

Convierta un objeto de enlace en un enlace incrustado; aunque el soporte para enlaces incrustados es algo irregular en las vistas de Dataview la incrustación de imágenes debería funcionar.

`embed(link("Hello.png")) => embedded link to the "Hello.png" image, which will render as an actual image.`

### `elink(url, [display])`

Construya un enlace a una URL externa (como `www.google.com`). Si se proporciona con dos argumentos, el segundo argumento es el nombre para mostrar del enlace.

`elink("www.google.com") => link element to google.com elink("www.google.com", "Google") => link element to google.com, displays as "Google"`

### `typeof(any)`

Obtenga el tipo de cualquier objeto para su inspección. Se puede usar junto con otros operadores para cambiar el comportamiento según el tipo.

`typeof(8) => "number" typeof("text") => "string" typeof([1, 2, 3]) => "array" typeof({ a: 1, b: 2 }) => "object" typeof(date(2020-01-01)) => "date" typeof(dur(8 minutes)) => "duration"`

---

## Operaciones numéricas

### `round(number, [digits])`

Redondea un número a un número dado de dígitos. Si no se especifica el segundo argumento, se redondea al número entero más cercano; de lo contrario, redondea al número dado de dígitos.

`round(16.555555) = 7 round(16.555555, 2) = 16.56`

### `min(a, b, ..)`

Calcule el valor mínimo de una lista de argumentos o una matriz.

`min(1, 2, 3) = 1 min([1, 2, 3]) = 1  min("a", "ab", "abc") = "a"`

### `max(a, b, ...)`

Calcule el valor máximo de una lista de argumentos o una matriz.

`max(1, 2, 3) = 3 max([1, 2, 3]) = 3  max("a", "ab", "abc") = "abc"`

### `sum(array)`

Suma todos los valores numéricos de la matriz. Si tiene valores nulos en su promedio, puede eliminarlos a través de la `nonnull`función.

`sum([1, 2, 3]) = 6 sum([]) = null  sum(nonnull([null, 1, 8])) = 9`

### `product(array)`

Calcula el producto de una lista de números. Si tiene valores nulos en su promedio, puede eliminarlos a través de la `nonnull`función.

`product([1,2,3]) = 6 product([]) = null  product(nonnull([null, 1, 2, 4])) = 8`

### `average(array)`

Calcula el promedio numérico de valores numéricos. Si tiene valores nulos en su promedio, puede eliminarlos a través de la `nonnull`función.

`average([1, 2, 3]) = 2 average([]) = null  average(nonnull([null, 1, 2])) = 1.5`

### `minby(array, function)`

Calcule el valor mínimo de una matriz, utilizando la función proporcionada.

`minby([1, 2, 3], (k) => k) = 1 minby([1, 2, 3], (k) => 0 - k) => 3  minby(this.file.tasks, (k) => k.due) => (earliest due)`

### `maxby(array, function)`

Calcule el valor máximo de una matriz, utilizando la función proporcionada.

`maxby([1, 2, 3], (k) => k) = 3 maxby([1, 2, 3], (k) => 0 - k) => 1  maxby(this.file.tasks, (k) => k.due) => (latest due)`

--

## Operaciones con objetos, matrices y cadenas

Operaciones que manipulan valores dentro de objetos contenedores.

### `contains()`y amigos

Para un resumen rápido, aquí hay algunos ejemplos:

`contains("Hello", "Lo") = false contains("Hello", "lo") = true  icontains("Hello", "Lo") = true icontains("Hello", "lo") = true  econtains("Hello", "Lo") = false econtains("Hello", "lo") = true econtains(["this","is","example"], "ex") = false econtains(["this","is","example"], "is") = true`

#### `contains(object|list|string, value)`

Comprueba si el tipo de contenedor dado tiene el valor dado. Esta función se comporta de forma ligeramente diferente en función de si el primer argumento es un objeto, una lista o una cadena. Esta función distingue entre mayúsculas y minúsculas.

- Para objetos, comprueba si el objeto tiene una clave con el nombre dado. Por ejemplo,
    
    `contains(file, "ctime") = true contains(file, "day") = true (if file has a date in its title, false otherwise)`
    
- Para las listas, comprueba si alguno de los elementos de la matriz es igual al valor dado. Por ejemplo,
    
    `contains(list(1, 2, 3), 3) = true contains(list(), 1) = false`
    
- Para cadenas, comprueba si el valor dado es una subcadena (es decir, dentro) de la cadena.
    
    `contains("hello", "lo") = true contains("yes", "no") = false`
    

#### `icontains(object|list|string, value)`

Versión insensible a mayúsculas y minúsculas de `contains()`.

#### `econtains(object|list|string, value)`

"Exacto contiene" comprueba si se encuentra la coincidencia exacta en la cadena/lista. Esta función distingue entre mayúsculas y minúsculas.

- Para cadenas, se comporta exactamente como [`contains()`](https://blacksmithgu.github.io/obsidian-dataview/reference/functions/#containsobjectliststring-value).
    
    `econtains("Hello", "Lo") = false econtains("Hello", "lo") = true`
    
- Para las listas, comprueba si la palabra exacta está en la lista.
    
    `econtains(["These", "are", "words"], "word") = false econtains(["These", "are", "words"], "words") = true`
    
- Para los objetos, comprueba si el nombre de clave exacto está presente en el objeto. No **realiza** comprobaciones recursivas.
    
    `econtains({key:"value", pairs:"here"}, "here") = false econtains({key:"value", pairs:"here"}, "key") = true econtains({key:"value", recur:{recurkey: "val"}}, "value") = false econtains({key:"value", recur:{recurkey: "val"}}, "Recur") = false econtains({key:"value", recur:{recurkey: "val"}}, "recurkey") = false`
    

### `containsword(list|string, value)`

comprueba si `value`tiene una palabra exacta en `string`o `list`. Esto es insensible a mayúsculas y minúsculas. Las salidas son diferentes para diferentes tipos de entrada, ver ejemplos.

- Para cadenas, verifica si la palabra está presente en la cadena dada.
    
    `containsword("word", "word") = true containsword("word", "Word") = true containsword("words", "Word") = false containsword("Hello there!, "hello") = true containsword("Hello there!, "HeLLo") = true containsword("Hello there chaps!, "chap") = false containsword("Hello there chaps!, "chaps") = true`
    
- Para las listas, devuelve una lista de valores booleanos que indican si se encontró la coincidencia insensible a mayúsculas y minúsculas de la palabra.
    
    `containsword(["I have no words.", "words"], "Word") = [false, false] containsword(["word", "Words"], "Word") = [true, false] containsword(["Word", "Words in word"], "WORD") = [true, true]`
    

### `extract(object, key1, key2, ...)`

Extrae múltiples campos de un objeto, creando un nuevo objeto solo con esos campos.

`extract(file, "ctime", "mtime") = object("ctime", file.ctime, "mtime", file.mtime) extract(object("test", 1)) = object()`

### `sort(list)`

Ordena una lista y devuelve una nueva lista ordenada.

`sort(list(3, 2, 1)) = list(1, 2, 3) sort(list("a", "b", "aa")) = list("a", "aa", "b")`

### `reverse(list)`

Invierte una lista, devolviendo una nueva lista en orden inverso.

`reverse(list(1, 2, 3)) = list(3, 2, 1) reverse(list("a", "b", "c")) = list("c", "b", "a")`

### `length(object|array)`

Devuelve el número de campos de un objeto o el número de entradas de una matriz.

`length([]) = 0 length([1, 2, 3]) = 3 length(object("hello", 1, "goodbye", 2)) = 2`

### `nonnull(array)`

Devuelve una nueva matriz con todos los valores nulos eliminados.

`nonnull([]) = [] nonnull([null, false]) = [false] nonnull([1, 2, 3]) = [1, 2, 3]`

### `all(array)`

Devoluciones `true`solo si TODOS los valores en la matriz son verdaderos. También puede pasar múltiples argumentos a esta función, en cuyo caso vuelve `true`sólo si todos los argumentos son verdaderos.

`all([1, 2, 3]) = true all([true, false]) = false all(true, false) = false all(true, true, true) = true`

Puede pasar una función como segundo argumento para devolver solo verdadero si todos los elementos de la matriz coinciden con el predicado.

`all([1, 2, 3], (x) => x > 0) = true all([1, 2, 3], (x) => x > 1) = false all(["apple", "pie", 3], (x) => typeof(x) = "string") = false`

### `any(array)`

Devoluciones `true`si CUALQUIERA de los valores en la matriz son verdaderos. También puede pasar múltiples argumentos a esta función, en cuyo caso vuelve `true`si alguno de los argumentos es verdadero.

`any(list(1, 2, 3)) = true any(list(true, false)) = true any(list(false, false, false)) = false any(true, false) = true any(false, false) = false`

Puede pasar una función como segundo argumento para devolver solo verdadero si algún elemento de la matriz coincide con el predicado.

`any(list(1, 2, 3), (x) => x > 2) = true any(list(1, 2, 3), (x) => x = 0) = false`

### `none(array)`

Devoluciones `true`si NINGUNO de los valores en la matriz es verdadero.

`none([]) = true none([false, false]) = true none([false, true]) = false none([1, 2, 3]) = false`

Puede pasar una función como segundo argumento para devolver solo verdadero si ninguno de los elementos de la matriz coincide con el predicado.

`none([1, 2, 3], (x) => x = 0) = true none([true, true], (x) => x = false) = true none(["Apple", "Pi", "Banana"], (x) => startswith(x, "A")) = false`

### `join(array, [delimiter])`

Une los elementos de una matriz en una sola cadena (es decir, los muestra todos en la misma línea). Si cuenta con un segundo argumento, entonces cada elemento estará separado por el separador dado.

`join(list(1, 2, 3)) = "1, 2, 3" join(list(1, 2, 3), " ") = "1 2 3" join(6) = "6" join(list()) = ""`

### `filter(array, predicate)`

Filtra elementos en una matriz de acuerdo con el predicado, devolviendo una nueva lista de los elementos que coincidieron.

`filter([1, 2, 3], (x) => x >= 2) = [2, 3] filter(["yes", "no", "yas"], (x) => startswith(x, "y")) = ["yes", "yas"]`

### `map(array, func)`

Aplica la función a cada elemento de la matriz y devuelve una lista de los resultados asignados.

`map([1, 2, 3], (x) => x + 2) = [3, 4, 5] map(["yes", "no"], (x) => x + "?") = ["yes?", "no?"]`

### `flat(array, [depth])`

Concatena subniveles de la matriz a la profundidad deseada. El valor predeterminado es 1 nivel, pero puede concatenar varios niveles. Por ejemplo, se puede utilizar para reducir la profundidad de la matriz en `rows`listas después haciendo `GROUP BY`.

`flat(list(1, 2, 3, list(4, 5), 6)) => list(1, 2, 3, 4, 5, 6) flat(list(1, list(21, 22), list(list (311, 312, 313))), 4) => list(1, 21, 22, 311, 312, 313) flat(rows.file.outlinks)) => All the file outlinks at first level in output`

---

## Operaciones con cadenas

### `regextest(pattern, string)`

Comprueba si el patrón de expresiones regulares dado se puede encontrar en la cadena (utilizando el motor de expresiones regulares de JavaScript).

`regextest("\w+", "hello") = true regextest(".", "a") = true regextest("yes|no", "maybe") = false regextest("what", "what's up dog?") = true`

### `regexmatch(pattern, string)`

Comprueba si el patrón de expresiones regulares dado coincide con la _cadena completa_ , utilizando el motor de expresiones regulares de JavaScript. Esto difiere de `regextest`en que regextest puede coincidir solo con partes del texto.

`regexmatch("\w+", "hello") = true regexmatch(".", "a") = true regexmatch("yes|no", "maybe") = false regexmatch("what", "what's up dog?") = false`

### `regexreplace(string, pattern, replacement)`

Reemplaza todas las instancias donde la _expresión regular_ `pattern`partidos en `string`, con `replacement`. Esto usa JavaScript reemplazar método bajo el capó, por lo que puede utilizar caracteres especiales como `$1`para referirse al primer grupo de captura, y así sucesivamente.

`regexreplace("yes", "[ys]", "a") = "aea" regexreplace("Suite 1000", "\d+", "-") = "Suite -"`

### `replace(string, pattern, replacement)`

Reemplace todas las instancias de `pattern`en `string`con `replacement`.

`replace("what", "wh", "h") = "hat" replace("The big dog chased the big cat.", "big", "small") = "The small dog chased the small cat." replace("test", "test", "no") = "no"`

### `lower(string)`

Convierte una cadena a minúsculas.

`lower("Test") = "test" lower("TEST") = "test"`

### `upper(string)`

Convierte una cadena a mayúsculas.

`upper("Test") = "TEST" upper("test") = "TEST"`

### `split(string, delimiter, [limit])`

Divida una cadena en la cadena delimitadora dada. Si se proporciona un tercer argumento, limita el número de divisiones que se producen. La cadena delimitadora se interpreta como una expresión regular. Si hay grupos de captura en el delimitador, las coincidencias se empalman en la matriz de resultados y las capturas que no coinciden son cadenas vacías.

`split("hello world", " ") = list("hello", "world") split("hello  world", "\s") = list("hello", "world") split("hello there world", " ", 2) = list("hello", "there") split("hello there world", "(t?here)") = list("hello ", "there", " world") split("hello there world", "( )(x)?") = list("hello", " ", "", "there", " ", "", "world")`

### `startswith(string, prefix)`

Comprueba si una cadena comienza con el prefijo dado.

`startswith("yes", "ye") = true startswith("path/to/something", "path/") = true startswith("yes", "no") = false`

### `endswith(string, suffix)`

Comprueba si una cadena termina con el sufijo dado.

`endswith("yes", "es") = true endswith("path/to/something", "something") = true endswith("yes", "ye") = false`

### `padleft(string, length, [padding])`

Rellena una cuerda hasta la longitud deseada agregando relleno en el lado izquierdo. Si omite el carácter de relleno, los espacios se usará por defecto.

`padleft("hello", 7) = "  hello" padleft("yes", 5, "!") = "!!yes"`

### `padright(string, length, [padding])`

Equivalente a `padleft`, pero almohadillas a la derecha en su lugar.

`padright("hello", 7) = "hello  " padright("yes", 5, "!") = "yes!!"`

### `substring(string, start, [end])`

Tome un trozo de cuerda, comenzando en `start`y terminando en `end`(o el final de la cadena si no se especifica).

`substring("hello", 0, 2) = "he" substring("hello", 2, 4) = "ll" substring("hello", 2) = "llo" substring("hello", 0) = "hello"`

### `truncate(string, length, [suffix])`

Trunca una cadena para que tenga como máximo la longitud dada, incluido el `suffix`(que por defecto es `...`). Generalmente útil para cortar texto largo en tablas.

`truncate("Hello there!", 8) = "Hello..." truncate("Hello there!", 8, "/") = "Hello t/" truncate("Hello there!", 10) = "Hello t..." truncate("Hello there!", 10, "!") = "Hello the!" truncate("Hello there!", 20) = "Hello there!"`

## Funciones de utilidad

### `default(field, value)`

Si `field`es nulo, regresa `value`; de lo contrario volver `field`. Útil para reemplazar valores nulos con valores predeterminados. Por ejemplo, para mostrar proyectos que aún no se han completado, use `"incomplete"`como su valor por defecto:

`default(dateCompleted, "incomplete")`

El valor predeterminado está vectorizado en ambos argumentos; si necesita usar default explícitamente en un argumento de lista, use `ldefault`, cual es el mismo que el predeterminado pero no está vectorizado.

`default(list(1, 2, null), 3) = list(1, 2, 3) ldefault(list(1, 2, null), 3) = list(1, 2, null)`

### `choice(bool, left, right)`

Una instrucción if primitiva: si el primer argumento es verdadero, regresa a la izquierda; de lo contrario, regresa a la derecha.

`choice(true, "yes", "no") = "yes" choice(false, "yes", "no") = "no" choice(x > 4, y, z) = y if x > 4, else z`

### `striptime(date)`

Elimine el componente de tiempo de una fecha, dejando solo el año, el mes y el día. Bueno para comparaciones de fechas si no te importa sobre el tiempo.

`striptime(file.ctime) = file.cday striptime(file.mtime) = file.mday`

### `dateformat(date|datetime, string)`

Formatee una fecha de vista de datos usando una cadena de formato. Utiliza [fichas de Luxon](https://moment.github.io/luxon/#/formatting?id=table-of-tokens) .

`dateformat(file.ctime,"yyyy-MM-dd") = "2022-01-05" dateformat(file.ctime,"HH:mm:ss") = "12:18:04" dateformat(date(now),"x") = "1407287224054" dateformat(file.mtime,"ffff") = "Wednesday, August 6, 2014, 1:07 PM Eastern Daylight Time"`

### `localtime(date)`

Convierte una fecha en una zona horaria fija en una fecha en la zona horaria actual.

### `meta(link)`

Obtiene un objeto que contiene metadatos de un enlace. Cuando accede a una propiedad en un enlace, lo que obtiene es la propiedad valor del archivo vinculado. El `meta`La función permite acceder a las propiedades del propio enlace.

Hay varias propiedades en el objeto devuelto por `meta`:

#### `meta(link).display`

Obtener el texto para mostrar de un enlace, o nulo si el enlace no tiene un texto para mostrar definido.

`meta([[2021-11-01|Displayed link text]]).display = "Displayed link text" meta([[2021-11-01]]).display = null`

#### `meta(link).embed`

Verdadero o falso dependiendo de si el enlace es una inserción. Esos son enlaces que comienzan con un signo de exclamación, como `![[Some Link]]`.

#### `meta(link).path`

Obtener la parte de la ruta de un enlace.

`meta([[My Project]]).path = "My Project" meta([[My Project#Next Actions]]).path = "My Project" meta([[My Project#^9bcbe8]]).path = "My Project"`

#### `meta(link).subpath`

Obtener la subruta de un enlace. Para enlaces a un encabezado dentro de un archivo, la subruta será el texto del encabezado. Para enlaces a un bloque, la ruta secundaria será el ID del bloque. Si no se aplica ninguno de esos casos, la subruta será nula.

`meta([[My Project#Next Actions]]).subpath = "Next Actions" meta([[My Project#^9bcbe8]]).subpath = "9bcbe8" meta([[My Project]]).subpath = null`

Esto se puede utilizar para seleccionar tareas bajo encabezados específicos.

` ```dataview task where meta(section).subpath = "Next Actions" ``` `

#### `meta(link).type`

Tiene el valor "archivo", "encabezado" o "bloque" dependiendo de si el vínculo vincula a un archivo completo, un encabezado dentro un archivo, o a un bloque dentro de un archivo.

`meta([[My Project]]).type = "file" meta([[My Project#Next Actions]]).type = "header" meta([[My Project#^9bcbe8]]).type = "block"`


*Vínculos:*
[[000-Menú Markdown 📃|Menú Markdown 📃]] ]]