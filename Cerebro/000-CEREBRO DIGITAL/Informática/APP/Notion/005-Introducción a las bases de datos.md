---
ID:: 005
-nombre:: "Introducción a las bases de datos"
-tags:: #notion #guia #pagnotion #base_de_datos #inline #full_page
---
___

Las bases de datos en Notion son los tipos de bloques más poderosos y que más funcionalidades nos ofrecen ya que nos permiten **estructurar información y visualizarla de diferentes maneras,** así como **categorizarla, filtrarla y hacer que resurja cuando más la necesitamos**, de la manera que más nos convenga en cada contexto.

## Qué hace de las bases de datos en Notion algo especial

Lo que caracteriza a las bases de datos en Notion, y las hace diferentes a las de otras aplicaciones, son esencialmente tres funcionalidades:

1. **Propiedades customizables:** Puedes añadir diferentes propiedades a un ítem que lo complementen con más información o la contextualicen; fechas, URLs, marcas de última edición, dueños, etc. Además de servir para complementar información, podrás usar esas propiedades después para filtrar u ordenar los ítems de tus bases de datos.
2. **Cada ítem que crees en una base de datos es, a su vez, su propia página**. Como todas las páginas en Notion, podrás añadir a ellas bloques, más páginas o más bases de datos.
3. **Diferentes modos de visualización**. Como vimos en lecciones anteriores, existen 5 bloques diferentes de bases de datos, cada uno correspondiente a un tipo;

- `Listas`
- `Tablas`
- `Galerías`
- `Tableros`
- `Calendario`

Pero los datos que introduzcas en estas tablas no tienen por qué ser siempre vistos así, sino que puedes cambiar la visualización y ver una lista como una tabla, una galería como un tablero o una tabla como un calendario. **La información siempre será la misma pero puedes elegir cómo visualizarla dependiendo del contexto**. Así, por ejemplo, puede serte útil crearte una lista de tareas en una tabla para poder ver todas las propiedades en una misma línea pero, en tu día a día, ver esas tareas en un modo de calendario.

## Cómo crear una base de datos

Tenemos diferentes maneras de crear una base de datos en Notion y, dependiendo de cuál elijamos, nuestra base de datos se comportará de manera algo diferente. Por ahora, aquí te cuento todas las maneras:

- Creando una página nueva y, antes de escribir nada, seleccionando una de las opciones debajo de "`DATABASE`"
- De la manera que conocemos ya de lecciones anteriores; En una página ya creada, insertando un nuevo bloque (con la tecla `/`) y eligiendo el tipo de base de datos que queremos insertar:

- Si elegimos nuestra base de datos como opción `Inline`, se creará como un bloque más en la misma página, ocupando el mismo ancho que tenga configurado la página (esto es; con el contenido centrado o full page)
- Si elegimos la opción `Full Page`, automáticamente se creará una página nueva con nuestra base de datos dentro.

Como decía, existe una pequeña diferencia entre las bases de datos `Inline` y las `Full Page`, que te cuento a continuación:

## Diferencia entre bases de datos inline o full page

### Bases de datos Inline

Las bases de datos que crees `Inline`, como su propio nombre indica, **convivirán con otros tipos de contenido en tu página**. Pueden ser muy útiles para insertar datos en documentos que tienen otro tipo de contenido como texto, imágenes o más páginas anidadas.

Debajo, he incluido una prueba de tabla inline para que veas cómo se muestra:

![[Pasted image 20230803203701.png|400]]


Como ves, puedo ver y acceder a los datos de la tabla sin abandonar la página en la que estoy, así que son una opción interesante a usar si necesitas que **los datos que muestren estén contextualizados** con otras bases de datos o con otra información de tu página.

Si la configuración de la página estuviera activada como `Ancho Completo`, la tabla pasaría a ocupar el ancho completo de la página pero seguiría estando en línea con el resto de contenido.

Por supuesto, como todo en Notion, puede convertirse en otra cosa. En este caso, una tabla `Inline` puede convertirse en una tabla `Full Page` simplemente pinchando en `...` y marcando la opción `Turn into Page`. Al hacer esto, esa base de datos se convertirá automáticamente en su propia página y sólo podrá contener a esa base de datos.

### Bases de datos Full page

Esto quiere decir que no podremos añadir más contenido a esa página que se salga de aquel que introduzcamos en la propia base de datos. Como todas las páginas, podremos visualizarla en la barra lateral, en la raíz o subanidada si la hemos creado dentro de otras páginas. También podremos añadir una descripción y "bloquearla" para que nadie haga cambios.

Debajo he creado una base de datos `Full Page` de ejemplo para que veas la diferencia entre estas y las `Inline`.

https://aprendenotion.com/introduccion-bases-datos/media-full-page

Este tipo de bases de datos puede ser útil utilizarlas en los casos en los que **no necesites incluir más contenido en ese documento** salvo el que ya está incluído en la base de datos. No nos servirán para usarlas junto a otras piezas de información a no ser que (como supongo que ya ibas oliéndote) la convirtamos en una base de datos inline. De nuevo, eso se hace pulsando en el menú `...` y clickando en la opción `Turn into Inline` , que convertirá automáticamente nuestra base de datos a página entera en una base de datos que conviva con el resto de contenido, donde podrás escribir, insertar imágenes u otros bloques.

