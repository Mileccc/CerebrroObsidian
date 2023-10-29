---
ID:: 011
-nombre:: "La propiedad Relation"
-tags:: #notion #guia #pagnotion #relation #relaciones #No_syncing #Sync_both_ways #padre #hijo
---
___

# La propiedad "Relation"

Por fin hemos llegado a la parte que, a mí personalmente, me parece que tiene más interés en todo lo relacionado con las bases de datos en Notion, que es la propiedad para poder **enlazar bases de datos entre ellas,** con la finalidad de **poder relacionar los items de una base de datos con otros y, a partir de ahí, usarlos como quieras.**

# ¿Para qué sirve relacionar unas bases de datos con otras?

A priori, puede que no se te ocurra cómo o por qué usar esta funcionalidad o por qué es tan crucial. Pero piensa por ejemplo que tienes una lista de clientes y una lista de proyectos, y quieres saber qué proyectos corresponden a cada uno de esos clientes. En ese caso, **podrías conectar tu base de datos de Clientes con la de Proyectos y de esta manera ambas estarían relacionadas entre sí**, por lo que al entrar en el registro de uno de tus clientes, en sus propiedades verías —además de las que hubieras creado en esa base de datos— todos los ítems de la base de datos de Proyectos que estarían asociados a ese cliente.

Más ejemplos de bases de datos relacionadas podrían ser:

- Una base de datos de Ingredientes conectada a una base de datos de **Recetas** para ver de qué I**ngredientes** está compuesta cada receta.
- Una base de datos de **Contactos** relacionada con otra base de datos de **Empresas** para tener un control de dónde trabajan cada uno de estos contactos.
- Una base de datos de **Reuniones** con una base de datos de **Clientes** en la que poder ver de manera sencilla todas las reuniones que has tenido con cada uno de tus clientes.
- Una base de datos de **Restaurantes** conectada con otra de **Barrios**, para ver todos los restaurantes de un mismo barrio (puede que esto te suene porque es exactamente lo que estamos haciendo en nuestra práctica de Construir una guía de viajes)

Otra manera de pensar en esta propiedad es con el concepto de "**Contenedor**". La base de datos de clientes contiene una serie de proyectos. Los proyectos pueden a su vez contener tareas. Y estas agrupaciones pueden darse a lo largo de todo tu espacio de trabajo, de tal manera que puedes relacionar clientes con proyectos pero también con recursos, que a su vez pueden estar relacionados con tareas, etc etc.

Esta funcionalidad de **agrupar y relacionar**, combinada con los filtros que ya conocemos, o con los `Rollups` que veremos más adelante, nos abren un amplio mundo de posibilidades de **manipulación y organización dentro de las bases de datos de nuestro espacio de trabajo**, permitiéndonos ver muchas cosas con sólo un par de pasos.

# ¿Cómo se crea una relación entre bases de datos?

Para relacionar bases de datos, aunque suene obvio, necesitarás **por lo menos dos bases de datos**. En este caso vamos a relacionar una serie de tareas con sus proyectos.

Crearemos pues dos base de datos, una de Proyectos y otra de Tareas. Ambas pueden tener, como propiedades, todas aquellas que consideres oportunas. Si no recuerdas o no sabes cómo crear propiedades, dimos ese tema en profundidad en [[005-Introducción a las bases de datos|Introducción a las bases de datos]]

- En la base de datos de **Proyectos**, crearás una nueva propiedad de tipo `Relation` a la que llamarás "**Tareas**"
- En el momento en que crees una propiedad del tipo `Relation`, se te abrirá un mensaje preguntándote a qué base de datos quieres enlazar dicha propiedad. Aquí es donde tienes que elegir la base de datos que quieres que esté conectada con **Proyectos**. En este caso, **Tareas**.
- Al crear esta relación, verás que automáticamente ha creado una propiedad nueva en tu base de datos de **Tareas**, que pondrá algo parecido a `Related to Proyectos (Tareas)` . Cambia el nombre de esta columna a uno más descriptivo (por ejemplo, **Proyectos**)

A partir de ahora, ambas tablas están relacionadas.

Para empezar a crear esos enlaces entre ellas, es tan sencillo como pinchar en una de las columnas que tenían esa propiedad `Relation` y seleccionar el ítem de la otra base de datos que quieres relacionar.

