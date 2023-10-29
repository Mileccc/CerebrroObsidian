---
ID: 15
-nombre: Instalar la interfaz de usuario web de difusión estable de AUTOMATIC1111 en Windows (GPU NVIDIA)
"-tags:":
---
___
# Instalar la interfaz de usuario web de difusión estable de AUTOMATIC1111 en Windows (GPU NVIDIA)
**a WebUI de Stable Diffusion de AUTOMATIC1111** es la forma más popular y rica en funciones de ejecutar Stable Diffusion en su propia computadora.

Tiene la comunidad más grande de cualquier front-end de Stable Diffusion, con casi 100.000 estrellas en su [repositorio de Github](https://github.com/AUTOMATIC1111/stable-diffusion-webui) .

En esta guía, lo pondremos en funcionamiento con AUTOMATIC1111 para que pueda comenzar a [solicitar](https://aituts.com/stable-diffusion-prompts/) su [el modelo de](https://aituts.com/models/) elección .

Al final de esta guía, veremos un ejemplo que produce esta imagen con el **modelo Stable Diffusion V1.5** que viene con la instalación de forma predeterminada:
![[Pasted image 20230924123350.png]]

Si su configuración funciona correctamente, podrá recrear **esta imagen exactamente** .

**==Esta guía es para GPU NVIDIA.==** Aquí tienes la guía para [las GPU de AMD](https://aituts.com/stable-diffusion-amd/) , para las que no existe soporte oficial.

## Requisitos

Es necesario cumplir con los siguientes requisitos.

- 16 GB de RAM
- GPU NVIDIA (GTX 7xx o posterior) con al menos 2 GB de VRAM
- Linux o Windows 7/8/10/11+
- Al menos 10 GB de espacio en disco

## Método de un clic

**Este método solo funcionará en Windows 10/11.** Para versiones anteriores de Windows, [desplácese hacia abajo hasta el método alternativo](https://aituts.com/stable-diffusion-on-windows-automatic1111/#alternate) .

### Paso 1: Descargar

Descargar [sd.webui.zip](https://github.com/AUTOMATIC1111/stable-diffusion-webui/releases/tag/v1.0.0-pre)extraiga el archivo zip.

### Paso 2: actualizar

Abra la carpeta extraída. Haga doble clic `update.bat`para actualizar la interfaz de usuario web a la última versión (si recibe una advertencia de seguridad, haga clic en el botón "Ejecutar de todos modos"). Cierra las ventanas cuando termines.

![[Pasted image 20230924123848.png]]

### Paso 3: instalar

Haga doble clic en `run.bat`script para iniciar la interfaz de usuario web, durante el primer lanzamiento.

La primera vez que inicie esto, le llevará un tiempo descargar todos los paquetes necesarios. Este paso también descargará el modelo Stable Diffusion v5.1.

![[Pasted image 20230924123936.png]]

Después de que todo se haya descargado e instalado correctamente, deberías ver un mensaje " `Running on local URL: http://127.0.0.1:7860`".

Abra su navegador y vaya a la dirección que aparece en este éxito. para mi lo es [http://127.0.0.1:7860](http://127.0.0.1:7860)(el tuyo puede ser diferente).

## Metodo alternativo

Pase a la [siguiente sección](https://aituts.com/stable-diffusion-on-windows-automatic1111/#test) si su instalación está funcionando.

### Paso 1: instalar Git

Vaya al [sitio web oficial de Git](https://git-scm.com/download/win) para descargar Git.

Obtenga el **instalador independiente** . Elija el instalador de Git apropiado para su sistema operativo Windows.

![[Pasted image 20230924124111.png]]

Abra el .exe que acaba de descargar. Haga clic en **Siguiente** para aceptar la licencia.

![[Pasted image 20230924124124.png]]

Las opciones predeterminadas están completamente bien. Haga clic en **Siguiente** .
![[Pasted image 20230924124136.png]]

Se le darán _muchas_ pantallas de opciones. Los valores predeterminados están todos bien. Haga clic en **Siguiente** para todos ellos. Git se instalará.

![[Pasted image 20230924124149.png]]

### Paso 2: instalar Python

Instale Python desde el [sitio oficial](https://www.python.org/downloads/windows/) . Quieres la última versión de 3.10. Asegúrese de elegir la versión correcta, 32 bits o 64 bits.

**Importante:** en el asistente de instalación, asegúrese de marcar " `Add python.exe to PATH`".

![[Pasted image 20230924124206.png]]

### Paso 3: descargue la interfaz de usuario web

Presione la **tecla del teclado de Windows** o haga clic en el **ícono de Windows (ícono de Inicio)** . Buscar " `Command Prompt`" y haga clic en la aplicación Símbolo del sistema cuando aparezca.

![[Pasted image 20230924124225.png]]

Deberías ver una línea como esta:

`C:\Users\YOUR_USER_NAME`

![[Pasted image 20230924124239.png]]

Utilice este comando para moverse a la carpeta:

![[Pasted image 20230924124254.png]]

Utilice este comando para hacer una copia de seguridad de una carpeta:

![[Pasted image 20230924124305.png]]

Utilice este comando para enumerar todas las carpetas dentro de la carpeta en la que se encuentra:

![[Pasted image 20230924124317.png]]

Como ejemplo, instalaré Stable Diffusion en mi `Documents` carpeta. Yo escribiría este comando:

![[Pasted image 20230924124326.png]]

![[Pasted image 20230924124334.png]]

Cuando esté en la carpeta en la que desea instalar Stable Diffusion, copie y pegue el siguiente comando:

![[Pasted image 20230924124346.png]]

Dale algo de tiempo a la interfaz de usuario web para que se descargue:

![[Pasted image 20230924124357.png]]

Una vez completada la descarga, podrás ver tu nuevo `stable-diffusion-webui`en el Explorador de Windows:

![[Pasted image 20230924124411.png]]

Ahora para configurar sus ajustes de VRAM. Es posible que encuentre errores de "memoria insuficiente" si no lo hace correctamente.

Comprueba cuánta VRAM tienes escribiendo "dxdiag" en la barra de búsqueda y haciendo clic en dxdiag, que es la herramienta de diagnóstico de DirectX. Su VRAM aparecerá en Display Memory en la pestaña Display (o Display 2):

![[Pasted image 20230924124434.png]]

Agregue el comando que necesita después del `set COMMANDLINE_ARGS=`línea. Por ejemplo:

![[Pasted image 20230924124450.png]]

2 GB de VRAM o menos, necesitarás usar `--lowvram`  
4 GB de VRAM o menos, necesitarás usar `--medvram`  
**Más de 4 GB de VRAM, ¡sáltate esta parte!**

¡Eso es todo lo que tienes que hacer con la WebUI!

### Ejecute la interfaz de usuario web

En el `stable-diffusion-webu`En la carpeta hay un archivo llamado ' `webui-user.bat`'. Haga doble clic en esto:

La interfaz de usuario web tardará varios minutos en instalar los módulos necesarios. Este paso también descargará el modelo Stable Diffusion v5.1.

![[Pasted image 20230924124530.png]]

Cuando termine verás la línea: `Running on local URL: http://127.0.0.1:7860`.

## Probando su primer mensaje
Así es como se verá su interfaz:

![[Pasted image 20230924124922.png]]

Notarás que en la parte superior hay un interruptor llamado “Stable Diffusion Checkpoint”.

Puedes usar esto para cambiar a cualquiera de los modelos que hayas colocado en el `stable-diffusion-webui/models/Stable-diffusion`carpeta.

Consulte esta [lista de modelos populares](https://aituts.com/models/) y esta lista de [modelos de anime populares](https://aituts.com/anime-models/) .

Para nuestro ejemplo, usaremos Stable Diffusion v1.5. El nombre del archivo es `v1-5-pruned-emaonly.safetensors` `[6ce0161689]`.


**Ingrese el mensaje:**

```
portrait of beautiful girl, brown hair, freckles, tshirt, professional lighting, indoor, artistic photography
```

**Ahora ingrese el mensaje negativo:**

```
lowres, bad anatomy, bad hands, text, error, missing fingers, extra digit, fewer digits, cropped, worst quality, low quality, normal quality, jpeg artifacts,signature, watermark, username, blurry, artist name
```

Establezca el control deslizante de height en **768** y mantenga el ancho en 512 para crear una relación de aspecto más agradable y adecuada para retratos.

Selecciona el [Seed](https://aituts.com/stable-diffusion-seed/)a `3463`para asegurarse de obtener el mismo resultado.

Luego haga clic `Generate`! Esto es lo que obtengo:

![[Pasted image 20230924125350.png]]

![[Pasted image 20230924125400.png]]

Tenga en cuenta que estoy usando el muestreador predeterminado. `Euler a`. Puedes jugar con estos samplers para tener una idea de lo que hacen.

Consulte la [wiki oficial](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Features) para conocer todas las funciones que se han implementado en AUTOMATIC1111. A continuación se ofrece una [descripción general de estas funciones con ejemplos](https://aituts.com/stable-diffusion-start/) .

Puede consultar estas indicaciones básicas sobre dónde llegar a continuación:

- [Guía de indicación de difusión estable](https://aituts.com/stable-diffusion-prompts/)

También recomiendo experimentar con modelos populares:

- [lista de los modelos de difusión estable más populares](https://aituts.com/models/) 


___
%%
Vínculos:
[[000-Menú Stable Diffusion XL 📃|Menú Stable diffusion XL]]

tags:
#pagstable_diffusion_xl #stable_diffusion_xl #stable_diffusion 
%%