---
ID: 3
"-nombre:": Descripción general y manual
"-tags:":
---
___
# Descripción general y manual
Stable Diffusion es una poderosa herramienta para la generación de imágenes, pero hay tantas maneras de usarla y tantos complementos que es difícil saber por dónde empezar.

Esta serie es para usted si ha oído hablar de Stable Diffusion y tiene una idea general de lo que es capaz de hacer, pero no tiene idea de cómo empezar.

Esta es la Parte 1 de la serie Difusión estable para principiantes:

## ¿Qué es la ## Stable Diffusion?

Stable Diffusion es un modelo de generación de imágenes lanzado por StabilityAI el 22 de agosto de 2022.

Es similar a otros modelos de generación de imágenes como [DALL **·** E 2](https://aituts.com/dalle-2/) y [Midjourney](https://aituts.com/midjourney/) de OpenAI , con una gran diferencia: fue lanzado en código abierto.

**Esto fue algo muy importante.**

A diferencia de estos otros modelos, que estaban estrechamente custodiados por las empresas que los fabricaban, cualquiera podía personalizar Stable Diffusion o construir sobre él.

En las breves semanas que siguieron al lanzamiento hubo una **explosión** de innovación en torno a Stable Diffusion.

La mejor parte es que puedes ejecutarlo en una computadora normal.

### ¿Es gratis?

Sí, Difusión estable es gratis.

Existen muchas herramientas y aplicaciones pagas que facilitan el uso de Stable Diffusion. Estos tienen sus propios pros y contras.

### ¿Es la herramienta de generación de imágenes más popular?

Stable Diffusion es la segunda herramienta de generación de imágenes más popular después de Midjourney.

Muchos predijeron que Midjourney superaría a Stable Diffusion como la herramienta de generación de imágenes de IA más popular a finales de 2022.

Esa predicción se ha hecho realidad: Midjourney ha superado a Stable Diffusion en varias métricas diferentes, incluido el volumen de búsqueda y la participación en las redes sociales.

Compare el crecimiento del subreddit Midjourney con el del subreddit Stable Diffusion:

![[Pasted image 20230924120844.png]]

Atribuimos esto a la difusión viral de Midjourney a través de las redes sociales, las imágenes de alta calidad de [Midjourney V4](https://aituts.com/midjourney-v4-prompts-to-try/) y [modelos posteriores](https://aituts.com/midjourney-versions/) , y su facilidad de uso. También se benefició de una mayor adopción de Discord.

**Esta no es una comparación de manzanas con manzanas.**

La mayoría de las herramientas de generación de imágenes, como [Leonardo AI,](https://leonardo.ai/) utilizan modelos de difusión estable bajo el capó para producir sus imágenes.

Se podría argumentar que Stable Diffusion tiene más **impacto** que Midjourney debido a la cantidad de nuevas herramientas y tecnologías que dependen de él.

## ¿Qué se puede hacer con  Stable Diffusion?

### Generar imágenes a partir de palabras.

Este es el uso más común de Difusión Estable. Se llama texto a imagen (txt2img) porque ingresas un texto y obtienes una imagen.

Hoy en día, puedes generar imágenes en una increíble cantidad de estilos.

#### Realista
![[Pasted image 20230924121053.png]]

#### Semi-realista
![[Pasted image 20230924121109.png]]

#### animado
Aprende a crear [imágenes de anime](https://aituts.com/novelai-anime-prompt-techniques/) .
![[Pasted image 20230924121130.png]]

#### Activos de juego
![[Pasted image 20230924121151.png]]
[Simcurious makes Age of Empires buildings](https://www.reddit.com/r/StableDiffusion/comments/13axnoa/trained_a_model_to_output_age_of_empires_style/)

#### Paisajes
![[Pasted image 20230924121208.png]]
by [SeaArt](https://www.reddit.com/r/StableDiffusion/comments/13pdbdy/medieval_landscapes/)


### Generar imágenes a partir de imágenes existentes

Puede utilizar imágenes existentes como inspiración estilística para crear nuevas imágenes o transformarlas de muchas maneras diferentes.
[Turn memes into real life](https://www.reddit.com/r/StableDiffusion/comments/10zn693/cant_believe_that_they_made_him_into_a_real_thing/), by XMBomb



![[Pasted image 20230924121349.png]]

Turning video game characters into Disney Princesses, by [Oatilis](https://www.reddit.com/user/Oatilis/)





### Corregir y editar imágenes

Puede pintar sobre imágenes y regenerar la parte pintada para que sea exactamente lo que desea.
This is called [inpainting](https://aituts.com/inpainting/).

![[Pasted image 20230924121449.png]]

![[Pasted image 20230924121459.png]]

### Pintar y generar al mismo tiempo.

Puedes llevar [el inpainting](https://aituts.com/inpainting/) al extremo:

https://aituts.com/wp-content/uploads/2023/07/m2-res_720p.mp4

### Ampliar imágenes

Incluso puedes generar fuera del marco para ampliar las imágenes. A esto se le llama pintar fuera.

### Crear animaciones

Existen varios métodos diferentes para crear animaciones con Stable Diffusion. El más popular es [Deforum](https://aituts.com/deforum/) , que crea estas animaciones muy alucinantes:

![](https://www.youtube.com/watch?v=CRY6C05QAPM)

## ¿La mejor manera de ejecutarlo?

Todo el mundo tiene diferentes aspiraciones y diferentes limitaciones técnicas, por lo que existen varias formas de ejecutar Stable Diffusion.

Hay varios sitios web en los que puede ejecutar Stable Diffusion, tanto gratuitos como de pago.

[Aquí hay una demostración gratuita](https://huggingface.co/spaces/stabilityai/stable-diffusion) que puede probar, realizada por StabilityAI (creadores de Stable Diffusion):

![[Pasted image 20230924121743.png]]

[ArtBot](https://tinybots.net/artbot/) es otro buen sitio web gratuito para probar. Funciona muy bien en dispositivos móviles y tiene una gran cantidad de modelos y funciones: img2img, inpainting y una galería pública.

![[Pasted image 20230924121809.png]]

### **Aplicaciones móviles**

Hasta ahora, la mejor aplicación móvil que hemos probado es [Draw Things de Liu Liu](https://apps.apple.com/us/app/draw-things-ai-generation/id6444050820) .

### Ejecutar en tu propia computadora

Si desea convertirse en un usuario intermedio, deberá ejecutar Stable Diffusion en su propia computadora. Esto le brindará la mayor cantidad de funciones y personalización.

Para hacer esto, necesitará descargar una interfaz de usuario.

Recomiendo [la WebUI de difusión estable de AUTOMATIC1111](https://github.com/AUTOMATIC1111/stable-diffusion-webui) . Es, con diferencia, la interfaz de usuario de Stable Diffusion más popular, con más de 60.000 me gusta en el repositorio de Github.

Aquí están las instrucciones de instalación:

- [GPU NVIDIA](https://aituts.com/stable-diffusion-on-windows-automatic1111/)
- [GPU AMD](https://aituts.com/stable-diffusion-amd/)
- [Apple Silicio (Mac M1/M2)](https://aituts.com/stable-diffusion-mac-m1/)

### Corriendo en la nube

Esto es un poco diferente de las versiones en línea mencionadas anteriormente. Está ejecutando la interfaz de usuario completa; sin embargo, está utilizando los servidores de Google para hacerlo.

Obtiene acceso a todas las funciones, pero no tiene que usar su propia computadora.

Google Colab es un servicio que permite ejecutar código Python, pero en los servidores de Google.

Puede parecer intimidante si nunca antes has codificado, pero en realidad es simplemente presionar una serie de botones de "ejecutar" para ejecutar diferentes secciones de código.

- **[Difusión estable rápida de TheLastBen](https://colab.research.google.com/github/TheLastBen/fast-stable-diffusion/blob/main/fast_stable_diffusion_AUTOMATIC1111.ipynb)** : Colab más popular para ejecutar difusión estable
- [**AnythingV3 Colab**](https://colab.research.google.com/github/Miraculix200/StableDiffusionUI_Colab/blob/main/StableDiffusionUI_Colab.ipynb#scrollTo=R-xAdMA5wxXd) : Colaboración de generación de anime

## Conceptos importantes

### Modelos de punto de control

StabilityAI y sus socios lanzaron los **modelos básicos de Stable Diffusion:** v1.4, v1.5, v2.0 y v2.1.

Stable Diffusion v1.5 es probablemente el modelo más importante que existe.

Esto no se debe a que genere buenas imágenes, sino a que se ha utilizado para entrenar muchos modelos personalizados.

Hoy en día, la mayoría de los modelos personalizados se crean sobre SD v1.5 o SD v2.1. Estos modelos personalizados son los que desea utilizar cuando intenta generar imágenes de alta calidad.

Los modelos de Checkpoint vienen en el formato de archivo antiguo `.ckpt` (punto de control) o el nuevo formato de archivo `.safetensors`.

**Consulte:** [Modelos de difusión estable más populares](https://aituts.com/models/)

![[Pasted image 20230924122114.png]]

La historia detrás de los modelos de anime es un poco diferente. La mayoría de los modelos de anime tienen su linaje en NAI Diffusion, creado por la empresa NovelAI (y ofrecido como servicio pago en su sitio web). Al igual que Stable Diffusion v1.5, ya nadie usa NAI Diffusion para generar imágenes, solo para entrenar nuevos LoRA (más sobre eso en un momento) y modelos.

**Echa un vistazo:** [Modelos de anime de difusión estable más populares](https://aituts.com/anime-models/)

![[Pasted image 20230924122205.png]]

### VAE 

Sin Vae tus imágenes se verán descoloridas. Vae son el entrenamiento de colores separados de un modelo de punto de control; la mayoría de los modelos tienen un vae recomendado, pero los vae son intercambiables, por lo que puedes usar tu favorito con una variedad de puntos de control diferentes.

### LoRA
Un LORA es un archivo de adaptación de rango bajo que agrega nuevos conceptos y términos a su IA que no estaban integrados originalmente. Aquí es donde realmente se puede ver la personalización de una persona. Los Lora se aplican en un porcentaje a su punto de control para agregar su entrenamiento individual al punto de control en uso.

## Mejorando tus resultados

### Prompting

Piense en los Prompting como si fuera el aprendizaje de un nuevo lenguaje que comunique de manera efectiva a la IA el resultado que desea.

Aquí hay un ejemplo de un mensaje (el mensaje negativo es lo que no **_desea_** ):

![[Pasted image 20230924122532.png]]

Este es un mensaje largo, pero también muy breve y simple:

![[Pasted image 20230924122615.png]]

A continuación se ofrecen algunos consejos generales sobre indicaciones:

- Utilice etiquetas de calidad como "masterpiece" y paréntesis para enfatizar sus etiquetas.
- Diferentes modelos responden de manera diferente a los estilos de estímulo. Elija algunos modelos que le gusten y quédese con ellos para conocer los entresijos de sus indicaciones, en lugar de sentir que tiene que descargar todos los modelos.
- Utilice nombres de artistas. Específicamente, utilice [nombres de artistas que estén bien representados en Stable Diffusion](https://rentry.org/artists_sd-v1-4) .
- ¿Los hacks más rápidos para mejorar tus generaciones? Utilice [LoRA](https://aituts.com/stable-diffusion-lora/) e [Embeddings](https://aituts.com/textual-inversion/).

Consulte la [guía de indicaciones de Difusión estable](https://aituts.com/stable-diffusion-prompts/) para obtener más información.


___
%%
Vínculos:
[[000-Menú Stable Diffusion XL 📃|Menú Stable diffusion XL]]

tags:
#pagstable_diffusion_xl #stable_diffusion_xl #stable_diffusion 
%%