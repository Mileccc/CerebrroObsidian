---
ID:: 010
tags:: #código #programación #metadatos #markdown #obsidian #dataview #expresiones

Vínculos:: [[000-Menú_Markdown]]
num_turno:: 10
prueba1:: elemento1
prueba2:: elemento2
---
## Formato de salida
- **Tabla**: table
- **Lista**: list
- **Tarea**: task
- **Calendario**: calendar

## Elegir fuente de los datos
- **from**

*Ejemplo 1:*
```
```dataview
list 
from "000-CEREBRO DIGITAL/Informática/Programación/Otros/Markdown"
```

Enumera todas las páginas dentro de la carpeta Markdown y sus subcarpetas

```dataview
list 
from "000-CEREBRO DIGITAL/Informática/Programación/Otros/Markdown"
```

*Ejemplo 2:*

```
```dataview
list
from #3d or #2d
```

Enumera todas las páginas que incluyen la etiqueta #3d o #2d

```dataview
list
from #3d or #2d
```

*Ejemplo 3:*
```
```dataview
list
from (#matemáticas and "000-CEREBRO DIGITAL/Matemáticas/020-Geometría") or ("000-CEREBRO DIGITAL/Matemáticas/001-Aritmética" and outgoing([[010-Propiedades aritméticas]]))
```

Enumera todas las páginas que tienen la etiqueta #matemáticas y están dentro de la carpeta "020-Geometría" (o sus subcarpetas), o están dentro de la carpeta "001-Aritmética" y están vinculadas a la página [010-Propiedades aritméticas] de la escuela Tareas pendientes actuales

```dataview
list
from (#matemáticas and "000-CEREBRO DIGITAL/Matemáticas/020-Geometría") or ("000-CEREBRO DIGITAL/Matemáticas/001-Aritmética" and outgoing([[010-Propiedades aritméticas]]))
```

## Filtrar, ordenar, agrupar o limitar resultados
- **where**: filtra notas según la información dentro de las notas, los campos de metadatos.
- **sort**: ordena los resultados según un campo y una dirección.
- **group by**: agrupa varios resultados en una fila de resultados por grupo.
- **limit**: limita el recuento de resultados de su consulta al número dado.
- **flatten**: divide un resultado en varios resultados en función de un campo o cálculo.

*Ejemplo 1:*
```
```dataview
list
where num_turno > 9
```

Enumera todas las páginas donde "num_anterior" es mayor a 9

```dataview
list
where num_turno > 9
```

*Ejemplo 2:*

```
```dataview
list
from #programación 
sort file.ctime desc
limit 3
```

Enumera las 3 páginas creadas más recientemente en su bóveda que tienen la etiqueta #programación 

```dataview
list
from #programación 
sort file.ctime desc
limit 3
```

*Ejemplo 3:*

```
```dataview
list
from #matemáticas 
group by file.link
sort rows.file.ctime desc
limit 10
```

Enumera los 10 tags de #matemáticas  más antiguos de su bóveda como una lista , agrupadas por su archivo contenedor y ordenadas del archivo más antiguo al más nuevo.

```dataview
list
from #matemáticas 
group by file.link
sort rows.file.ctime desc
limit 10
```

*Ejemplo 4:*

```
```dataview
table num_turno as "prueba0", prueba1, prueba2 
from "000-CEREBRO DIGITAL/Informática/Programación/Otros/Markdown"
```

Muestra una tabla con tres metadatos ( uno con alias) de la carpeta Markdown

```dataview
table num_turno as "prueba0", prueba1, prueba2 
from "000-CEREBRO DIGITAL/Informática/Programación/Otros/Markdown"
```

*Ejemplo 5:*

```
```dataview
list 
from #matemáticas 
where prueba1 = "elemento1"
```

Muestra una lista de notas con el tag #matemáticas en el que su metadato prueba1 sea igual a elemento1

```dataview
list 
from #matemáticas 
where prueba1 = "elemento1"
```

*Ejemplo 6:*

```
```dataview
table file.ctime, file.etags, file.folder, file.link, file.name
from "000-CEREBRO DIGITAL/Matemáticas/001-Aritmética"
sort file.ctime
```
Crea una tabla con varios campos ordenados por fecha de creación
```dataview
table file.ctime, file.etags, file.folder, file.link, file.name
from "000-CEREBRO DIGITAL/Matemáticas/001-Aritmética"
sort file.ctime
```
*Ejemplo 7:*

```
```dataview
list "file path: " + file.folder + " _(created: " + file.cday + ")_"
from "000-CEREBRO DIGITAL/Matemáticas/001-Aritmética"
```

Crea una lista que concatena texto con datos

```dataview
list "file path: " + file.folder + " _(created: " + file.cday + ")_"
from "000-CEREBRO DIGITAL/Matemáticas/001-Aritmética"
```

## Expresiones
```
# Literals
1                   (number)
true/false          (boolean)
"text"              (text)
date(2021-04-18)    (date)
dur(1 day)          (duration)
[[Link]]            (link)
[1, 2, 3]           (list)
{ a: 1, b: 2 }      (object)

# Lambdas
(x1, x2) => ...     (lambda)

# References
field               (se refiere directamente a un campo)
simple-field        (se refiere a los campos con espacios/puntuación en ellos como "¡Campo simple!)
a.b                 (si a es un objeto, recupera el campo llamado 'b')
a[expr]             (si a es un objeto o una matriz, recupera el campo con el nombre especificado por la expresión 'expr')
f(a, b, ...)        (llamar a una función llamada `f` en los argumentos a, b, ...)

# Arithmetic
a + b               (addition)
a - b               (subtraction)
a * b               (multiplication)
a / b               (division)
a % b               (modulo / remainder of division)

# Comparison
a > b               (check if a is greater than b)
a < b               (check if a is less than b)
a = b               (check if a equals b)
a != b              (check if a does not equal b)
a <= b              (check if a is less than or equal to b)
a >= b              (check if a is greater than or equal to b)

# Strings

a + b               (string concatenation)
a * num             (repeat string <num> times)

# Special Operations
[[Link]].value      (obtener 'valor' de la página 'Enlace')
```

## Fechas

| `date(2021-11-11)`       | A date, November 11th, 2021                            |
| ------------------------ | ------------------------------------------------------ |
| `date(2021-09-20T20:17)` | A date, September 20th, 2021 at 20:17                  |
| `date(today)`            | Una fecha que representa la fecha actual               |
| `date(now)`              | Una fecha que representa la fecha y hora actual        |
| `date(tomorrow)`         | Una fecha que representa la fecha de mañana            |
| `date(yesterday)`        | Una fecha que representa la fecha de ayer.             |
| `date(sow)`              | Una fecha que representa el inicio de la semana actual |
| `date(eow)`              | Una fecha que representa el final de la semana actual  |
| `date(som)`              | Una fecha que representa el inicio del mes actual      |
| `date(eom)`              | Una fecha que representa el final del mes actual       |
| `date(soy)`              | Una fecha que representa el inicio del año en curso    |
| `date(eoy)`              | Una fecha que representa el final del año en curso     |

## Duraciones

| Literal          | Description   |
| ---------------- | ------------- |
| `dur(1 s)`       | one second    |
| `dur(3 s)`       | three seconds |
| `dur(1 sec)`     | one second    |
| `dur(3 secs)`    | three seconds |
| `dur(1 second)`  | one second    |
| `dur(3 seconds)` | three seconds |

|Literal|Description|
|---|---|
|`dur(1 m)`|one minute|
|`dur(3 m)`|three minutes|
|`dur(1 min)`|one minute|
|`dur(3 mins)`|three minutes|
|`dur(1 minute)`|one minute|
|`dur(3 minutes)`|three minutes|

| Literal        | Description |
| -------------- | ----------- |
| `dur(1 h)`     | one hour    |
| `dur(3 h)`     | three hours |
| `dur(1 hr)`    | one hour    |
| `dur(3 hrs)`   | three hours |
| `dur(1 hour)`  | one hour    |
| `dur(3 hours)` | three hours |

|Literal|Description|
|---|---|
|`dur(1 d)`|one day|
|`dur(3 d)`|three days|
|`dur(1 day)`|one day|
|`dur(3 days)`|three days|

|Literal|Description|
|---|---|
|`dur(1 w)`|one week|
|`dur(3 w)`|three weeks|
|`dur(1 wk)`|one week|
|`dur(3 wks)`|three weeks|
|`dur(1 week)`|one week|
|`dur(3 weeks)`|three weeks|

|Literal|Description|
|---|---|
|`dur(1 mo)`|one month|
|`dur(3 mo)`|three month|
|`dur(1 month)`|one month|
|`dur(3 months)`|three months|

|Literal|Description|
|---|---|
|`dur(1 yr)`|one year|
|`dur(3 yrs)`|three years|
|`dur(1 year)`|one year|
|`dur(3 years)`|three years|

|Literal|Description|
|---|---|
|`dur(1 s, 2 m, 3 h)`|three hours, two minutes, and one second|
|`dur(1 s 2 m 3 h)`|three hours, two minutes, and one second|
|`dur(1s 2m 3h)`|three hours, two minutes, and one second|
|`dur(1second 2min 3h)`|three hours, two minutes, and one second|

*Vínculos:*
[[000-Menú Markdown 📃|Menú Markdown 📃]] 