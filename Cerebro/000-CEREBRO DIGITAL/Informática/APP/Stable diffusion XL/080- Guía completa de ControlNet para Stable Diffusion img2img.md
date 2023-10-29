---
ID: 80
-nombre: Guía completa de ControlNet para Stable Diffusion img2img
"-tags:":
---
___
# Guía completa de ControlNet para Stable Diffusion img2img

¿Qué es exactamente ControlNet y por qué los usuarios de Stable Diffusion están tan entusiasmados con él?

**Piense en la función img2img de Stable Diffusion con esteroides.**

Con img2img normal, no tenías control sobre qué partes de la imagen original querías conservar y qué partes querías ignorar.

Con ControlNet, puede elegir _exactamente_ qué partes conservar de la imagen original y cuáles ignorar (los usos prácticos en este momento son controlar **poses** y **composiciones** , pero con el tiempo veremos muchos más modelos y casos de uso).

Puede leer más al respecto en el [repositorio oficial de Github](https://github.com/lllyasviel/ControlNet) y en el [artículo académico](https://arxiv.org/abs/2302.05543) .

¿Qué es posible con ControlNet? Puedes copiar cualquier pose:

![[Pasted image 20230924192633.png]]
_[ghostintheshell107](https://www.reddit.com/r/StableDiffusion/comments/113p99k/using_daz3d_as_pose_generator_for_controlnet/) _utiliza el software_ [Daz3D](https://www.daz3d.com/) _para crear poses y luego aplica ControlNet OpenPose en un modelo llamado RPG para obtener resultados sorprendentes._
_**Diffusion model:** [RPG by Anashel](https://civitai.com/models/1116/rpg)  
**ControlNet Model**: [control_openpose-fp16](https://huggingface.co/webui/ControlNet-modules-safetensors/blob/main/control_openpose-fp16.safetensors)_ _(OpenPose)_

Puede modificar los entornos conservando las características principales del lugar:

![[Pasted image 20230924192739.png]]
_[lokitsar](https://www.reddit.com/r/StableDiffusion/comments/118cdcx/i_swear_ive_seen_this_town_before_controlnet/) hace muchas variaciones de Whiterun de Skyrim  
**Modelo de difusión:** privado_ _(pero similar a [deliberado](https://civitai.com/models/4823/deliberate) )_  
_**Modelo ControlNet** : [control_ Depth-fp16](https://huggingface.co/webui/ControlNet-modules-safetensors/blob/main/control_depth-fp16.safetensors)_ _(Profundidad)_

Puedes convertir los garabatos de un niño (o los tuyos propios) en obras maestras:

![[Pasted image 20230924192826.png]]

_[nyblett](https://www.reddit.com/user/nybbleth/) convierte la "cool S" en algo mucho más genial_

Y, por supuesto, puedes hacer cosas tontas como esta:

![[Pasted image 20230924192858.png]]

_[AaronGNP](https://www.reddit.com/r/StableDiffusion/comments/1197muc/gta_san_andreas_brought_to_life_with_controlnet/) convierte los personajes de GTA: San Andreas_ _en la vida real_  
_**Modelo de difusión:** [RealisticVision](https://civitai.com/models/4201/realistic-vision-v13)_  
_**Modelo ControlNet** :_ _[control_scribble-fp16](https://huggingface.co/webui/ControlNet-modules-safetensors/blob/main/control_scribble-fp16.safetensors) (garabato)_


ControlNet logra esto extrayendo una _imagen procesada_ de una imagen que usted le proporciona.

La imagen procesada se usa para **controlar** el proceso de difusión cuando haces img2img (que usa otra imagen más para comenzar) o txt2img y lo impulsa hacia resultados deseables.

**ControlNet es un hito importante hacia el desarrollo de herramientas de inteligencia artificial altamente configurables para los creadores** , en lugar de la difusión estable de "pedir y orar" que conocemos hoy.

Entonces, ¿cómo puedes empezar a **controlar** las generaciones de tus imágenes?

Empecemos.

## 1. Descargar modelos ControlNet

Descargue primero los modelos ControlNet para poder completar los demás pasos mientras se descargan los modelos.

**Tenga en cuenta que se utilizan por separado de su modelo de difusión.** Lo ideal es que ya tenga un modelo de difusión preparado para usar con los modelos ControlNet.

Si aún no tienes uno, te sugiero un modelo popular como [Deliberate](https://civitai.com/models/4823/deliberate) (propósito general) o [Realistic Vision](https://civitai.com/models/4201/realistic-vision-v13) (personas hiperrealistas).

Vaya a este enlace:

[https://huggingface.co/webui/ControlNet-modules-safetensors/tree/main](https://huggingface.co/webui/ControlNet-modules-safetensors/tree/main)

Puedes elegir modelos específicos o descargarlos todos (estás descargando el `.safetensor`archivos).

Recomiendo adquirirlos todos ya que solo pesan 700 MB~ cada uno. Es posible que veas versiones de 5,5 GB flotando, pero son versiones anteriores y ya no son necesarias.

Si no está seguro de lo que quiere, comience con los **modelos de profundidad** y **apertura** .

Puede probar todos los modelos en línea antes de descargarlos: [https://huggingface.co/spaces/hysts/ControlNet](https://huggingface.co/spaces/hysts/ControlNet)

## 2. Descargue la interfaz de usuario web

Supongo que ya ha descargado la WebUI de difusión estable de AUTOMATIC1111. De lo contrario, siga las instrucciones de instalación para su plataforma y vuelva a este artículo cuando haya terminado.

- Instalación para Windows (NVIDIA GPU): [instrucciones](https://aituts.com/stable-diffusion-on-windows-automatic1111/)
- Instalación para Windows (AMD GPU): [instrucciones](https://rentry.org/sd-nativeisekaitoo)
- Instalación para Apple Silicon (Mac M1/M2): [instrucciones](https://aituts.com/stable-diffusion-mac-m1/)
- Linux: [instrucciones](https://github.com/AUTOMATIC1111/stable-diffusion-webui#automatic-installation-on-linux) [Instalación para](https://rentry.org/linux-sd)

## 3. Descargue la extensión ControlNet

Su WebUI debería estar ejecutándose. Como recordatorio:

- **Windows:** haga doble clic `webui-user.bat`(Archivo por lotes de Windows) para comenzar
- **Mac:** ejecuta el comando `./webui.sh`en la terminal para comenzar
- **Linux:** ejecute el comando `webui-user.sh`para comenzar

Clickea en la pestaña `Extensions`  y en `Install from URL` subpestaña:

Copie y pegue el siguiente enlace en el campo etiquetado: `URL for extension's git repository`y luego presione el botón grande `Install` botón.

```
https://github.com/Mikubill/sd-webui-controlnet
```

![[Pasted image 20230924195603.png]]

Recibirá un mensaje de confirmación cuando se complete la instalación.

Cierre su WebUI (cierre el símbolo del sistema/terminal o presione Ctrl+C) e inícielo nuevamente.

## 4. Coloque los modelos en la carpeta WebUI

Colocar el `.safetensor` modelo/s que has descargado dentro dentro `stable-diffusion-webui\extensions\sd-webui-controlnet\models`.

**Nota** : ¡esto es diferente de la carpeta en la que colocas tus modelos de difusión!

## 5. Usando ControlNet para controlar la red

**Nota:** ControlNet no tiene su propia pestaña en AUTOMATIC1111. En su lugar, aparecerá como una sección propia en la parte inferior de las pestañas txt2img o img2img.

Desplácese hacia abajo y expanda esta sección en la pestaña txt2img o en la pestaña img2img.

To-dos:

- Check " `Enable`"
- Seleccione un Preprocesador y luego seleccione el Modelo correspondiente (por ej. `openpose`& `control_openposer-fp16`)

![[Pasted image 20230924200143.png]]

### img2img

Lo mismo de siempre. Arrastre y suelte la imagen que desea usar en el área de entrada normal de img2img.

Aquí usaré una imagen de Darth Vader:

![[Pasted image 20230924200245.png]]


Luego, desplácese hacia abajo hasta la sección ControlNet. Arrastre y suelte **la imagen de su controlador** en el área de entrada de imágenes de ControlNet.

La imagen del controlador es lo que realmente usará para restringir/controlar el resultado. Lo que estés usando para esta imagen realmente depende del modelo que estés usando.

Por ejemplo, si estás usando el modelo OpenPose, la imagen del controlador contendrá la **pose real que deseas** .

Como ejemplo, voy a utilizar esta imagen de un hombre en un autobús:

![[Pasted image 20230924200516.png]]

En realidad, no verás los píxeles originales de esta imagen del controlador reflejados en la imagen final.

Lo único que importa es qué información procesa el modelo ControlNet que elija de esta imagen (desplácese hacia abajo y haga clic `Preview annotation result`para ver qué información extrapola el modelo ControlNet de la imagen del controlador).

¡Recuerde escribir un mensaje! Estoy tomando algunos elementos temáticos y estilísticos de mi imagen original, usando la imagen ControlNet para controlar la pose y, finalmente, usando el mensaje para llevar las cosas a casa:

```
darth vader sitting on bus looking at his phone wearing black gloves, new york city passing by outside
```

Presione Generar:

![[Pasted image 20230924200743.png]]

![[Pasted image 20230924200802.png]]

Tenga en cuenta que OpenPose es uno de muchos modelos, cada uno con diferentes posibilidades y aplicaciones. ¡Te recomiendo que descargues y pruebes todos los modelos por ti mismo!

Nota: puedes usar tu propio esqueleto y tus propios mapas también, y el modelo respectivo los detectará. Esto puede ayudarte a obtener la pose exacta que deseas sin extraerla primero de una imagen. Recuerde configurar su preprocesador en Ninguno cuando los use o, de lo contrario, se procesarán nuevamente. Más sobre esto a continuación.





























___
%%
Vínculos:
[[000-Menú Stable Diffusion XL 📃|Menú Stable diffusion XL]]

tags:
#pagstable_diffusion_xl #stable_diffusion_xl #stable_diffusion 
%%