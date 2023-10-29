---
ID:: 012
-nombre:: "La propiedad Rollup"
-tags:: #notion #guia #pagnotion #rollup #fórmula 
---
___
# La propiedad "Rollup"
La propiedad `Rollup` es una propiedad dependiente de la de `Relation`; es decir, no vas a poder crear ningún `Rollup` de nada sin no tienes previamente una relación creada con otra base de datos. Esto es así porque la finalidad de la propiedad `Rollup` es "extraer" los datos de las bases de datos relacionadas y operar con ellos.

Por continuar con nuestro ejemplo de **Proyectos** y **Tareas**, creando una propiedad `Rollup` en la base de datos de **Proyectos** que "llamara" a las propiedades de la base de datos de **Tareas**, podríamos por ejemplo ver, en la base de datos de **Proyectos**, cuántas tareas tenemos en total en esa otra base de datos. O cuántas de estas tareas han sido completadas.

# Cómo crear un rollup

Como decíamos arriba, lo primero para que una `Rollup` funcione es que exista una propiedad `Relation` creada y que haya otra base de datos enlazada. En nuestro caso, ya tenemos la base de datos de **Tareas** relacionada con nuestra base de datos de **Proyectos**, así que en esta misma crearemos una nueva propiedad, esta vez del tipo `Rollup`, y le pondremos un nombre, por ejemplo "🔍**Progreso**", ya que vamos a usarla para conocer el progreso de las tareas que componen cada proyecto.

Una vez creada la propiedad, cuando pinchemos en la columna correspondiente, se abrirá un menú con tres desplegables distintos:

![image|600](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/664e50f6-06b1-443b-9759-b5a42a4e2773/Untitled/w=3840,quality=80)

- `Relation`. Aquí tienes que seleccionar de cuál de las propiedades relacionadas con la otra base de datos quieres extraer la información. En nuestro caso, como queremos saber el porcentaje de tareas completadas, elegiremos la propiedad a la que hemos llamado "**↗️Tareas"**
- `Property`. Aquí es donde elegiremos de qué propiedad queremos que use los datos para realizar la operación. En este caso, la propiedad de la que queremos saber es la propiedad de checkbox a la que habíamos llamado " 🔲**Hecha?**"
- `Calculate`. La operación que queremos hacer con esos datos extraídos. En este caso, como hemos seleccionado una propiedad de tipo `Checkbox`, nos dejará seleccionar una serie de opciones entre las cuales elegiremos "Percent checked"

Haciendo esto, en nuestra base de **Proyectos** ahora veremos el progreso de cada uno de ellos basándonos en el porcentaje de tareas pertenecientes a ese proyecto que están ya completadas.

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/26b28426-82d9-4e96-b2cd-22c7d445df77/rollups_y_progreso_de_tareas/w=3840,quality=80)

# Tipos de rollup

Una vez has extraído los datos que quieras de la propiedad elegida de otra base de datos, cómo has visto, podremos operar con esos datos. Notion nos permite hacer bastantes cálculos usando los rollup.

- `Show Original`: Muestra las páginas relacionadas con esa base de datos que existen en esa misma celda. Marcar esta opción muestra lo mismo que el indicador de la propiedad `Relation`.
- `Count All`: Cuenta todos los ítems que hay en esa propiedad seleccionada.
- `Count Unique Values`: Igual que la anterior pero sólo cuenta el número de ítems únicos.
- `Count Empty`: Cuenta el número de páginas relacionadas cuyo valor, en esa propiedad seleccionada, está vacío.
- `Count Not Empty`: Como la anterior pero, en vez de contar las vacías, cuenta las páginas que tienen un valor en ese campo
- `Percent Empty`: Igual que `Count Empty` pero en vez de mostrar un número muestra un procentaje.
- `Percent Not Empty`: Igual que `Count Not Empty` pero en vez de mostrar un número muestra un procentaje.

Luego existen una serie de rollups que sólo estarán disponibles si la operación que queremos hacer es sobre una propiedad de tipo numérico (`Number`):

- `Sum`: Suma el valor de las propiedades de tipo numérico de las páginas relacionadas.
- `Average`: Saca la media de las propiedades de tipo numérico de las páginas relacionadas.
- `Median`: Encuentra la mediana de las propiedades de tipo numérico de las páginas relacionadas.
- `Min`: Muestra el número más pequeño de las propiedades de tipo numérico de las páginas relacionadas.
- `Max`: Muestra el número más alto de las propiedades de tipo numérico de las páginas relacionadas.
- `Range`: Muestra el rango entre el número más alto y el más bajo de las propiedades de tipo numérico de las páginas relacionadas.

Y, por último, existen algunos rollups que sólo aparecerán cuando actuamos sobre propiedades de tipo `Date`:

- `Earliest Date`: Muestra la fecha más temprana de las propiedades de tipo fecha de las páginas relacionadas.
- `Latest Date`: Muestra la última fecha de las propiedades de tipo fecha de las páginas relacionadas.
- `Date Range`: Muestra el rango de fechas (es decir, el número de días) entre la fecha más temprana y la última fecha de las propiedades de este tipos que se encuentren en las páginas relacionadas.

## Hacer operaciones con rollups

Al igual que Notion nos permite hacer operaciones directamente en nuestras bases de datos sin necesidad de introducir la propiedad de `Formula` (como ya vimos en la lección [[008-Hacer cálculos, crear templates y enlazar bases de datos|Hacer cálculos, crear templates y enlazar bases de datos]] podremos hacer exactamente lo mismo pero con los rollups.

Recuerda que esta funcionalidad sólo podrás usarla en las bases de datos de tipo Tabla y Tablero, y que se "activa" simplemente pasando el ratón por encima del final de la columna, en el caso de las `Tablas`, y por encima del número gris en el caso de los `Tableros`.


![](https://www.youtube.com/watch?v=e6Re1I0p46I)

___

Links:

%%
Vínculos:
[[000-Menú Notion📃|Menú Notion]] , [[008-Hacer cálculos, crear templates y enlazar bases de datos|Hacer cálculos, crear templates y enlazar bases de datos]]

tags:
#notion #guia #pagnotion #rollup #fórmula 