En nuestro ejemplo de **Proyectos** y **Tareas** por cada proyecto nuevo que introdujera, tendría que seleccionar qué tareas lo componen, seleccionándolos de la tabla de **Tareas**.

Según vayas seleccionando **Tareas**, (con el botón de `+`) verás que van apareciendo en su columna correspondiente y, además, como la sincronización funciona en ambas direcciones, verás que en la base de datos de **Tareas** ahora también indica a qué proyecto pertenecen.

![image|800](https://assets.super.so/6f476e9c-8680-451e-b108-4cc5c7025a30/images/22fe8b71-c736-4d81-99fb-b6d6f1b3c25b/crear-relation.gif?w=1500)

# Las páginas relacionadas

Cuando creas una relación entre dos bases de datos, a efectos prácticos, lo que estás haciendo es añadir las páginas que formaban una de las bases de datos a una de las propiedades de la otra. Es decir, desde tu base de datos de **Proyectos**, además de todas las propiedades que pudiera tener esa base de datos, ahora también podrás ver todas las páginas que están relacionadas con ella.

En nuestro ejemplo, desde la base de datos de **Proyectos** podrás ver todas las tareas que pertenecen a ese proyecto. Puesto que, como ya sabemos, cada registro en una base de datos es a su vez una página, podrás abrir esas tareas como páginas normales y llenarlas con el contenido que necesites.

Para abrir una página relacionada en una base de datos, es tan sencillo como pinchar en esta nueva propiedad que se ha creado y seleccionar la página que quieres abrir.

![image|800](https://assets.super.so/6f476e9c-8680-451e-b108-4cc5c7025a30/images/a344ed66-5c84-4684-b544-de3cd9aefd5b/abrir_pagina_relacionada.gif?w=1500)


# Relacionar una base de datos consigo misma
En ocasiones, puede que quieras que los items de una misma base de datos estén a su vez relacionados consigo mismos. En nuestro ejemplo de la base de **Tareas**, podríamos querer que estuvieran relacionadas entre sí. Para hacerlo, deberías relacionar esa base de datos consigo misma.

En Notion, cuando haces esto, puedes elegir cómo quieres que sea esta relación.

- Como **tareas relacionadas**. Se crea solo la propiedad de `Relation` que tu hayas elegido y en esa columna verás las tareas que hayas relacionado. A esto Notion lo llama `No syncing`.
- Como **subtareas de tareas** (o tareas hijo y tareas padre). Se crearán automáticamente dos columnas. En una verás la tarea que has relacionado (digamos que verás la tarea 2, relacionada con la tarea 1) y, en la otra, visualizarás la tarea que ha sido relacionada al lado de aquella tarea con la que la has relacionado (es decir, verás la tarea 2 al lado de la tarea 1). Para diferenciarla de la otra, Notion especifica que en este tipo de relación la sincronización es a los dos lados (`Sync both ways`)

Diferencia ambas maneras de crear esta relación con este gráfico, que te aparecerá siempre que quieras relacionar una base de datos consigo misma así que no te preocupes si se te olvida.

![image|600](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7ae39ff3-3c89-4c1b-a12b-da58512aa53c/Untitled/w=3840,quality=80)

Soy consciente de que esta parte cuesta muchísimo entenderla así leída. A mí me cuesta y es un concepto bastante complicado de pillar sin verlo, así que te lo voy a enseñar con ejemplos para que veas bien la diferencia.

## Tareas relacionadas (la opción fácil)

Si eliges esta opción, que sólo crea una columna. Al relacionar una tarea con otra, simplemente verás al lado de la primera tarea la tarea con la que la has relacionado.

En nuestro ejemplo, yo he relacionado la tarea "Buscar inspiración color paredes" (Tarea 1) con otra tarea de esta misma base de datos y del mismo proyecto "Buscar inspiración salones" (Tarea 2). Como he relacionado la Tarea 1 con la Tarea 2, la columna de **Tareas** relacionadas me muestra la Tarea 2, porque me muestra aquellas tareas que he relacionado.

![image|600](https://assets.super.so/6f476e9c-8680-451e-b108-4cc5c7025a30/images/12496e35-057a-46ad-9dc9-762632bb1c98/tareas_relacionadas.gif?w=1500)

Al ver esto, realmente lo que uno puede pensar es "¿De qué me sirve ver la tarea relacionada de "Buscar inspiración color paredes" si luego no puedo ver que ésta está a su vez relacionada con "Buscar inspiración salones?" "¿No son tareas relacionadas?" "¿No podría ver cómo se relacionan entre sí metiéndome en cada una de ellas (porque ahora mismo, al pinchar en "Buscar inspiración salones", no puedes ver que está relacionada con "Buscar inspiración color paredes")?"

Efectivamente. Para eso está la segunda opción, en la que básicamente hacemos lo mismo, relacionar una tarea con otra, pero en este caso cómo están relacionadas se sincroniza de las dos maneras.

Abajo lo verás mejor 👇🏻

## Subtareas de tareas (o Tareas Padre y Tareas Hijo)

En esta segunda manera, al relacionar la base de datos consigo misma, deberíamos elegir la opción de `Sync Both Ways` que lo que hará será crear una segunda columna adicional automáticamente para suplir aquello que nos faltaba en la opción anterior. Poder ver cómo ambas tareas se relacionan entre sí.

El uso más común de esta funcionalidad es el de saber qué tareas, de todas las que tenemos, están compuestas a su vez de tareas más pequeñas o subtareas. Como se sincronizan a ambos lados, podremos ver las subtareas de una tarea y, a su vez, las tareas padre de estas subtareas.

Para que lo veas en funcionamiento, aquí está el ejemplo:

![image|600](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d013d7e6-75f5-44f8-87b8-705cb928f1ad/tareas_y_subtareas/w=3840,quality=80)

En este caso, al relacionar la base de datos de **Tareas** consigo misma, elegí la primera opción, que crea automáticamente dos columnas de propiedades en vez de una. A una la llamé "**Tarea padre**" y a la otra "**Subtarea**". En este caso, al relacionar la tarea "Buscar inspiración salones" con la tarea "Buscar inspiración color paredes", ésta última me aparece como Subtarea de la primera y, a su vez, en la columna de "**Tarea Padre**", puedo ver que "Buscar inspiración color paredes" tiene como tarea padre a la primera.

Como decía, esta funcionalidad de relacionar bases de datos consigo mismas tendrán casos de uso muy particulares, casi siempre relacionados con tareas y subtareas, ya que en parte es la manera que tiene Notion de cubrir esa funcionalidad, tan común en otras herramientas de gestión de proyectos.

Es probable que no necesites usarlo en tu día a día si usas Notion para cosas más personales pero, si estás acostumbrado a trabajar con tareas y subtareas, entonces por ahora esta es la única manera de hacerlo.



☝🏻**Tip**: Te aconsejo que, si vas a usar esta funcionalidad para gestionar las subtareas dentro de tus tareas, hagas tres cosas:



1️⃣ Marca las subtareas con una pista visual al comienzo de las mismas para saber que son tareas pertenecientes a una tarea mayor. Por ejemplo **→**

2️⃣ Esconde la propiedad de "**Tarea Padre**" para sólo ver las subtareas, ya que si no la vista es bastante confusa y ver esta propiedad no te aportará mucho porque ya puedes ver a qué tareas padre pertenecen simplemente fijándote en su Tarea a la izquierda.

2️⃣ Si todas tus tareas van a tener subtareas, mi consejo es que sencillamente filtres la tabla para que sólo te enseñe aquellos registros cuya propiedad "**Subtarea**" tenga algo dentro. Es decir, que solo te muestre las tareas padre. (esto sería con un filtro con la opción `Subtarea` + `Is not Empty`)

Siguiendo todos estos consejos, nuestra base de datos quedaría así:

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1223a3d6-334c-4bac-bb9e-de4e80265551/Untitled/w=3840,quality=80)


![](https://www.youtube.com/watch?v=PmPDB5BnnOE)

___

Links:

%%
Vínculos:
[[000-Menú Notion📃|Menú Notion]] , [[008-Hacer cálculos, crear templates y enlazar bases de datos|Hacer cálculos, crear templates y enlazar bases de datos]]

tags:
#notion #guia #pagnotion #relation #relaciones #No_syncing #Sync_both_ways #padre #hijo