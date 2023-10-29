---
ID:: 008
-nombre:: "Hacer cálculos, crear templates y enlazar bases de datos"
-tags:: #notion #guia #pagnotion #base_de_datos #tablas #enlazar #templates #cálculos #funciones
---
___
# Hacer cálculos, crear templates y enlazar bases de datos

## Cálculos en nuestras bases de datos

En las bases de datos del tipo Tabla o Tablero, podremos además realizar operaciones con la información que contengan nuestros ítems.

- Para ver esta opción en una `Table`, basta con pasar el ratón por encima de la parte inferior de tu tabla o tablero, verás que aparece la palabra `Calculate` debajo de cada una de las columnas de tus propiedades,
- En un `Tablero`, esta opción está escondida al lado del nombre de la propiedad que estés usando como referencia para crear las columnas. Verás que, por defecto, al lado de este texto hay un número gris. Si pinchas en él, se abrirá un menú con diferentes opciones.

Este menú desplegable te permitirá una serie de opciones de cálculo:

- `Count All`: Cuenta el número de ítems en esa columna o fila.
- `Count Values`: Abrirá un desplegable con todas las propiedades de tu base de datos y contará el número de valores de la propiedad que elijas. Por ejemplo, si tienes una propiedad de `File`, podrás saber cuántos ítems tienen subido un archivo.
- `Count Unique Values`: Cuenta el número de veces que se ha usado un valor en una propiedad determinada sin tener en cuenta duplicados : Por ejemplo, el número de tareas asignadas a personas.
- `Count Empty`: Cuenta el número de filas que no tienen un valor en esa columna. Por ejemplo ver el número de tareas que no están asignadas.
- `Count Not Empty`: Cuenta el número de filas en las que esa columna está "rellena". Por ejemplo ver el número de tareas que ya están asignadas.
- `Percent Empty`: Te devuelve el porcentaje de filas que no tienen esa propiedad rellenada. Por ejemplo, en una lista de tareas podríamos ver el porcentaje de tareas no completadas atendiendo a si su propiedad `Checked` no está marcada.
- `Percent Not Empty`: Igual que el anterior pero al revés, nos dará el porcentaje de ítems que no tienen esa propiedad rellena. Por ejemplo, podríamos saber el porcentaje de tareas completadas.
- `Earliest Date`: Si tu base de datos tiene propiedades de `Fecha` como `Last Edited` or `Created Time`, puedes elegir la opción de que te muestre cuando fue creado el ítem más antiguo, y así tener una idea de cuánto tiempo llevan esa tarea "colgando" en esa base de datos.
- `Latest Date`: Indica cuando fue creado el último ítem de esa base de datos, muy útil para saber lo actualizada que está la base de datos.
- `Date Range`: Muestra el tiempo transcurrido entre el primer ítem que fue creado y el último.

Si en tus bases de datos hay ítems con propiedad de `Number`, podremos además hacer una serie de cálculos adicionales:

- `Sum`: Suma los números de esa columna.
- `Average`: Muestra la media de los números de la columna.
- `Median`: Muestra la mediana de los números de esa columna.
- `Min`: Te indica el número más bajo de esa columna. 
- `Max`: Indica el número más alto de la columna.
- `Range`: Resta el número más bajo al más alto.

## Templates dentro de bases de datos

Cuando creamos bases de datos, normalmente suele ser porque **los ítems o páginas que creamos dentro responden todos a una misma estructura**. Piensa por ejemplo en una base de datos de películas; todas tendrán un título, un director/a, una duración, calificación, etc... Para evitar que, por cada nuevo registro en nuestra base de datos, tengamos que volver a escribir siempre el mismo contenido, tenemos la opción de crear templates dentro de las mismas bases de datos.

☝

