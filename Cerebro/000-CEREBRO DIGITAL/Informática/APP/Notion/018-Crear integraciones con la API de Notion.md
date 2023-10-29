---
ID:: 018
-nombre:: "Crear integraciones con la API de Notion"
-tags:: #notion #guia #pagnotion #api #integración #token
---
___
# Crear integraciones con la API de Notion
## Una aclaración sobre las integraciones con otras aplicaciones

Si te has dado un paseo por internet, te habrás dado cuenta de que a la hora de hablar de conectar aplicaciones, se usa mucho la palabra "_integration_" pero, ¿Qué es realmente esto, para qué nos sirve y cómo podemos crear nosotros una para empezar a jugar?

Una integración es la manera que tiene una API de conectarse con otra. Esta conexión se realiza a través de un **bot**, un usuario virtual al que invitaremos a nuestros proyectos y que será el encargado de extraer o insertar los datos de las páginas o bases de datos a las que le demos acceso. Así que, de ahora en adelante, cuando veas que se habla sobre "integration", puedes pensar en ese compañero virtual.

## Crear una integración en Notion (crear el bot)

Para crear nuestra primera integración en Notion, tendremos que hacer lo siguiente:

- En la barra lateral, busca `Settings & Members` > `Integrations`
- Aquí verás todas las integraciones que hayas instalado en ese espacio. Si esta es tu primera incursión a la API de Notion, no tendrás ninguna ;)
- Haz click en `Develop your own integrations`

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/aea1bcf3-4899-4cf1-8cca-b1dd72075bd5/CleanShot_2021-05-16_at_16.55.012x/w=3840,quality=80)

- Se abrirá la página de [`My Integrations`](https://www.notion.so/my-integrations), un espacio dedicado a crear y, posteriormente, a gestionar las integraciones que vayas creando.

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f3d087b3-771c-4ad6-8e43-193ffe4c34c9/Untitled/w=3840,quality=80)

Aquí es donde puedes configurar tu bot. Como ves, es muy sencillo, basta con ponerle un nombre, una imagen y, muy importante, decidir **a qué espacio de trabajo** va a tener acceso ese bot. (Esto sólo es relevante si tienes más de uno, pero asegúrate de estar en aquel al que quieres "invitar" al bot)
![image|600](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4fb4cc52-3176-460f-b3c1-3fe81234901f/Untitled/w=1080,quality=80)

Una vez has configurado la integración, se te abrirá esta página con los detalles de la misma:

- `Internal Integration Token`: Es la clave que permitirá al bot conectarse con otras herramientas y que estas puedan así leer los datos de nuestras páginas o bases de datos. Es la que tienes que pegar si una herramienta externa te pide el Token de Notion ;)
- `Integration Type`: Por defecto viene marcada Internal Integration ya que, a no ser que seas desarrollador y estés construyendo una integración pública, todas las que crees serán de uso privado.

![image|600](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/005ff183-4a6a-401c-9ae6-8c5c809ec386/CleanShot_2021-05-16_at_17.17.502x/w=1080,quality=80)

Una vez hemos creado nuestra primer integración, verás que si vuelves al apartado `Integrations` ya SI que aparecerá una. Ese bot que acabas de crear.

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/691290d6-366f-4ed6-ae87-a02256f03def/Untitled/w=3840,quality=80)

## Instalar integraciones de otras herramientas

A día de hoy, Notion ha llegado a acuerdos con 3 aplicaciones que ya tienen una integración con Notion. Estas aplicaciones son [Zapier](http://zapier.com), [Typeform](https://www.typeform.com/es/) y [Automate.io](http://automate.io)

Hay dos formas distintas de conectar con ellas.

### Instalación desde la plataforma externa

En el caso de [Automate.io](http://automate.io), al escribir _Notion_ en el campo de búsqueda para crear tu primera automatización, ya te pedirá acceso a tu espacio de trabajo.

![image](https://assets.super.so/6f476e9c-8680-451e-b108-4cc5c7025a30/images/66e71e16-df2a-4bff-9c04-7c2be29288bc/CleanShot_2021-05-16_at_17.59.28.gif?w=1500)

Desde ahí tendrás que elegir qué páginas son a las que das acceso (en mi caso acabé eligiendo todas 😅)

Desde este momento, Notion y [Automate.io](http://automate.io) están conectados y esta última tiene acceso a todas las páginas a las que tú le hayas dado acceso.

Si vuelves ahora a `Integrations`, verás que hay una nueva correspondiente a [Automate.io](http://automate.io)

![image|800](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/345b42ac-737b-40c8-bc16-730326fbdc58/Untitled/w=1200,quality=80)

### Instalación con el token interno

Otras plataformas, como Zapier, en el momento en el que selecciones Notion como una de las herramientas de tu automatización, te pedirán un token interno para poder conectarse a tu espacio de trabajo. Este token es ese que se nos generó cuando creamos nuestro bot, y al que te recuerdo que podrás acceder desde:

- El espacio [`My Integrations`](https://www.notion.so/my-integrations)

![image|600](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/27e80e0a-0a09-40c8-a009-dea1db3365ed/CleanShot_2021-05-16_at_18.15.562x/w=1080,quality=80)

- A través de `Settings & Members` > `Integrations` .

- Allí verás el bot que has creado al principio (es al que le pusiste el nombre y está etiquetado como Internal) → Selecciona los tres puntos `...` y `Copy internal Integration Token`

![image|600](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e35a8fb7-6bc7-41fb-8cc3-582e83544850/Untitled/w=1080,quality=80)

- Pega esta clave cuando la plataforma te lo pida (normalmente al ir a crear una automatización). Esto es lo que permitirá que su servicio y tu bot interactúen.

# Invitar al bot a nuestras páginas

En el caso de que la herramienta en cuestión no nos haya hecho seleccionar las páginas a las que queremos darle acceso, tendremos que "invitar" manualmente a nuestro bot a las páginas o bases de datos que queramos conectar a esas otras plataformas de terceros.

Como, a fin de cuentas, este bot era como un usuario virtual, le invitaremos igual que haríamos con cualquier compañero de equipo.

- Vamos a la página que queramos conectar y pinchamos en `Share`
- Hacemos click en `Add people, emails, groups, or integrations`

![image|600](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4f13380f-c6a1-4150-bf00-b4c54cd48391/CleanShot_2021-05-16_at_18.34.382x/w=1200,quality=80)

- Se nos abrirá una ventana con las demás personas que tengan acceso a alguna parte de nuestro espacio de trabajo (si es que has añadido alguna en algún momento) y, más abajo, verás tus integraciones bajo el título `Select and Integration`
![image|600](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/af8b2052-1253-4140-9da4-a2b28ed26ec2/Untitled/w=1080,quality=80)

- Selecciona la integración (o bot) que quieras invitar a esta página.
- Una vez hecho, verás esa nueva integración en el menú `Share` de esa página. Esto quiere decir que el bot ya tiene acceso a la misma y está listo para conectarse con otras herramientas 😊

![image|600](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a1382c33-73d1-4d76-8e52-669cd97baf13/Untitled/w=1080,quality=80)


___

Links:

%%
Vínculos:
[[000-Menú Notion📃|Menú Notion]] 

tags:
#notion #guia #pagnotion #api #integración #token
%%