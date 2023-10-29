---
ID: 70
-nombre: Promp guide
"-tags:":
---
___
# Promp guide
## Indicaciones: cómo empezar
Los prompts son las palabras que le das a la IA para decirle qué generar.

Aquí hay una plantilla de prompts muy simple para comenzar. Todo comienza preguntando: ¿Qué quieres ver?

1. ¿Cuál es el tema? p.ej. → `girl`
2. ¿Cuáles son los atributos del sujeto? → `looking to side, jeweled crown`
3. ¿Cuáles son las características visuales de la imagen?
    - Ángulos de cámara / Tipo de toma de cámara → `close-up`
    - Iluminación → `cinematic lighting, ethereal glow`
    - Estilos de arte / Estilo del artista / Estética → `digital painting`
    - Esquema de colores → `vibrant colors`
    - Entorno circundante → `in a forest`
4. 1. Descriptores de calidad (explicados a continuación) → `best quality, masterpiece`

Ponlos todos juntos:

```
girl, looking to side, jeweled crown, close-up, cinematic lighting, fantasy art, digital painting, ethereal glow, vibrant colors, forest, best quality, masterpiece
```

Querrás probar [diferentes modelos](https://aituts.com/models/) para ver cuál te gusta más. Aquí está el mensaje anterior que se utiliza con mis modelos favoritos:

![[Pasted image 20230924185128.png]]


### Quality Tags
Mucha gente utiliza "etiquetas de calidad" en sus mensajes, que son palabras y frases como:

- masterpiece
- best quality
- intricate details

Estas palabras tendrán un impacto positivo en la mayoría de las indicaciones. La magnitud del impacto depende del modelo que esté utilizando.

![[Pasted image 20230924185243.png]]

```
girl looking to side, jeweled crown, close-up, cinematic lighting, vibrant colors,  fantasy art, disney pixar style, ethereal glow, forest
```

![[Pasted image 20230924185302.png]]

```
((masterpiece)), (top quality), (best quality), girl looking to side, jeweled crown, close-up, cinematic lighting, vibrant colors,  fantasy art, disney pixar style, ethereal glow, forest
```

Una regla general: cuanto más "orientado al anime" sea un modelo, mejor funcionarán estas etiquetas.

## Negative Prompts
Hay mucha confusión detrás de las indicaciones negativas, porque hay muchas maneras diferentes en que la gente piensa acerca de cómo usarlas. Aquí están 2 de los más comunes:

- **Contenido no deseado** : el mensaje negativo debe ser _lo que no desea_ en la imagen, por ejemplo: "bad hands" "mutated"

**Opuesto conceptual** : las indicaciones negativas deben ser el _opuesto conceptual_ de sus indicaciones, por ejemplo."noodles" si intentas generar "rocks" , "anime" si intentas genera "photorealism"

Aunque esta última es la forma "correcta" de pensar sobre las indicaciones negativas, la primera puede resultar práctica.

Las indicaciones negativas no funcionan en el sentido de que le estás diciendo a la IA que arregle tus manos deformes. Más bien, proporcionan una dirección (vector) que aleja a la generación de la parte del [espacio latente](https://towardsdatascience.com/understanding-latent-space-in-machine-learning-de5a7c687d8d) que tiene probabilidades de contener esas cosas. Piense en las indicaciones y las indicaciones negativas como si estuvieran encerradas en un juego de tira y afloja.

### Undesirable Content Negative Prompts
Aquí hay una imagen que salió bien y que utiliza un mensaje negativo simple usando el modelo animado de ReV:

```
(1girl) looking at camera, braids, smiling, dress, rural envionment, lens flare, beautiful day (fabric with intricate pattern:1.2), (insanely detailed:1.2), ((masterpiece)), (painting:1.1), (digital painting:1.1)
Negative prompt: cartoon, 3d, ((disfigured)), ((bad art)), ((deformed)), ((poorly drawn)), ((extra limbs)), ((close up)), ((b&w)), weird colors, blurry
Steps: 35, Sampler: DPM++ 2M Karras, CFG scale: 7, Seed: 561242768, Size: 768x512, Model hash: 4199bcdd14, Model: revAnimated_v122, Denoising strength: 0.7, Hires upscale: 2, Hires steps: 15, Hires upscaler: 4x-UltraSharp, Version: v1.4.1
```

![[Pasted image 20230924185631.png]]

**Negative prompt:** 
```
cartoon, 3d, ((disfigured)), ((bad art)), ((deformed)), ((poorly drawn)), ((extra limbs)), ((close up)), ((b&w)), weird colors, blurry
```

Eche un vistazo a lo que sucede si aumento la duración del mensaje negativo y agrego mucho "contenido indeseable".

![[Pasted image 20230924185726.png]]

**Negative prompt:**
```
(worst quality:2), (low quality:2), (normal quality:2), (b&w:1.2), (black and white:1.2), (blurry:1.2), (out of frame:1.2), (ugly:1.2), (cross-eyed:1.2), (disfigured:1.2),(deformed:1.2), (extra limbs:1.2), (b&w:1.2), (blurry:1.2), (duplicate:1.2), (morbid:1.2), (mutilated:1.2), (poorly drawn hands:1.2), (poorly drawn face:1.2), (mutation:1.2), (deformed:1.2), (bad anatomy:1.2), (bad proportions:1.2), (watermark:1.5), (text:1.5), (logo:1.5)
```

La imagen es más nítida, las sombras son más profundas y el personaje está más animado y menos rígido.

### Conceptual Opposite Negative Prompts
Algunos ejemplos negativos publicados por StabilityAI parecen [completamente desquiciados](https://www.reddit.com/r/StableDiffusion/comments/zq2zoe/the_negative_prompt_examples_in_the_official/) .

Un "opuesto" puede no tener mucho sentido para nosotros, pero sí lo tiene en el contexto del espacio latente. Mira [este experimento](https://www.reddit.com/r/StableDiffusion/comments/y0t4pd/a_bizarre_experiment_with_negative_prompts/) .

Una forma de descubrir lo contrario de tu imagen: utiliza una escala CFG negativa.

AUTOMATIC1111 no permite una escala CFG negativa. Sin embargo, podemos solucionar esto usando la función de gráfico X/Y (una característica muy útil en otras situaciones que permite crear gráficos de comparación con diferentes configuraciones).

Ve a la parte inferior de la pantalla. Debajo del campo Semilla verás el menú desplegable Script. Seleccionar `X/Y/Z plot`, luego seleccione `CFG Scale`en el `X type`campo. Escribir `-7`en el `X values`campo.

![[Pasted image 20230924190121.png]]


Ahora, cuando genere, obtendrá lo **contrario de su mensaje, según Stable Diffusion** . Esto es lo que obtuve:

![[Pasted image 20230924190133.png]]

¡Además de ser extremadamente inquietantes, estas imágenes tienen mucho en común!

Identifico los puntos en común y los uso en un nuevo mensaje negativo. Si le resulta difícil describir imágenes, intente usar [CLIP Interrogator](https://huggingface.co/spaces/fffiloni/CLIP-Interrogator-2) , que las etiquetará por usted.

Aquí está el resultado final:

![[Pasted image 20230924190604.png]]

```
a black and white photo of a cartoon character, greyscale, zbrush, (ambient occlusion render), b&w, (photo of a man's torso), polycount, sculpture, (ugly:1.2),(bad quality:1.2)
```

**Conclusiones** :

- Las indicaciones muy largas sobre "contenido indeseable" son en su mayoría placebo. Vea [esta publicación de Reddit](https://www.reddit.com/r/StableDiffusion/comments/z4s8bz/clip_is_not_skynet_a_primer_on_why_your_negative/) .
- Los "contenidos indeseables" incitan al trabajo porque todavía alejan a la generación de conceptos en el espacio latente
- Las indicaciones opuestas pueden producir resultados muy interesantes.

### Cambiar el estilo con indicaciones negativas.
Aquí hay un uso subestimado de indicaciones negativas. Describe estilos que sean opuestos al estilo que deseas.

![[Pasted image 20230924190855.png]]


## Pesos con paréntesis

### Paréntesis
En Stable Diffusion, los paréntesis se utilizan para aumentar el peso de los tokens (enfatizar), como por ejemplo: `(((red hair)))`.

El peso predeterminado de un token es 1.

El peso de todo lo que esté entre paréntesis se _multiplicará_ por 1,05.

Este multiplicador se acumula sobre sí mismo dependiendo de cuántos paréntesis utilice:

![[Pasted image 20230924191027.png]]


Sin embargo, no agregues demasiados paréntesis, ya que llegarás a un punto en el que la palabra resaltada dominará por completo la imagen.

También puedes ser específico y escribir el peso exacto que deseas usando el formato `(KEYWORD:WEIGHT)`.

Entonces podrías escribir `(jeweled crown:1.477)`, y esto sería lo mismo que `((((((((jeweled crown))))))))`.

### Corchetes
En Stable Diffusion, los corchetes se utilizan para disminuir el peso de (quitar énfasis) a las palabras, como por ejemplo: `[[hat]]`.

El peso de cualquier cosa dentro de los corchetes se dividirá _por_ 1,05.

Lo usas cuando todavía quieres el concepto entre paréntesis, solo quieres disminuirlo en relación con los otros conceptos.

Esto **no** es lo mismo que una indicación negativa.

![[Pasted image 20230924191210.png]]

Observe cómo la corona se hace cada vez más pequeña, hasta desaparecer en los 6 corchetes.

## Posición de la palabra
Es posible que tenga la sensación de que los tokens colocados anteriormente en el mensaje son más importantes que los tokens que aparecen más adelante en el mensaje.

Esa es sólo la mitad de la historia.

Cuando Stable Diffusion analiza su prompt, lo hace en partes. Los fragmentos se procesan en orden.

Aquí hay un problema común con Stable Diffusion: cuando especificas colores, estos sangran con el tiempo otros elementos. En este especifiqué **5 colores diferentes** y _casi_ acerté, con la excepción de la corbata roja:

![[Pasted image 20230924191330.png]]

```
1girl, close-up, green eyes, long black hair, white dress shirt, gold earrings,  red tie
```

Para resolver esto, movería la "corbata roja" a otro lugar del mensaje, donde se analizará en un fragmento diferente al de los "pendientes de oro":

![[Pasted image 20230924191406.png]]

```
1girl, close-up, red tie, green eyes, long black hair, white dress shirt, gold earrings
```

## Cámara, iluminación y fotografía , Palabras clave
Aprender algunos términos básicos de fotografía te dará una gran ventaja. Estos términos se utilizan ampliamente para etiquetar las imágenes y entrenar los modelos.

### Tipos de tomas de cámara
#### Primer plano / Retrato

Pruebe las palabras clave [ close-up], [ portrait], [ face].

![[Pasted image 20230924191544.png]]
**MODEL:**
[ReV Animated](https://aituts.com/models#rev-animated)
**Prompt:**
```
close-up, (masterpiece, top quality, best quality, official art, beautiful and aesthetic:1.2), (1girl), (fractal art:1.2),absurdres, highres, ultra detailed, Ultra-precise depiction, Ultra-detailed depiction, solo, ( halo armor:1.2), dynamic pose, floating hair, (thin: 1.2),  (abstract:1.2), 
```
**Negative Prompt:**
 ```
 easynegative badhandv4
```
**SAMPLER:**
DPM+++ SDE Karras

#### Medium Range
Pruebe las palabras clave [ medium shot], [ medium cowboy shot].

![[Pasted image 20230924191715.png]]

**MODEL:**
[ReV Animated](https://aituts.com/models#rev-animated)
**Prompt:**
```
medium cowboy shot, (masterpiece, top quality, best quality, official art, beautiful and aesthetic:1.2), (1girl), (fractal art:1.2),absurdres, highres, ultra detailed, Ultra-precise depiction, Ultra-detailed depiction, solo, ( halo armor:1.2), dynamic pose, floating hair, (thin: 1.2),  (abstract:1.2), 
```
**Negative Prompt:**
 ```
 easynegative badhandv4
```
**SAMPLER:**
DPM+++ SDE Karras

#### Full Body
Prueba las palabras clave `[full body]`.

![[Pasted image 20230924191825.png]]

**MODEL:**
[ReV Animated](https://aituts.com/models#rev-animated)
**Prompt:**
```
full body, (masterpiece, top quality, best quality, official art, beautiful and aesthetic:1.2), (1girl), (fractal art:1.2),absurdres, highres, ultra detailed, Ultra-precise depiction, Ultra-detailed depiction, solo, ( halo armor:1.2), dynamic pose, floating hair, (thin: 1.2),  (abstract:1.2), 
``` 
**Negative Prompt:**
 ```
 easynegative badhandv4
```
**SAMPLER:**
DPM+++ SDE Karras


### Depth of field (Profundidad de campo)
La profundidad de campo es el área de nitidez aceptable delante y detrás del sujeto. En pocas palabras, se refiere a qué tan borrosa o nítida es la imagen alrededor del sujeto.

Se utiliza una gran profundidad de campo para crear intimidad con los sujetos.

## Style Keywords(Palabras clave de estilo)
A continuación se muestran algunas palabras clave interesantes para modificar el estilo y sus efectos.

Todas estas imágenes usan el mismo mensaje, con una frase agregada para modificar el estilo:

**Prompt:**
```
((best quality)), ((masterpiece)), (detailed), woman sitting at table, <STYLEMODIFIER>
```
**Negative Prompt:**
 ```
 worst quality badhandv4 easynegative
```

![[Pasted image 20230924192020.png]]
![[Pasted image 20230924192035.png]]

### Artist names

![[Pasted image 20230924192059.png]]
![[Pasted image 20230924192113.png]]

### ¿Existe una forma "correcta" de hacer prompts?

Algunas personas incitarán con oraciones gramaticalmente correctas como [ a photograph of a girl wearing a parka in a city] y otros escribirán fragmentos como [ photograph, 1girl, parka, city]. Entonces, ¿Cuál es la forma correcta?

Lamentablemente la respuesta es: depende.

A veces depende del modelo que estés usando.

El modelo base 1.5 de RunwayML y los modelos 2.x de Stability AI son capaces de procesar comandos en lenguaje natural como el primero.

El modelo Novel AI (filtrado, pero incorporado en muchos de los modelos de anime que existen) usa etiquetas delineadas por comas como la segunda, basada en el concepto de etiquetado Danbooru.

Cuando los modelos se combinan con ambos elementos, puedes usar ambos. Y probablemente obtendrá resultados equivalentes siempre que SD pueda seleccionar las palabras clave allí.

## Buscando inspiración

Los mejores lugares para encontrar indicaciones en este momento:

- [civitai.com](https://civitai.com) presenta indicaciones e imágenes enviadas por los usuarios para cada modelo
- [mage.space](https://www.mage.space/explore) te permite explorar indicaciones por género
- [tensor.art](https://tensor.art/posts) te permite explorar indicaciones por tema
- [majinai.art](https://majinai.art/) está actualizado sobre modelos de anime y es un buen lugar para encontrar indicaciones de anime.


___
%%
Vínculos:
[[000-Menú Stable Diffusion XL 📃|Menú Stable diffusion XL]]

tags:
#pagstable_diffusion_xl #stable_diffusion_xl #stable_diffusion 
%%