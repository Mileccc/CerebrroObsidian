---
ID: 131
"tags:": 
nombre: cheat sheet expresiones regulares
---
___
# cheat sheet expresiones regulares


![[5483089e3aa56bbee7c194370d1a22d7.png|1800]]

https://regex101.com/r/q9piol/1

https://regexr.com/

### 1- Caracteres Especiales

`^` | Coincide con la expresión a su derecha al comienzo de una cadena. Coincide con cada instancia antes de cada `\n` en la cadena.

`$` | Coincide con la expresión a su izquierda al final de una cadena. Coincide con cada instancia antes de cada `\n` en la cadena.

`.` | Coincide con cualquier carácter excepto los terminadores de línea como `\n`.

`\` | Escapa caracteres especiales o denota clases de caracteres.

`A|B` | Coincide con la expresión A o B. Si se coincide con A primero, B se deja sin probar.

`+` | Coincide de manera codiciosa con la expresión a su izquierda 1 o más veces.

`*` | Coincide de manera codiciosa con la expresión a su izquierda 0 o más veces.

`?` | Coincide de manera codiciosa con la expresión a su izquierda 0 o 1 vez. Pero si se agrega `?` a los calificadores (`+`, `*`, y `?` en sí), realizará coincidencias de manera no codiciosa.

`{m}` | Coincide con la expresión a su izquierda m veces, y no menos.

`{m,n}` | Coincide con la expresión a su izquierda de m a n veces, y no menos.

`{m,n}?` | Coincide con la expresión a su izquierda m veces, y omite n. Ver `?` arriba.

### 2- Clases de Caracteres (también conocidas como Secuencias Especiales)

`\w` | Coincide con caracteres alfanuméricos, es decir, `a-z`, `A-Z`, y `0-9`. También coincide con el guion bajo, `_`.

`\d` | Coincide con dígitos, es decir, `0-9`.

`\D` | Coincide con cualquier no dígito.

`\s` | Coincide con caracteres de espacio en blanco, que incluyen `\t`, `\n`, `\r` y espacio.

`\S` | Coincide con caracteres que no son de espacio en blanco.

`\b` | Coincide con el límite (o cadena vacía) al principio y al final de una palabra, es decir, entre `\w` y `\W`.

`\B` | Coincide donde `\b` no lo hace, es decir, el límite de caracteres `\w`.

`\A` | Coincide con la expresión a su derecha en el inicio absoluto de una cadena, ya sea en modo de línea única o multilínea.

`\Z` | Coincide con la expresión a su izquierda en el final absoluto de una cadena, ya sea en modo de línea única o multilínea.

### 3- Conjuntos

`[ ]` | Contiene un conjunto de caracteres para coincidir.

`[amk]` | Coincide con `a`, `m` o `k`. No coincide con `amk`.

`[a-z]` | Coincide con cualquier letra del alfabeto de `a` a `z`.

`[a\-z]` | Coincide con `a`, `-`, o `z`. Coincide con `-` porque `\` lo escapa.

`[a-]` | Coincide con `a` o `-`. porque `-` no se usa para indicar una serie de caracteres.

`[-a]` | Igual que arriba, coincide con `a` o `-`.

`[a-z0-9]` | Coincide con caracteres de `a` a `z` y también de `0` a `9`.

`[(+*)]` | Los caracteres especiales se vuelven literales dentro de un conjunto, por lo que coincide con `(`, `+`, `*`, y `)`.

`[^ab5]` | Agregar `^` excluye cualquier carácter en el conjunto. Aquí coincide con caracteres que no son `a`, `b` o `5`.

### 4- Grupos

`( )` | Coincide con la expresión dentro de los paréntesis y la agrupa.

`(? )` | Dentro de paréntesis como este, `?` actúa como una notación de extensión. Su significado depende del carácter inmediatamente a su derecha.

`(?PAB)` | Coincide con la expresión `AB` y se puede acceder con el nombre del grupo.

`(?aiLmsux)` | Aquí, `a`, `i`, `L`, `m`, `s`, `u` y `x` son indicadores:

- `a` — Coincide solo con ASCII
- `i` — Ignora mayúsculas y minúsculas
- `L` — Dependiente de la configuración local
- `m` — Multilínea
- `s` — Coincide con todo
- `u` — Coincide con Unicode
- `x` — Explicativo

`(?:A)` | Coincide con la expresión representada por `A`, pero a diferencia de `(?PAB)`, no se puede recuperar después.

`(?#...)` | Un comentario. El contenido es para que lo leamos, no para que coincida.

`A(?=B)` | Afirmación de búsqueda adelante. Esto coincide con la expresión `A` solo si está seguida de `B`.

`A(?!B)` | Afirmación de búsqueda negativa adelante. Esto coincide con la expresión `A` solo si no está seguida de `B`.

`(?<=B)A` | Afirmación de búsqueda positiva hacia atrás. Esto coincide con la expresión `A` solo si `B` está inmediatamente a su izquierda. Esto solo puede coincidir con expresiones de longitud fija.

`(?<!B)A` | Afirmación de búsqueda negativa hacia atrás. Esto coincide con la expresión `A` solo si `B` no está inmediatamente a su izquierda. Esto solo puede coincidir con expresiones de longitud fija.

`(?P=name)` | Coincide con la expresión coincidida por un grupo anterior llamado "nombre".

`(...)\1` | El número 1 corresponde al primer grupo que se debe coincidir. Si queremos coincidir con más instancias de la misma expresión, simplemente usamos su número en lugar de escribir la expresión completa nuevamente. Podemos usar de 1 a 99 de estos grupos y sus números correspondientes.

### 5- Funciones Populares del Módulo re de Python

`re.findall(A, B)` | Coincide con todas las instancias de una expresión `A` en una cadena `B` y las devuelve en una lista.

`re.search(A, B)` | Coincide con la primera instancia de una expresión `A` en una cadena `B` y la devuelve como un objeto de coincidencia de `re`.

`re.split(A, B)` | Divide una cadena `B` en una lista utilizando el delimitador `A`.

`re.sub(A, B, C)` | Reemplaza `A` con `B` en la cadena `C`.


___

%%
tags:  #programación #pagfundamentospython #python  

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%