## Propiedades de las bases de datos

Para añadir información que complemente y contextualice la información que tenemos en nuestra base de datos, podemos añadir diferentes propiedades. Notion las divide en `Básicas` y `Avanzadas.`

Las propiedades básicas de las bases de datos son las siguientes:

- `Name`: Aquí es donde eliges cómo quieres llamar a tu ítem principal, y que será el título de esa página. Por ejemplo "Hacer la compra" si estás haciendo una lista de tareas, o el título de tu post si estás montando un calendario de contenidos.
- `Text`: Un campo de texto básico para añadir descripciones o comentarios. El texto que pongas aquí podrás formatearlo, es decir, ponerlo en negrita, con colores o incluso poner enlaces.
- `Number`: En los campos con esta propiedad podrás escribir en formato numérico, con opciones de elegir si quieres que se muestre en porcentajes, con decimales, o el tipo de moneda.
- `Select`: Un menú desplegable para añadir propiedades pero que sólo podrán ser seleccionada de una en una. (Para status o prioridades, casos en los que sólo puede existir una única opción)
- `Multiselect`: Sirve para lo mismo que el `Select`, para hacer una lista de propiedades que pueden servir como tags, pero en este caso podrás seleccionar más de una. Un caso de uso muy común sería el de listar categorías.
- `Date`: Nos permitirá introducir una fecha, que puede ser un sólo día concreto o un rango y que, como en las fechas que vimos anteriormente, nos permitirá añadir recordatorios.
- `Person`: Para asignar ese ítem de tu base de datos a personas que compartan tu mismo espacio de trabajo o, en su defecto, simplemente mencionarlas para que les llegue una notificación.
- `Files & Media`: Esta propiedad nos permitirá subir archivos a nuestra base de datos, bien enlazados o desde nuestro ordenador.
- `Checkbox`. La propiedad de checkbox que todos conocemos y que nos sirve para indicar si algo está hecho o no. Esta propiedad posteriormente nos será útil, no solo para visualizar tareas completadas, libros leídos o cualquier otro uso que quieras darle, sino para ver el progreso de proyectos. Pero esto será más adelante 😉
- `URL`: Para poner enlaces en tus bases de datos
- `Email`: Acepta direcciones de email que, al pincharlas, abren tu cliente de correo para escribir
- `Phone`: Igual que en el campo de email, al escribir aquí un teléfono y pinchar, se abrirá automáticamente la aplicación de llamadas de tu ordenador o teléfono.

### Propiedades avanzadas

Además de estas propiedades básicas, Notion separa unas a las que llama "Avanzadas" y que son las siguientes:

- `Created Time`: Al añadir esta propiedad, automáticamente se creará un timestamp que indique la fecha de creación de ese ítem
- `Created by`: Automáticamente registra la persona que ha creado ese ítem
- `Last Edited Time`: Si añadimos esta propiedad, cada vez que esta página se edite, quedará marcada la fecha en la que tuvo lugar esa última edición.
- `Last Edited By`: Igual que en el caso anterior, al añadir esta propiedad podremos saber quién fue la última persona que editó esa página.

Las otras tres propiedades avanzadas que podremos añadir en nuestras bases de datos son mis favoritas, y son tan potentes que dedicaré una sección entera, con sus videos correspondientes, a ellas, pero para que sepas de qué van, te dejo un mini avance:

- `Relation`: Al añadir una propiedad relation podremos enlazar bases de datos entre ellas para añadir los ítems que queramos de unas bases de datos a otras.
- `Rollup`: Con esta propiedad podremos realizar operaciones sobre los ítems que nos hayamos "traído" de esas otras bases de datos.
- `Formula`: Como su propio nombre indica, al añadir esta propiedad podremos realizar cálculos o desencadenar acciones basándonos en otras propiedades de nuestra base de datos. Esta propiedad nos será muy útil para vitaminar un poco nuestras bases de datos y ponerlas realmente a funcionar para nosotros.

Todas las propiedades que vayamos creando en una base de datos, podremos organizarlas (reordenarlas, mostrarlas, esconderlas o crear nuevas) desde el menú `...` en la parte superior derecha de la base de datos en caso de que esta sea `Inline` o, directamente desde `Properties` en las bases de datos `Full Page`.

Además, en ambos casos podremos crear filtros, especificar criterios de ordenación y elegir cómo queremos visualizar dichas bases de datos.

![](https://www.youtube.com/watch?v=FCn92JBS3Dk)


___

Links:

%%
Vínculos:
[[000-Menú Notion📃|Menú Notion]] , [[003-Bloques|Bloques]], [[006-Filtros, opciones de ordenación y visualización|Filtros, opciones de ordenación y visualización]], [[007-Diferentes bases de datos y particularidades|Diferentes bases de datos y particularidades]]

tags:
#notion #guia #pagnotion #base_de_datos #inline #full_page