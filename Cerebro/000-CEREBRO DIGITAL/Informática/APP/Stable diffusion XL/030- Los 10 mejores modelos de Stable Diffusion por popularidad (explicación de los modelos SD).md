---
ID: 30
-nombre: Los 10 mejores modelos de Stable Diffusion por popularidad (explicación de los modelos SD)
"-tags:":
---
___
# Los 10 mejores modelos de Stable Diffusion por popularidad (explicación de los modelos SD)
La calidad y el estilo de las imágenes que genera con Stable Diffusion dependen completamente del modelo que utilice.

StabilityAI lanzó el primer modelo público, **Stable Diffusion v1.4** , en agosto de 2022. En los próximos meses, lanzaron v1.5, v2.0 y v2.1.

Poco después del lanzamiento de estos modelos, los usuarios comenzaron a crear sus propios modelos personalizados sobre los modelos base.

Hoy en día, la mayoría de los modelos personalizados se crean sobre SD v1.5 o SD v2.1. Estos modelos personalizados suelen funcionar mejor que los modelos básicos.

"Modelo de difusión estable" se utiliza para referirse a los modelos base oficiales de StabilityAI, así como a todos estos modelos personalizados.

## ¿Dónde encontrar modelos de Difusión Estable?

Para mantenerse al día con los modelos más nuevos, visite [Civitai.com](https://civitai.com/) y [HuggingFace.co](https://huggingface.co/models?pipeline_tag=text-to-image&sort=downloads) .

Prefiero Civitai porque los usuarios comparten muchos ejemplos de imágenes, con indicaciones, para cada modelo.

El espacio de modelos se mueve muy rápido: no me sorprendería que hoy se creara un nuevo modelo y se convirtiera en el modelo más popular en un mes. Puede obtener información sobre los desarrollos de Stable Diffusion en nuestras [actualizaciones semanales](https://aituts.com/join) .

![[Pasted image 20230924154251.png]]

**Nota:** deberá tener una cuenta de Civitai para ver algunos de los modelos de este artículo, porque muchos tienen capacidades NSFW.

HuggingFace es mejor si tienes un modelo en mente y simplemente lo estás buscando. La mayoría de las veces no habrá ejemplos de imágenes:

![[Pasted image 20230924154330.png]]


Los modelos de punto de control de Difusión Estable se presentan en dos formatos diferentes: **`.ckpt`**y **`.safetensors`**. Los archivos `.safetensor` son preferibles a `.ckpt`archivos porque tienen mejores características de seguridad.

Ejecutará estos modelos localmente o en una computadora portátil Colab (ejecutándose en la nube en los servidores de Google)

Instrucciones de instalación para ejecutar localmente con AUTOMATIC1111:

- [Instalación de GPU NVIDIA](https://aituts.com/stable-diffusion-on-windows-automatic1111/)
- [Instalación de GPU AMD](https://aituts.com/stable-diffusion-amd/)
- [instalación mac](https://aituts.com/stable-diffusion-mac-m1/)

## Los mejores ## Checkpoint Models

### Dreamshaper
![[Pasted image 20230924154542.png]]

[Enlace de descarga](https://civitai.com/models/4384/dreamshaper)

**Ideal para:** arte fantástico, ilustración, semirealismo, personajes, entornos.

Dreamshaper es un gran modelo para empezar porque es muy versátil. No se necesitan muchas indicaciones para obtener buenos resultados, por lo que es ideal para principiantes.

Puedes crear una amplia variedad de temas: personajes, entornos y animales en estilos que van desde lo muy artístico hasta el semirrealismo.

### CyberRealistic

![[Pasted image 20230924154630.png]]

[Enlace de descarga](https://civitai.com/models/15003)

**Genial para:** fotorrealismo, gente real

CyberRealistic es extremadamente versátil en las personas que puede generar. Es muy sensible a los ajustes en las características físicas, la ropa y el entorno. Es bastante bueno con los personajes famosos.

Le recomendamos encarecidamente que utilice descriptores de iluminación, cámara y fotografía en sus indicaciones.

También te recomendamos usarlo con la inversión textual [CyberRealistic Negative](https://civitai.com/models/77976/cyberrealistic-negative) .

> Una de las fortalezas clave del modelo radica en su capacidad para procesar de manera efectiva inversiones textuales y LORA, proporcionando resultados precisos y detallados. Además, el modelo requiere indicaciones mínimas, lo que lo hace increíblemente fácil de usar y accesible.
> 
> Cyberdelia, creadora de modelos

### majicMIX realistic
![[Pasted image 20230924154746.png]]

[Enlace de descarga](https://civitai.com/models/43331/)

**Ideal para:** Fotorrealismo, Mujeres

majicMIX es un modelo de anime popular: esta es la variante realista de ese modelo.

La iluminación, la textura de la piel y los efectos de cámara fotorrealistas de este modelo son simplemente asombrosos.

La desventaja es que no es tan versátil como otros modelos realistas como CyberRealistic. Al igual que otros modelos de "mujeres hermosas", produce una cara muy similar.

### Realistic Vision
![[Pasted image 20230924154903.png]]

[Enlace de descarga](https://civitai.com/models/4201)

**Genial para:** fotorrealismo, gente real

Modelo de fotorrealismo utilizado tanto para celebridades como para personajes originales.

Bastante versátil en los tipos de personas que puedes conseguir.

### GhostMix

![[Pasted image 20230924154937.png]]

[Enlace de descarga](https://civitai.com/models/36520/)

**Ideal para:** anime, semirealismo

Un modelo de anime muy bonito que puede virar hacia el semirealismo.

### ReV Animated

![[Pasted image 20230924155017.png]]

[Enlace de descarga](https://civitai.com/models/7371)

**Ideal para:** 2.5D, Semirealismo, Ilustración

ReV Animated es un modelo muy versátil y con un gran estilo. Es una mezcla de realismo y anime, virando hacia el lado del realismo. Es otro modelo apto para principiantes que requiere un mínimo de indicaciones para obtener excelentes resultados.

### ChilloutMix

![[Pasted image 20230924155053.png]]

[Enlace de descarga](https://civitai.com/models/6424/chilloutmix)

**Ideal para:** Fotorrealismo, Mujeres

El modelo más popular de todos los tiempos en Civitai. Las imágenes son de alta calidad; Bueno para crear la apariencia de ídolo Kpop, pero no es un estilo muy versátil.

### NeverEnding Dream

![[Pasted image 20230924155128.png]]

[Enlace de descarga](https://civitai.com/models/10028)

**Ideal para:** arte fantástico, ilustración, semirealismo y anime.

NeverEnding Dream pretende ser un modelo complementario a DreamShaper, para cubrir todo aquello en lo que DreamShaper no es bueno.

Está diseñado para usarse con LoRA y también puede generar anime.

### Deliberate

![[Pasted image 20230924155207.png]]

[Enlace de descarga](https://civitai.com/models/4823/deliberate)

**Ideal para:** semirealismo, ilustración y arte fantástico.

Un modelo "experto en todos los oficios": puedes probar retratos, entornos, fantasía, etc. Uno de los modelos más populares de todos los tiempos, aunque un poco anticuado.

### Henmix_Real

![[Pasted image 20230924155240.png]]

[Enlace de descarga](https://civitai.com/models/20282)

**Genial para:** realismo

Buen modelo realista en todos los sentidos. La intención del creador era producir un modelo que fuera bueno en todas las carreras.

## Mejores modelos de anime

**Comparación completa: [los mejores modelos de difusión estable para anime](https://aituts.com/anime-models/)**

Los modelos de anime pueden rastrear sus orígenes en [NAI Diffusion](https://aituts.com/run-novelai-image-generator-locally/) . NAI es un modelo creado por la empresa NovelAI [modificando](https://blog.novelai.net/novelai-improvements-on-stable-diffusion-e10d38db82ac) la arquitectura y el método de entrenamiento de Difusión Estable.

En el momento del lanzamiento (octubre de 2022), supuso una gran mejora con respecto a otros modelos de anime. Mientras que el entonces popular Waifu Diffusion se entrenó en imágenes de anime SD + 300k, NAI se entrenó en millones.

Aquí hay una [guía rápida de NAI](https://aituts.com/novelai-anime-prompt-techniques/) que es ampliamente aplicable a la mayoría de los modelos de anime.

### Anything V5

![[Pasted image 20230924155418.png]]

[Enlace de descarga](https://civitai.com/api/download/models/30163) • [Información del modelo](https://civitai.com/models/9409/)

Anything V3 fue un ajuste muy popular de NAI Diffusion. V5 es la última versión.

### AbyssOrangeMix3 (AOM3)

![[Pasted image 20230924155449.png]]

[Enlace de descarga](https://huggingface.co/WarriorMama777/OrangeMixs/resolve/main/Models/AbyssOrangeMix3/AOM3_orangemixs.safetensors) • [Información del modelo](https://civitai.com/models/4468/)

Última versión de AbyssOrangeMix, una serie de mezclas que produce un estilo artístico de alta calidad.


### Counterfeit

![[Pasted image 20230924155514.png]]

[Enlace de descarga](https://civitai.com/api/download/models/57618) • [Información del modelo](https://civitai.com/models/4468)

Modelo anime de alta calidad y con un estilo muy artístico. Creado por gsdf, con DreamBooth + Fusionar pesos de bloque + Fusionar LoRA. **Altamente recomendado** .


### MeinaMix
![[Pasted image 20230924155553.png]]

[Enlace de descarga](https://civitai.com/api/download/models/57618) • [Información del modelo](https://civitai.com/models/4468)

Modelo anime de alta calidad y con un estilo muy artístico. Creado por gsdf, con DreamBooth + Fusionar pesos de bloque + Fusionar LoRA

## Base Models
Ya nadie utiliza los modelos base para la generación porque los ajustes finos producen resultados mucho mejores. Para qué sirven los modelos base: entrenar nuevos modelos, [entrenar LoRA](https://aituts.com/stable-diffusion-lora/) .

### Stable Diffusion v1.5

![[Pasted image 20230924155647.png]]

[Enlace de descarga](https://huggingface.co/runwayml/stable-diffusion-v1-5/resolve/main/v1-5-pruned-emaonly.ckpt)
Stable Diffusion v1.5 se lanzó en octubre de 2022.

Produce resultados ligeramente diferentes en comparación con la versión 1.4. El consenso general es que es ligeramente mejor, pero la diferencia es pequeña.

v1.4 y 1.5 son la base para la mayoría de los modelos que la gente ha creado. Tiene mucho más reconocimiento de celebridades y artistas que 2.0.

### Stable Diffusion v2.1

![[Pasted image 20230924155800.png]]

[Enlace de descarga](https://huggingface.co/stabilityai/stable-diffusion-2-1/tree/main) • [Instrucciones](https://aituts.com/install-stable-diffusion-v2-1/)

v2.0 se creó para resolver lo que los creadores vieron como un potencial de demandas mediante la implementación de un intérprete de avisos personalizado que es capaz de filtrar palabras que no quieren que usted use en los avisos, simplemente por razones de responsabilidad (pronunciación falsa profunda, etc.). ).

La versión 2.0 fue muy estricta en su filtrado y se volvió algo difícil crear buenos mensajes para ello.

v2.1 mejora las indicaciones y corrige mucho de lo que faltaba en 2.0 con respecto a las celebridades y artistas que faltan. También se mejoraron los filtros para no reaccionar exageradamente con falsos positivos.

Usaría 1,4 o 1,5 en lugar de 2,0 o 2,1 cualquier día de la semana.
## Extras: mejora tus resultados

### Usando LoRAs

Utilice LoRA **en combinación con los modelos de punto de control anteriores para agregar nuevos sujetos a su imagen** . Los LoRA se pueden entrenar en

Por ejemplo, podría utilizar un Studio Ghibli LoRA para hacer que sus resultados se parezcan más a la estética de Studio Ghibli.

**Guía completa: [Guía completa de LoRA de difusión estable](https://aituts.com/stable-diffusion-lora/)**

### Usando Textual Inversion / Embeddings
Los Embeddings (también conocidas como inversión textual) son pequeños archivos que contienen conceptos adicionales. Los usas descargándolos y colocándolos en la carpeta `stable-diffusion-webui/embeddings`. Los activa escribiendo una palabra clave especial en el mensaje.

_Los Embeddings negativos_ son archivos entrenados con imágenes de mala calidad. Al colocar la palabra clave de activación para estos en su **mensaje negativo** , obtendrá imágenes de mejor calidad.

Algunas incrustaciones negativas populares son [EasyNegative](https://civitai.com/models/7808/easynegative) y [negativo_hand](https://civitai.com/models/56519/negativehand-negative-embedding) .

## Preguntas más frecuentes

**¿Cuál es la diferencia entre fp16 y fp32?**

**fp16** (punto flotante 16) y **fp32** (punto flotante 32) se refieren al formato mediante el cual se almacenan los datos, que puede ser de 16 bits (2 bytes) o 32 bits (4 bytes).  
A menos que quieras entrenar o mezclar tu propio modelo personalizado, todo lo que necesitas es la versión más pequeña del fp16. Para usuarios ocasionales, la diferencia entre la calidad de imagen producida por fp16 y fp32 es insignificante.

**¿Cuál es la principal diferencia entre Stable Diffusion v1.5 y v2.1?**

v1.5: compatibilidad con NSFW, más modelos personalizados, mejor compatibilidad con ControlNet, más LoRA, TI, más artistas y celebridades en el conjunto de imágenes de datos de entrenamiento. El conjunto de entrenamiento es de 512x512, por lo que el tamaño óptimo para una exploración rápida es 512x512, lo cual es algo limitado.  
  
v2.1: Mejor soporte para fotografías y paisajes. El conjunto de entrenamiento es de 768x768, por lo que se obtiene una composición y detalles más interesantes, más fácil de explorar y experimentar a partir de 768x768.



___
%%
Vínculos:
[[000-Menú Stable Diffusion XL 📃|Menú Stable diffusion XL]]

tags:
#pagstable_diffusion_xl #stable_diffusion_xl #stable_diffusion 
%%