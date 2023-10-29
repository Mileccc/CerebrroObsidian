---
ID: 33
nombre: Expresiones anidadas
tags:
  - pagacceso_a_datos
---
___
### Expresiones anidadas

Las expresiones XPath pueden anidarse, lo que permite definir expresiones más complicadas. Por ejemplo, en el documento utilizado anteriormente:


```xml
<?xml version="1.0" encoding="UTF-8"?>
<biblioteca>
  <libro>
    <titulo>La vida está en otra parte</titulo>
    <autor>Milan Kundera</autor>
    <fechaPublicacion año="1973"/>
  </libro>
  <libro>
    <titulo>Pantaleón y las visitadoras</titulo>
    <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
    <fechaPublicacion año="1973"/>
  </libro>
  <libro>
    <titulo>Conversación en la catedral</titulo>
    <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
    <fechaPublicacion año="1969"/>
  </libro>
</biblioteca>
```

___
___

Un ejemplo de expresión anidada sería, por ejemplo, obtener los títulos de los libros publicados el mismo año que la novela "La vida está en otra parte". Esta información no está directamente almacenada en el documento, pero se puede obtener la respuesta en dos pasos:

- obtener primero el año en que se publicó la novela "La vida está en otra parte":

```
//libro[titulo="La vida está en otra parte"]/fechaPublicacion/@año
```
$$Resultado$$
```xml
año="1973"
```

___
___

Estas dos expresiones se pueden unir en una única expresión, sustituyendo en la segunda expresión el valor 1973 por la primera expresión:

```
//libro[fechaPublicacion/@año=//libro[titulo="La vida está en otra parte"]/fechaPublicacion/@año]/titulo
```
$$Resultado$$
```xml
<titulo>La vida está en otra parte</titulo>
<titulo>Pantaleón y las visitadoras</titulo>
```

___
___

Como cada una de las expresiones puede escribirse de varias maneras, en realidad hay muchas formas de encontrar la respuesta. Por ejemplo, en la solución siguiente los predicados se encuentran al final del eje en cada subexpresión:

```
//titulo[../fechaPublicacion/@año=//@año[../../titulo="La vida está en otra parte"]]
```
$$Resultado$$
```xml
<titulo>La vida está en otra parte</titulo>
<titulo>Pantaleón y las visitadoras</titulo>
```

___
___

Otro ejemplo de expresión anidada sería obtener los títulos de los libros del mismo autor que la novela "Pantaleón y las visitadoras". Como en el ejemplo anterior, la respuesta puede obtenerse en dos pasos:

- obtener primero el autor de la novela "Pantaleón y las visitadoras":

```
//libro[titulo="Pantaleón y las visitadoras"]/autor/text()
```
$$Resultado$$
```xml
Mario Vargas Llosa
```

___
___

- y obtener después los títulos de los libros escritos por Mario Vargas Llosa:

```
//libro[autor="Mario Vargas Llosa"]/titulo
```
$$Resultado$$
```xml
<titulo>Pantaleón y las visitadoras</titulo>
<titulo>Conversación en la catedral</titulo>
```

___
___

Estas dos expresiones se pueden unir en una única expresión, sustituyendo en la segunda expresión el valor "Mario Vargas Llosa" por la primera expresión:

```
//libro[autor=//libro[titulo="Pantaleón y las visitadoras"]/autor/text()]/titulo
```
$$Resultado$$
```xml
<titulo>Pantaleón y las visitadoras</titulo>
<titulo>Conversación en la catedral</titulo>
```

___
___

Un detalle importante es que no hay que escribir la primera expresión entre comillas.

Incluso se puede omitir la selección de nodos /text() de la segunda expresión y escribir la expresión XPath así:

```
//libro[autor=//libro[titulo="Pantaleón y las visitadoras"]/autor]/titulo
```
$$Resultado$$
```xml
<titulo>Pantaleón y las visitadoras</titulo>
<titulo>Conversación en la catedral</titulo>
```


___
%%
tags: #java  #pagacceso_a_datos  #ExpresionesAnidadas #XPath #XML #Biblioteca #Libro #Titulo #Autor #FechaPublicacion #Año #Resultado #Predicado #Eje #Subexpresion #MarioVargasLlosa #MilanKundera #LaVidaEstáEnOtraParte #PantaleónYLasVisitadoras #ConversaciónEnLaCatedral #VariasManeras #DosPasos #UnDetalleImportante
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%