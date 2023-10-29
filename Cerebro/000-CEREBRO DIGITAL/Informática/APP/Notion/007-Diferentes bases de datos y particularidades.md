---
ID:: 007
-nombre:: "Diferentes bases de datos y particularidades"
-tags:: #notion #guia #pagnotion #base_de_datos #tablas #tableros #listas #galerías #calendarios #board
---
___

# Diferentes bases de datos y particularidades

Una vez conoces las diferentes propiedades que puede tener una base de datos y sus particularidades, es hora de saber un poco más sobre cada uno de los tipos de bases de datos que tenemos a nuestra disposición que, te recuerdo, son 5:

- [`Tabla`](https://aprendenotion.com/4be9428ea4224a66808240f8eb01d9af#d3d33a418df34f4d88a0bf1ae679be5d)
- [`Tablero`](https://aprendenotion.com/4be9428ea4224a66808240f8eb01d9af#5c512fca08da433186764d6c80c0455e)
- [`Galería`](https://aprendenotion.com/4be9428ea4224a66808240f8eb01d9af#2121342dced84622b213fee87d04d767)
- [`Calendario`](https://aprendenotion.com/4be9428ea4224a66808240f8eb01d9af#878ee490d7af4a788c59376b445d5981)
- [`Lista`](https://aprendenotion.com/4be9428ea4224a66808240f8eb01d9af#eb62af0baec24e6399c9e4b7b2e7f457)

## Tablas

La vista de tablas es la más tradicional y más parecida a nuestro concepto de tabla de Excel de toda la vida. Te permite **introducir una serie de registros, que se van apilando de arriba a abajo, y añadirles todas las propiedades que necesites** (cada propiedad será una columna) de la lista que vimos anteriormente. Estas propiedades puedes esconderlas, hacerlas visibles, o cambiarlas de lugar pinchando y arrastrando sus columnas.

![image](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2459e3af-e30a-4a0e-9cb2-25040cc0a10a/reordenacion-items/w=1920,quality=80)

También, al ser una versión expandida de una lista, puedes hacer que las celdas se ajusten a su contenido (marcando la opción `Wrap Cells` en el menú `...`) o que lo contengan, es decir, que se quede todo en una línea o que, por el contrario, las celdas se redimensionen para poder ver todo el contenido.
![image](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/258f3116-cac7-4ed4-a401-4228194f6cf0/wrap-cells/w=1920,quality=80)

## Tableros (board)

Si lo que necesitas es poner un mayor foco **en qué estado de un proceso determinado** están tus ítems, la vista más útil es la de tablero, que te permitirá organizar los registros por fases y moverlos de una a otra según sus propiedades.

En este tipo de base de datos, los ítems que se creen tomarán el aspecto de "cards" o "tarjetas", y al pinchar en cada uno se abrirá su página correspondiente.

### Reagrupar columnas y tarjetas

Igual que en las tablas, podemos reordenar nuestros ítems simplemente pinchando y arrastrando

- Para cambiar el **orden de las columnas**, basta con pinchar en el hombre de la misma y moverla de un lado a otro.
- Para cambiar el **orden de las tarjetas**, basta con pinchar una y arrastrarla arriba o hacia abajo.

### Criterios de agrupación

Como habrás podido comprobar, al crear una vista de tablero, las tarjetas se agrupan por columnas en base a una propiedad. A día de hoy, los tipos de Propiedades por los que puedes agrupar tus tarjetas son `Select`, `Multi-select` y `Person`.

Para cambiar la propiedad por la que se agrupen, basta ir a la parte superior derecha de la tabla y buscar `Group by` (en las tablas `Inline` esta opción está escondida en el menu `...`)

![He cambiado el criterio de ordenación para que, en vez de agruparme los contenidos por tipo, los agrupe por puntuación.](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f126cee3-9a5b-4b5f-a30c-1dfb5b51635c/agrupar-por/w=1920,quality=80)

He cambiado el criterio de ordenación para que, en vez de agruparme los contenidos por tipo, los agrupe por puntuación.

Una vez apliques el cambio, las columnas del tablero cambiarán a la propiedad que has definido.

De la misma manera, todos los ítems nuevos que crees bajo una de esas columnas, llevarán esa propiedad asignada por defecto.

### Cambiar vista previa de tarjeta

En este tipo de vista, como los ítems se visualizan en forma de tarjeta, podemos tener un mayor control en la vista de estos. Para modificar cómo los vemos en el tablero, basta con ir a `Properties` y allí verás dos desplegables; `Card Preview` y `Card Size`.

- `Card size`. Aquí elegiremos el tamaño de nuestra tarjeta, que puede ser `Small`, `Medium` o `Large`
- `Card preview`. En este desplegable tendremos tres opciones a elegir:

- `Page Cover`: Mostrará la imagen que hayas definido como portada de la página, si es que has definido alguna
- `Page Content`: Mostrará un previo del cuerpo de la página. Si en tu contenido hay alguna imagen, mostrará esta.
- `Files`: Si en tu base de datos has añadido la propiedad de `Files & Media`, con esta opción tendrás la opción de elegir la imagen que hayas subido aquí como vista previa.

![image](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2fe2281a-6552-427d-8d3b-0d401ddd5299/card-preview-size/w=1920,quality=80)

Una vez has seleccionado la imagen que quieres que se vea en tus tarjetas, si marcas la opción `Fit Image` esta imagen ocupará la totalidad del marco de la tarjeta y podrás reposicionarla pasando el ratón por encima y marcando la opción `Reposition` para ajustarla a tu gusto.

Por el contrario, si dejas `Fit Image` desmarcado, la imagen se redimensionará para que toda quepa dentro del marco de la tarjeta.

### Esconder columnas

Dependiendo del contexto, es posible que haya columnas que no nos interese ver en algunos tableros. Para centrarte sólo en las columnas que te interesan, basta con pinchar en `...` en la columna que desees esconder y pulsar en `Hide`. Todas las columnas escondidas residirán en una columna con el título `Hidden columns`, desde donde podrás seguir añadiendo ítems y operar con ellas pinchando en el nombre de la propiedad.

![image](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/85ec11b0-a29d-406a-962a-6b0da9f931a9/hide-columns/w=1920,quality=80)

## Galerías

La vista de galería nos será muy útil cuando en nuestra base de datos tengamos **contenido visual**, como moodboards, directorios de personas, recetas o un registro de libros o CD's .

En este tipo de bases de datos, al igual que en los tableros, los ítems se mostrarán como tarjetas cuadradas con una imagen representativa. Para que una galería "funcione", será por tanto **indispensable que en cada item haya algún tipo de imagen** que Notion pueda usar para convertirla en la portada de tu tarjeta.

Como ya vimos en los tableros, Notion podrá tomar esta imagen de tres fuentes diferentes:

- `Page Cover`: La imagen que hayas definido como portada de la página
- `Page Content`: Si en el contenido de la página hay alguna imagen, Notion la detectará y la usará como previo de la tarjeta
- La propiedad `Files:` Si has creado esta propiedad y has subido imágenes a través de ellas, Notion usará esa imagen como previo.

Recuerda que también puedes especificar cómo quieres que se comporte la imagen:

- Por defecto, verás la totalidad de la imagen aunque esto suponga que queden espacios blancos a los lados de la tarjeta.
- Si quieres que la imagen cubra la totalidad del marco, deberás marcar la opción `Fit Image` y jugar con `Reposition` para moverla a tu gusto.

![image](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/aeddeca4-b403-4860-a6e5-9e599181d984/fit-image/w=1920,quality=80)

Y, como también hemos visto anteriormente, podrás modificar el tamaño de cada ítem en `Propiedades`, marcando la opción `Card Size` y eligiendo el tamaño en el que quieres que se vean tus ítems.

## Calendarios

Esta vista de tabla de datos es muy interesante cuando quieres **poner el foco en cómo tus ítems se conectan con fechas**. Para que una tabla de datos pueda convertirse en calendario es esencial que, al menos, una de sus propiedades sea de `Date`.

Esta propiedad de Date será la que Notion use como referencia para colocar los ítems como su fueran eventos en un calendario, que **pueden durar un sólo día o alargarse en el tiempo**, dependiendo de si su propiedad de `Date` se refiera a un día concreto o un rango de tiempo.

Para añadir más ítems en un calendario, basta con pasar el ratón por encima del día en cuestión y automáticamente se creará un nuevo ítem con ese día ya generado automáticamente en la propiedad `Date`.

### Criterio de agrupación de items en el calendario

Como aclaración, para que la vista de Calendario funcione necesitas que tus ítems tengan al menos una propiedad `Date`, pero no tiene por qué ser sólo esa, sino cualquier propiedad que haga uso de una fecha, que como sabemos son tres:

- `Date`
- `Created time`
- `Last edited time`

Si en nuestro ítem tenemos más de una propiedad de Fecha, y al igual que en los tableros podríamos definir por qué propiedad queríamos que se agruparan nuestros items, en los calendarios podremos decidir qué propiedad de Fecha será la que queramos que use Notion como referencia para colocar nuestros items. Esto se puede hacer de dos maneras:

- Si el calendario es `Full Page`, en la parte superior derecha del mismo, al lado de `Properties`, habrá un texto que ponga `By [Propiedad]` donde podrás seleccionar qué tipo de propiedad de fecha quieres que tome como referencia
- Si el calendario es `Inline`, verás esta opción escondida tras el menú `...`, en `Calendar by`

### Reordenar y editar items en el calendario

Igual que en las otras bases de datos que hemos visto hasta ahora, podrás pinchar y arrastrar los ítems por los diferentes días para reorganizarlos. Esto hará que automáticamente esos ítems cambien de fecha, con lo que funciona realmente como un calendario de cualquier aplicación al uso.

De la misma forma, cada item tiene la opción de ser alargado o acortado en el tiempo, y convertirá esa propiedad de fecha en una que contega un rango de un día a otro. Basta con que te pongas encima del item en cuestión y, al ver el cursor cambiar a dos flechas, arrastres ese item hacia el lado que quieras para alargarlo en el tiempo.

![image](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bf4c7900-aefc-4dcb-987c-38da766b9fbb/change_date_stretch/w=1920,quality=80)

Por último, si alguno de tus ítems no tiene fecha, no aparecerán en el calendario pero podrás seguir accediendo a ellos. En estos casos, en el menú superior del calendario aparecerá una opción que diga `No [Propiedad]`.

Desde aquí podrás ver y acceder a los items que no tienen una fecha asignada en ninguna de sus propiedades.

![image](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/64391652-1d8f-4701-8df2-d0e0bfd00319/ver-sin-fecha/w=1920,quality=80)

## Listas

El último tipo de bases de datos que veremos es el de tipo Lista. Y es el último porque es el más minimalista de todos. Este tipo de visualización puede resultarnos muy útil cuando queremos **centrarnos únicamente en el nombre del ítem y, quizá, una o dos propiedades asignadas a él que nos ayuden a contextualizarlo.**

Que sea minimalista no la hace menos útil ya que, recuerda, es sólo una visualización. Dentro de cada ítem (o páginas) pueden seguir existiendo multitud de propiedades que amplíen las funcionalidades y el contexto de dicha página, pero en ocasiones nos valdrá mucho más visualizar las cosas con pocos datos que nos distraigan, y para eso este tipo de base de datos es la mejor.

Como en cualquier otra base de datos, podrás elegir qué propiedades visualizar en el menú `Properties` de la parte superior de la lista o, si es `Inline`, bajo el menú `...` y, como en cualquier otra base de datos, podrás reordenar los ítems simplemente pinchando y arrastrándolos arriba o abajo. Así mismo, todas las opciones de ordenación o de filtrado siguen aplicando.

Es, en definitiva, sólo una manera condensada de mostrar la misma información. Pruébala para tus notas o borradores 😉



![](https://www.youtube.com/watch?v=4o6mJNhXuMk)



___

Links:

%%
Vínculos:
[[000-Menú Notion📃|Menú Notion]] , [[005-Introducción a las bases de datos|Introducción a las bases de datos]] , [[006-Filtros, opciones de ordenación y visualización|Filtros, opciones de ordenación y visualización]]

tags:
#notion #guia #pagnotion #base_de_datos #Tablas #tableros #listas #galerías #calendarios #board