Si recuerdas, los templates eran **plantillas con un contenido ya predefinido que podíamos crear nosotros para ahorrarnos escribir lo mismo una y otra vez en documentos que responden siempre a una misma estructura**. En **[este video](https://youtu.be/VVz6AwlX9Ug?t=654)** te explicaba cómo puedes crear botones que generen automáticamente ese contenido repetido en tus páginas.

Para crear un template en una base de datos, tenemos dos opciones:

- Pulsando en la flecha hacia abajo del botón azul de `New` en la parte superior derecha de nuestra base de datos. Esto abrirá un desplegable donde, una vez vayas creando templates, residirán todas ellas. Por el momento, como no tendrás ninguna creada, tendrás que pinchar en `+ New template`.
![image](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/15fb0646-fbe0-4228-8e76-545b2741e50d/new-template/w=1920,quality=80)

- Al abrir uno de los ítems de la base de datos recién creado, este estará vacío y, en el cuerpo de texto, veremos una opción que nos invita a crear un nuevo template.

Una vez estás dentro de este template, puedes escribir lo que quieras y añadir el contenido que quieras. Puedes definir las propiedades fijas que quieras que tenga esa página, las secciones del contenido, etc.

Por ejemplo, es posible que, para el trabajo, te interese tener un template para todas las reuniones. Este template tendría, en todos los casos, una propiedad de fecha y otra de personas. También tendrá una lista de temas a tratar, una sección de "Próximos pasos", etc. Rellenando esta página con ese contenido y, posteriormente, dándole un nombre, tendrás siempre disponible en tu base de datos de reuniones una plantilla ya preconfigurada con la estructura típica de una reunión.
![image](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f3326238-5bad-47e2-9d99-b7f23062c9fa/template/w=1920,quality=80)

### Editar, compartir y marcar templates como favoritos.

Para editar un template ya creado, puedes volver al botón `New` que veíamos al principio y pulsar en la flecha hacia abajo para que se abra el desplegable donde están todas tus templates. Pasa el ratón por encima de la que quieras editar y aparecerá un menú `...` desde el cual puedes eliminar el template, duplicarlo o editarlo.

Cuando lo edites, saldrá un mensajito amarillo en la parte superior de la página que te indica que estás editando un template, para que no edites plantillas por error. Todos los cambios que realices en tu página desde ese momento, se aplicarán en el template y se harán efectivos la próxima vez que crees uno.

Puedes crear tantos templates como desees por cada base de datos. Eso si, cada base de datos tendrá sus propios templates y no puedes reutilizarlos en otras bases de datos o en otros espacios.

Si que podrás compartir tus templates con el botón de `Share` con otros miembros de tu equipo o invitados y, además, desde el mismo menú `...` podrás marcar un template como Favorito, que se quedará automáticamente pinneado en tu sección de `Favorites` del sidebar. Así, siempre que pinches en esa página, se te abrirá automáticamente una página ya pre-rellenada que se creará automáticamente en su base de datos correspondiente.

## Enlazar bases de datos

Por último, pero no menos importante, otra de las cosas que podemos hacer con las bases de datos es **enlazarlas para poder visualizarlas en diferentes puntos de nuestro espacio de trabajo.** Esta funcionalidad es realmente interesante porque **nos evitará tener que estar moviéndonos y cambiando de páginas constantemente cuando queremos consultar datos**. Podemos tener, por ejemplo, una base de datos de tipo tabla con un plan de contenidos en una página de Marketing pero queremos poder consultar esa misma base de datos estando en la página de Diseño. Y además queremos poder verla en modo calendario.

Para esto, usaremos el bloque `Linked Database`, uno de los últimos bloques que nos quedaba por ver.

- Escribe `/linked` y pulsa `Enter`
- Escribe el nombre de la base de datos que quieres enlazar en esa otra página.
- Cambia la visualización de esa base de datos a la que necesites. En este caso, como queríamos ver el plan de contenidos en modo `Calendario`, lo cambiaríamos a este tipo de vista
- De la misma manera, podremos jugar con los filtros y las opciones de ordenación para que la misma base de datos nos muestre la información de la manera que necesitemos dependiendo del contexto.

Alternativamente a esta opción, como las bases de datos también son bloques, otra manera de enlazar a ellas en otra página es, sencillamente, pinchar en el menú **`⋮⋮`** que aparece a la izquierda de la tabla, pulsar la opción `Copy link` y pegar ese enlace allá donde queramos enlazar la tabla. Nos saldrá un mensajito y sólo tendremos que pinchar en `Create linked database` para que nuestra base de datos aparezca "incrustada" en esa página.



![](https://www.youtube.com/watch?v=a3HjQhB0UVI)


___

Links:

%%
Vínculos:
[[000-Menú Notion📃|Menú Notion]] , [[005-Introducción a las bases de datos|Introducción a las bases de datos]] 

tags:
#notion #guia #pagnotion #base_de_datos #Tablas #enlazar #templates #cálculos #funciones