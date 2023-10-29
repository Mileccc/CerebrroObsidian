---
ID: 40
-nombre: La guía definitiva de LoRA de Stable Diffusion (descarga, uso, capacitación)
"-tags:":
---
___
# La guía definitiva de LoRA de Stable Diffusion (descarga, uso, capacitación)
Los LoRA (adaptaciones de bajo rango) son archivos más pequeños (entre 1 MB y 200 MB) que se combinan con modelos de [Stable Diffusion checkpoint models](https://aituts.com/models/) existentes para **introducir nuevos conceptos** **en sus modelos** , de modo que su modelo pueda generar estos conceptos.

Estos nuevos conceptos se dividen en 2 categorías: **temas(subject)** y **estilos(styles)** .

Los temas pueden ser cualquier cosa, desde personajes ficticios hasta personas de la vida real, expresiones faciales, poses, accesorios, objetos y entornos.

Los estilos incluyen [visual aesthetics](https://aesthetics.fandom.com/wiki/List_of_Aesthetics) , estilos de arte  y estilos artísticos.

LoRA fue desarrollado por Microsoft Research en 2021 [ [Papel](https://arxiv.org/pdf/2106.09685.pdf) ][ [Github](https://github.com/microsoft/LoRA) ].

**Datos breves** :

- Ajustar los modelos de IA para realizar tareas específicas puede resultar lento y difícil. LoRA se creó como una forma más rápida y eficiente de ajustar modelos de lenguaje grandes y luego se adaptó a modelos de difusión para la generación de imágenes.
- Los LoRA han ganado popularidad porque tienen menores requisitos de hardware para la capacitación y su pequeño tamaño los hace fáciles de compartir y descargar.
- Puedes [entrenar tu propio LoRA](https://aituts.com/wp-admin/post.php?post=5309&action=edit#training) con tan solo 10 imágenes de entrenamiento
- Debes entrenar tu LoRA sobre un [modelo básico/fundamental](https://www.adalovelaceinstitute.org/resource/foundation-models-explainer/#:~:text=Foundation%20models%20are%20AI%20models,base'%20for%20many%20other%20applications.) :
    - Los LoRA más realistas de la actualidad están entrenados en Stable Diffusion v1.5 (o modelos basados ​​en él)
    - La mayoría de los LoRA de anime/dibujos animados/estilizados de hoy en día están entrenados en NAI Diffusion (o modelos basados ​​en él)
    - La próxima generación de LoRA se entrenará en [SDXL](https://aituts.com/sdxl/)

**Uso rápido:**

- [Los usuarios de AUTOMATIC1111](https://aituts.com/stable-diffusion-on-windows-automatic1111/) pueden usar LoRA descargándolos y colocándolos en la carpeta `stable-diffusion-webui/models/Lora`y luego agregando la frase `<lora:LORA-FILENAME:WEIGHT>` a su mensaje, donde ``LORA-FILENAME`` es el nombre de archivo del LoRA sin la extensión de archivo, y ``WEIGHT``(que toma un valor de 0-1) es la fuerza de la LoRA
- A veces, los LoRA tienen palabras desencadenantes que debes usar en el mensaje además de la frase clave anterior.
- Puede utilizar tantos LoRA en el mismo mensaje como desee

En esta guía, cubriremos brevemente qué es un LoRA, cómo se compara con otras técnicas de ajuste, mostraremos algunos LoRA populares, le mostraremos cómo ejecutarlos y, finalmente, le mostraremos cómo entrenar uno.

Esta es la parte 4 de la serie Difusión estable para principiantes:

## ¿Qué son las LoRA?

Un LoRA es un tipo de método de entrenamiento para **ajustar** modelos de Stable Diffusion.

¿Qué es el fine-tuning?

Digamos que queremos entrenar un modelo de imagen para generar imágenes a nuestra semejanza.

Entrenar un modelo desde cero será extremadamente costoso y prohibitivo para la mayoría de las personas.

En lugar de entrenar un nuevo modelo desde cero **,** podemos **reutilizar uno existente como punto de partida** . Podemos tomar un modelo como Stable Diffusion v1.5 y entrenarlo en un conjunto de datos mucho más pequeño (las imágenes de nosotros), creando un modelo que sea simultáneamente bueno en la tarea amplia de generar imágenes realistas y en la tarea limitada de generar imágenes de nuestro semejanza.

### LoRA y Dreambooth

Dreambooth es otra técnica de ajuste que te permite entrenar a tu modelo en un concepto como un personaje o estilo. En la práctica, Dreambooth y LoRA están destinados a lograr lo mismo.

La diferencia es que Dreambooth _actualiza_ todo el modelo, pero LoRA genera un pequeño archivo _externo_ al modelo.

Esto significa que el entrenamiento de Dreambooth producirá un modelo de punto de control completo (esta es una de las principales formas en que las personas crean [modelos personalizados](https://aituts.com/models/) ), pero los archivos LoRA deben usarse _en combinación_ con un modelo de punto de control existente.

En términos de calidad, un LoRA bien entrenado es comparable a un modelo Dreambooth. LoRA tiene la ventaja de un _proceso de entrenamiento mucho_ más rápido, menores requisitos de GPU y resultados más pequeños.

### LoRA vs Hypernetwork
[Las hiperredes](https://aituts.com/hypernetworks/) funcionan casi exactamente igual que LoRA. También son archivos más pequeños que se utilizan con modelos de puntos de control para presentar nuevos conceptos a sus generaciones.

La diferencia es técnica: tanto las hiperredes como las LoRA cambian de valores a medida que pasan por las [capas de atención](https://jalammar.github.io/illustrated-stable-diffusion/) del modelo, sin embargo, lo hacen de manera diferente.

Puede considerarlos como "LoRA heredados" porque en gran medida se han vuelto obsoletos.

Sin embargo, si tienes una hiperred que usas y disfrutas, no hay razón para dejar de usarla.

### LoRA vs Textual Inversion
LoRA y Dreambooth están destinados a enseñarle a un modelo un _nuevo_ concepto.

**[Textual Inversion/Embeddings](https://aituts.com/textual-inversion/)** Por otro lado, utiliza elementos que el modelo ya conoce para crear el resultado deseado. Son más bien ayudantes rápidos que cualquier otra cosa.

Usemos caras como ejemplo. Cuando usamos una inversión textual para generar una cara, el modelo no genera una cara "nueva".

En cambio, nuestra inversión textual es solo un _atajo_ para la combinación específica de nariz/mentón/boca/ojos que ya está en el modelo y que se parece a lo que queremos.

Puedes ver la limitación: si aún no está en el modelo, no se puede producir mediante una inversión textual.

Las inversiones textuales siguen siendo muy populares porque se utilizan en indicaciones negativas (un uso comúnmente denominado "incrustación negativa"). La gente entrena inversiones textuales sobre cosas indeseables como malas manos y mutaciones. Cuando los colocamos en nuestras indicaciones negativas, podemos mejorar casi todas las indicaciones.

## ¿Qué pueden hacer los LoRA?

Los LoRA son extremadamente versátiles. A continuación se muestran algunos conceptos en los que la comunidad de Stable Diffusion ha capacitado a los LoRA:

- Mejoras de calidad (por ejemplo, [Detail Tweaker](https://civitai.com/models/58390/detail-tweaker-lora-lora) )
- Estilos/estética (p. ej., [estilo Arcano](https://civitai.com/models/7094/arcane-style-lora) , [estilo Studio Ghibli](https://civitai.com/models/6526/studio-ghibli-style-lora) , [Anime Lineart](https://civitai.com/models/16014/anime-lineart-manga-like-style) )
- Personajes o personas (por ejemplo, [Makima](https://civitai.com/models/5373/makima-chainsaw-man-lora) , [Cute_girl_mix](https://civitai.com/models/14171/cutegirlmix4) )
- Ropa u objetos (por ejemplo, [Hanfu](https://civitai.com/models/15365/hanfu) , [Foo taiwanés](https://civitai.com/models/21079/common-taiwanese-food-or) )
- Entornos (por ejemplo, [edificio escolar](https://civitai.com/models/20289/school-building-scenery-lora) )

Las generaciones siguientes utilizan el mismo modelo, el mismo mensaje y la misma semilla. La única diferencia es la presencia de LoRA:

![[Pasted image 20230924161811.png]]
[Colorwater](https://civitai.com/models/16055/colorwater) 

![[Pasted image 20230924161832.png]]
[Hanfu](https://civitai.com/models/15365/hanfu)

![[Pasted image 20230924161848.png]]
[Anime Lineart](https://civitai.com/models/16014/anime-lineart-manga-like-style)

**Puede utilizar LoRA con cualquier modelo de Stable Diffusion** , siempre que el modelo y LoRA formen parte de la misma serie:

- Los LoRA entrenados desde SD v1.x solo funcionarán con modelos entrenados desde SD v1.x
- Los LoRA entrenados desde SD v2.x solo funcionarán con modelos entrenados desde SD v2.x
- Los LoRA entrenados desde SDXL solo funcionarán con modelos entrenados desde SDXL

Generalmente, los LoRA realistas funcionan mejor con modelos realistas y los LoRA de anime funcionan mejor con modelos de anime. Sin embargo, esta distinción no es tan clara, ya que los modelos más populares hoy en día son **fusiones** de modelos realistas y anime/estilizados.

A veces, los creadores suelen tener notas sobre los modelos recomendados en sus descripciones de LoRA.

## ¿Dónde descargas los LoRA?
Hay 2 lugares para encontrar LoRA:

- [**Civitai.com**](https://civitai.com/tag/lora) : Más popular y recomendado
- [**HuggingFace.co**](https://huggingface.co/lora-library) : Menos popular. El problema es que HuggingFace coloca a los LoRA en la misma categoría que los modelos de punto de control, por lo que no hay una manera fácil de encontrarlos.

No entraré en detalles sobre NSFW LoRA, pero hay _muchos_ en Civitai, solo tienes que crear una cuenta para verlos.

## LoRA populares

### LoRA de propósito general

Los LoRA se pueden utilizar para mejorar la calidad de la imagen o producir variaciones interesantes de una imagen.

- [epinoiseoffset](https://civitai.com/models/13941/epinoiseoffset) : aumenta el contraste para obtener imágenes de mejor calidad. **Recomendado 🔥**
- [Detail Tweaker](https://civitai.com/models/58390/detail-tweaker-lora-lora) : aumenta o disminuye el nivel de detalle. **Recomendado 🔥**
- [CharTurnerBeta](https://civitai.com/models/7252/charturnerbeta-lora-experimental) : crea cambios de personajes para el diseño de personajes

![[Pasted image 20230924162100.png]]

[Detail Tweaker LoRA](https://civitai.com/models/58390/detail-tweaker-lora-lora) with [Counterfeit model](https://aituts.com/anime-models#counterfeit)

### LoRA de estilo/estética

Producir una determinada estética o estilo artístico.

- [Colorwater](https://civitai.com/models/16055) - estilo acuarela
- [Anime lineart](https://civitai.com/models/16014/anime-lineart-manga-like-style) - estilo lineart / libro de colores
- [Anime tarot card art style](https://civitai.com/models/11177/anime-tarot-card-art-style-lora) : estilo de ilustración de cartas de tarot intrincado
- [Blindbox](https://civitai.com/models/25995/blindbox) - estilo chibi 3D
- [Anime Magazine Cover](https://civitai.com/models/18438/anime-magazine-cover) - estilo de portada de revista

![[Pasted image 20230924162205.png]]

### LoRA de personaje/persona

Crea un personaje ficticio o una persona de la vida real.

- [Yae Miko](https://civitai.com/models/8484/yae-miko-or-realistic-genshin-lora) - Genshin Impact
- [Makima](https://civitai.com/models/5373/makima-chainsaw-man-lora) - Chainsaw Man
- [Jinx](https://civitai.com/models/11457/jinx-league-of-legends) - League of Legends

![[Pasted image 20230924162338.png]]

### Costume LoRAs

- [【Costume】Straitjacket](https://civitai.com/models/10640/costumestraitjacket) - agrega camisa de fuerza a los personajes
- [Oversized Sweater/hoodie](https://civitai.com/models/52885/oversized-sweaterhoodie)
- [Urban Samurai](https://civitai.com/models/23337/urban-samurai-or-v014-or-clothing-lora) - ropa tecnológica y katanas

## Cómo utilizar LoRA

### Con AUTOMATIC1111

**Requisito previo:** Tiene un AUTOMATIC1111 funcional y actualizado. Aquí hay instrucciones específicas de la plataforma:

- [Instrucciones de la GPU NVIDIA](https://aituts.com/stable-diffusion-on-windows-automatic1111/)
- [Instrucciones de la GPU AMD](https://aituts.com/stable-diffusion-amd/)
- [instrucciones para Mac](https://aituts.com/stable-diffusion-mac-m1/)

También debe tener un modelo de punto de control descargado y colocado en la carpeta `stable-diffusion-webui/models/Stable-diffusion`. Usaré [Anything V3](https://civitai.com/models/66) en este ejemplo.

1. Descargue el archivo LoRA ( `.pt`o `.safetensor`) y colóquelo en la carpeta `stable-diffusion-webui/models/Lora`. Como ejemplo, usaré [Detail Tweaker](https://civitai.com/models/58390/detail-tweaker-lora-lora) , pero puedes usar cualquier LoRA que quieras.
2. Inicie su WebUI (haga clic `webui-user.bat`).
3. Bajo la `Generate`botón, haga clic en el `Show Extra Networks`icono. Es un pequeño icono rosa:

![[Pasted image 20230924162537.png]]

Haga clic en la pestaña LoRA. Mostrará todos los LoRA en la carpeta. `stable-diffusion-webui/models/Lora`(si no ves nada, haz clic en el icono gris `Refresh` botón).

Haga clic en el LoRA que desee y la frase clave de LoRA se agregará a su mensaje. Puede utilizar tantos LoRA en el mismo mensaje como desee.

![[Pasted image 20230924162609.png]]


También puedes escribir la frase clave LoRA manualmente. Sigue el formato:  
`<lora:LORA-FILENAME:WEIGHT>`

==`LORA-FILENAME`== es el nombre de archivo del modelo LoRA, sin la extensión de archivo (por ejemplo, no `.safetensor`).

`WEIGHT`es qué tan fuerte quieres que sea LoRA. El rango es 0-1; 0 es lo mismo que desactivar el LoRA, 1 es la fuerza máxima. Con muchos LoRA, un peso de `1`puede ser abrumador hasta el punto de crear malos resultados, así que experimente con valores más bajos como `0.5`a `0.8`.

(Detail Tweaker es un poco especial. Va en 2 direcciones y acepta cualquier valor entre -1 y 1. -1 eliminará detalles y 1 agregará detalles).

**Palabras desencadenantes:** a veces, los LoRA tendrán palabras desencadenantes. Son palabras que activan el concepto.

(Nuestro ejemplo Detail Tweaker no tiene palabras desencadenantes. Por otro lado, con un LoRA como **Anime Lineart** , querrás incluir " **lineart** " en tu mensaje. El creador generalmente te dirá estas palabras desencadenantes, si las hay, en la descripción de LoRA.)

#### Ejemplo

**Escribe el mensaje:**

```
(extremely detailed CG unity 8k wallpaper),(masterpiece), (best quality), (ultra-detailed), (best illustration),(best shadow),(an extremely delicate and beautiful), dynamic angle, floating, finely detail,Depth of field,1girl,solo,girl with beautiful detailed despair face and long fluttering hair and beautiful detailed eyes,((blood)) <lora:add_detail:1>
```

**Y el mensaje negativo:**

```
mutated hands and fingers:1.5,lowres, bad anatomy, bad hands, fused fingers,text error, liquid digit,missing fingers, extra digits,malformed feet, fewer digits, cropped,fused feet,worst quality, low quality, standard quality, jpeg artifacts , signature, watermark, username, blurry,bad mouth,cracked mouth
```

**Establecer la semilla: `3944989649`**

Y luego haga clic `Generate`. Esto es lo que obtengo.

![[Pasted image 20230924162939.png]]

Asegúrese de que sus configuraciones sean todas iguales si está intentando seguirlas. estoy usando el `Euler a` dechado, `20` pasos de muestreo y `7` Escala CFG.

¿Cómo puedes saber qué está haciendo realmente LoRA?

Cambiar `<lora:add_detail:1>`a `<lora:add_detail:0>`(desactivando el LoRA por completo), y luego regenerar.

Entonces cambia esta frase a `<lora:add_detail:-1>`y regenerar (recuerde que la dirección negativa _elimina_ detalles).

Entonces podemos comparar las generaciones:

![[Pasted image 20230924163209.png]]

Agregar detalles aumenta los detalles, la iluminación y las texturas. Por otro lado, eliminar detalles crea una ilustración de estilo plano que resulta atractiva a su manera.

## Entrenamiento de LoRA

Se ha **comparado el entrenamiento de LoRA con hornear un pastel** , y esa es la mejor analogía que he visto hasta ahora.

Intentas conseguir los mejores ingredientes (imágenes de entrenamiento), usas la temperatura adecuada (configuraciones), pero después de meterlo en el horno (comenzar a entrenar) solo puedes rezar para que todo salga bien.

![[Pasted image 20230924163306.png]]

No tendrás idea de si tendrás éxito o no hasta que esté terminado (aunque puedes [verificar el progreso](https://aituts.com/stable-diffusion-lora/#generating-sample-images) en todo momento).

**Por eso es importante sumergirse y HORNEAR** , en lugar de intentar crear el "LoRA perfecto". ¡Deberías dedicar más tiempo a hornear y menos a leer!

**Un LoRA fallido le enseñará mucho más que cualquier guía que lea.** Utilice los números predeterminados a continuación y solucione el problema desde allí. Es **imposible** predecir por completo qué va a hacer la IA, con qué elementos va a luchar, cómo aceptará las imágenes dadas, etc.

Lo bueno: cada LoRA que entrenes te brindará una mejor intuición y nuevos conocimientos sobre cómo entrenar mejor al siguiente.

No pretendo que este sea el tren "correcto". Estas son algunas de las mejores prácticas que aprendí al capacitar a alrededor de 40 LoRA.

He escrito una guía separada para entrenar [SDXL LoRA con Runpod](https://aituts.com/sdxl-lora/) .

Antes de comenzar necesitarás:

- **GPU NVIDIA** con al menos 6 GB, pero en realidad 8 GB o más de VRAM (existen soluciones para tarjetas AMD, pero no están maduras)
    - Si no tienes NVIDIA, no tienes suficiente VRAM o simplemente quieres entrenar más rápido, puedes usar [Google Colab para tu entrenamiento](https://colab.research.google.com/github/camenduru/kohya_ss-colab/blob/main/kohya_ss_colab.ipynb) .
- **Un modelo fundamental:**
    
    - Muchos (pero no todos) modelos son adecuados como modelo básico/fundamental. Elija un modelo que sea bueno en lo que intenta hacer. Más sugerencias de modelos a continuación.
    
    - Aquí hay algunas ideas:
        - Para estilo anime/dibujos animados, elija un [modelo de la familia NAI](https://aituts.com/anime-models#nai) : NAI Diffusion, AnythingV3.0, AnythingV4.0, AnythingV4.5, AnythingV5.
        - Para un estilo realista, elija Stable Diffusion v1.5, o si tiene 12GM VRAM, puede optar por [SDXL](https://aituts.com/sdxl/) .

Esto es lo que haremos:

1. Prepare training images
2. Create folder structure
3. Install Koyha SS
4. Captioning/Tagging
5. Train LoRA

### Paso 1: preparar imágenes de entrenamiento

Decide cuál quieres que sea el tema de tu LoRA antes de comenzar.

Uno de nuestros [suscriptores](https://aituts.com/join/) me envió un conjunto de datos de Lisa, la artista de K-pop:

![[Pasted image 20230924163527.png]]

Usaré esto como ejemplo para entrenar un LoRA paso a paso. Aquí están las imágenes que LoRA es capaz de producir cuando esté terminado:

![[Pasted image 20230924163547.png]]

El conjunto de datos tiene 34 imágenes. Cuantas más imágenes mejor, pero **la calidad importa** . No agregue imágenes por agregar imágenes si son de baja calidad.

Utilice únicamente archivos JPG y PNG. Convierta cualquier imagen WEBP a JPG/PNG antes de comenzar.

Si creas un personaje, asegúrate de que tus imágenes tengan:

- Poses unicas
- Ángulos de zoom únicos
- Diferentes trajes
- Colores diferentes
- Mayor resolución que 512x512

#### Fuentes de imágenes

Aquí hay algunos sitios web útiles para obtener imágenes:

- [Pinterest](https://www.pinterest.com/) : Excelente por su versatilidad. Probablemente encontrarás lo que estás buscando.
- [Danbooru](https://danbooru.donmai.us/) : el sitio web booru más grande: la mayoría de los modelos de puntos de control de anime y LoRA obtienen sus imágenes desde aquí
- [Safebooru](https://safebooru.donmai.us/) : Como Danbooru, pero solo para imágenes SFW
- [MovieStillsDB](https://www.moviestillsdb.com/) : Archivo de más de 1 millón de imágenes fijas de películas, con posibilidad de búsqueda por actores y título de la película.

### Paso 2: estructura de carpetas

Cree esta estructura de carpetas:

***img***: Esta es la carpeta que contendrá la carpeta de imágenes.
Dentro de esta carpeta 'img', crear una subcarpeta siguiendo la convención `$REPEATS_TRIGGER CLASS$`.

- ``REPEATS`` es el número de pasadas que realizará el algoritmo de entrenamiento sobre cada imagen por época. Un buen número es 200-400 dividido por la cantidad de imágenes que tienes, redondeando hacia abajo. Por ejemplo, si tienes 34 imágenes, $200/34 \approx 6$.

- `TRIGGER` es algo único que se mencionará en su mensaje para que LoRA se aplique correctamente. No usaré "lisa" porque el modelo podría interpretarlo como otra cosa.

- `CLASS` es la clase amplia de cosas a las que pertenece su tema. En este caso, usaremos 'woman'.

Entonces, llamaría a mi carpeta `6_lisabp woman`.

¡No pongas nada más dentro de esta carpeta!

***model***: Esta carpeta es donde se colocarán tus modelos finales.

***log*** (opcional): dónde irán tus registros.

***reg*** (opcional): aquí es donde se colocan las imágenes de regularización. Esto es opcional, pero muy recomendable. Cree una subcarpeta con el siguiente formato: `1_CLASS`, donde `CLASS` debe ser el mismo que se usó en el nombre de la carpeta de imágenes arriba. En este ejemplo, usaríamos `1_woman`.

Me gusta poner todo en la misma carpeta para mantenerme organizado. Terminaré con una estructura de carpetas similar a esta:

![[Pasted image 20230924164224.png]]


**Paso 3: Imágenes de Regularización para Entrenamiento**

Las imágenes de regularización son *opcionales*, pero pueden mejorar tu entrenamiento. Puedes excluirlas por completo si lo prefieres.

Existen varias formas de obtener imágenes de regularización. Puedes descargar conjuntos prefabricados desde enlaces como este:

[Conjuntos de Imágenes de Regularización](https://huggingface.co/datasets/ProGamerGov/StableDiffusion-v1-5-Regularization-Images/tree/main)

En tu caso, utilizarás el conjunto de datos "mujer" llamado `woman_v1-5_mse_vae_ddim50_cfg7_n4420.zip`.

Descarga el conjunto de imágenes que consideres más adecuado para tu tema y descomprímelo.

Luego, copia al menos *X* número de imágenes a la subcarpeta que creaste previamente en la carpeta de regularización (en mi caso, se llama `1_woman`). Donde *X* se calcula como REPETICIONES * NÚMERO_DE_IMÁGENES_ENTRENAMIENTO.

En nuestro caso, esto significa 6 * 34 = 204 imágenes.

### Paso 4: Instale Koyha SS

Koyha SS es la mejor interfaz de usuario de su clase para modelos de entrenamiento en este momento.

#### Dependencias requeridas

- Instalar [Python 3.10](https://www.python.org/ftp/python/3.10.9/python-3.10.9-amd64.exe)
    - asegúrese de marcar la casilla para agregar Python a la variable de entorno 'PATH'
- Instalar [Git](https://git-scm.com/download/win)
- Instale [Visual Studio 2015, 2017, 2019 y 2022 redistribuible](https://aka.ms/vs/17/release/vc_redist.x64.exe)

Abra una ventana del símbolo del sistema (en la barra de búsqueda, busque "símbolo del sistema", haga clic en Símbolo del sistema).

En el símbolo del sistema, navegue hasta donde desea instalar Kohya.

Utilice este comando para moverse a la carpeta (presione `Enter`para ejecutarlo):

```
cd FOLDER_NAME
```

Utilice este comando para hacer una copia de seguridad de una carpeta:

```
cd ..
```

Utilice este comando para enumerar todas las carpetas dentro de la carpeta en la que se encuentra. Esto puede ayudarle a orientarse:

```
dir
```

Como ejemplo, instalaré Koyha en mi `Documents` carpeta. Yo escribiría este comando:

```
cd documents
```

![[Pasted image 20230924164534.png]]

Copie y pegue cada línea, una por una, y presione Entrar.

```
clon de git https://github.com/bmaltais/kohya_ss.git
 cd kohya_ss
 .\setup.bat
```

Ingrese 1 y luego 1 para las opciones:

![[Pasted image 20230924164633.png]]

**Nota: la instalación completa de los paquetes puede tardar un poco.**

Cuando se complete la instalación, ingrese `4`, que es la opción de `Start Kohya_ss GUI in browser`.

En unos segundos debería darte el mensaje de éxito:

`Running on local URL: http://127.0.0.1:7860`

Vaya a esta URL en su navegador web [http://127.0.0.1:7860](http://127.0.0.1:7860) para abrir la interfaz:

![[Pasted image 20230924164705.png]]

### Step 5: Caption Images
Cada imagen de tus datos de entrenamiento necesita un título correspondiente, o un `.txt`archivos que describen el contenido de la imagen.

**Afortunadamente, Koyha tiene una herramienta incorporada para reconocer y subtitular imágenes automáticamente** .

Nos ayudará a subtitular con oraciones en lenguaje natural como: " `girl with yellow dress sitting down`", así como etiquetas divididas por comas como " `1girl, yellow dress, sitting`". El estilo de los subtítulos depende de si el tema es realista o anime/estilizado.

#### Para sujetos realistas

Clickea en  `Utilities` pestaña -> `Captioning` pestaña -> `BLIP Captioning` pestaña.

En `Image folder to caption`, selecciona la carpeta con tus imágenes de entrenamiento.

![[Pasted image 20230924164854.png]]

Para la configuración:

1. **`Prefix to add to BLIP caption`**_:_ agregue la palabra desencadenante elegida, **seguida de** una coma y un espacio. En nuestro caso 'lisabp, '
2. **`Batch size`**_:_ Manténgase en 1-2, a menos que tenga una GPU con mayor VRAM.
3. **`Use beam search`**_:_ Comprobado
4. **`Number of beams`**_:_ aumentar esta configuración produce subtítulos más coherentes tipo "oración". Establezca esto entre 10 y 15.
5. **`Min length`**_:_ Establezca esto en 25-30; de lo contrario, los subtítulos serán demasiado cortos.

Golpear " `Caption Images`". La primera vez que haga esto, tardará un poco en descargar el subtítulo BLIP. Consulte el símbolo del sistema para ver las actualizaciones de estado.

Una vez finalizados los subtítulos, la herramienta colocará automáticamente los archivos de subtítulos en la misma carpeta que sus imágenes de entrenamiento.

#### Para anime/sujetos estilizados

Los temas de anime requieren un estilo de subtítulos diferente.

Clickea en el `Utilities` pestaña -> `Captioning` pestaña -> `WD14 Captioning`pestaña.

En `Image folder to caption`, selecciona la carpeta con tus imágenes de entrenamiento.

Si estás entrenando un estilo LoRA, puedes dejar la configuración predeterminada. Si entrenas a un personaje LoRA cambia el `Character Threshold` ajuste a `0.7`

![[Pasted image 20230924165024.png]]

Golpear " `Caption Images`". La primera vez que haga esto, tardará un poco en descargar el subtítulo Blip. Consulte el símbolo del sistema para ver las actualizaciones de estado.

Una vez finalizados los subtítulos, la herramienta colocará automáticamente los archivos de subtítulos en la misma carpeta que sus imágenes de entrenamiento.

![[Pasted image 20230924165102.png]]

### Paso 6: Entrenamiento

¡Finalmente estás listo para entrenar!

**Asegúrate de cambiar a la pestaña `LoRA`  y no estar en la pestaña `Dreambooth` .** Esto ha causado mucha confusión porque el contenido de las pestañas parece el mismo.

![[Pasted image 20230924165231.png]]

#### Selección de modelo

Seleccione el modelo fundamental (base) en el que entrenará su LoRA.

`Model Quick Pick`le permitirá utilizar los modelos base de StabilityAI y sus socios:

![[Pasted image 20230924165258.png]]

Si seleccionas `custom`, puedes elegir un modelo que hayas descargado.

![[Pasted image 20230924165314.png]]

Otras opciones:

- **`v2`casilla de verificación** : marque la casilla de verificación v2 si está utilizando Stable Diffusion v2.0 o v2.1 como base, o un modelo ajustado a partir de estos.
- **`SDXL Model`casilla de verificación** : Marque la casilla de verificación Modelo SDXL si está utilizando SDXL v1.0 como base o un modelo ajustado desde SDXL. **Esto requiere un mínimo de 12 GB de VRAM** . Si no tienes suficiente VRAM, prueba Google Colab.

Los modelos base funcionan bien; A veces, los modelos personalizados funcionarán mejor. Aquí te dejo algunos modelos que recomiendo para entrenar:

- **[NeverEnding Dream](https://aituts.com/models#neverending-dream)**   : gran modelo para el entrenamiento de personajes y temas específicos (BLIP o WD14 funcionan)
- **[Anything V5](https://aituts.com/models#anything-v5)**   : Anything V3 inició una generación de LoRA de anime. Esta es la próxima versión del mismo autor. (Subtítulos WD14)
- **[ReV Animated](https://aituts.com/models#rev-animated)**   : un modelo confiable y predecible que puede usar como alternativa (BLIP o WD14 funcionan)
- **[AnyLora](https://civitai.com/models/23900)** : modelo creado para entrenar anime LoRA (subtítulos WD14)

#### Archivo de configuración

[**Descargue el archivo de configuración**](https://pastebin.com/raw/ZgbbrE7f) (Vaya al enlace, luego haga clic derecho en la página -> `Save as`), luego cambie la extensión para que el nombre del archivo sea `pastebin.com_raw_ZgbbrE7f.json`

Haga clic en el " `Configuration File`"menú desplegable y luego `Open`.

![[Pasted image 20230924165457.png]]

Seleccione el archivo que acaba de descargar y luego presione `Load`.

#### Establecer carpetas

Ve a la " `Folders`"pestaña y configure sus carpetas:

- `Image folder`: ubicación de `img` carpeta que creó en el paso anterior (NO la subcarpeta numerada dentro de ella)
- `Output folder`: carpeta para colocar sus LoRA cuando esté completo
- `Regularization` `folder` **(opcional)** : ubicación de la carpeta de registro que contiene una subcarpeta con sus imágenes de regularización
- `Logging` `folder`(opcional) : carpeta donde enviar sus registros
- `Model output name`: Nombre de su LoRA generado. Por lo general, me gusta nombrar LoRA con la palabra desencadenante seguida de un número de versión como " `_v1`", en caso de que entrene algunos (la mayoría de las veces, se necesitan varios intentos para hacerlo bien).

![[Pasted image 20230924165626.png]]

#### Épocas y pasos

Creo que los personajes LoRA salen mejor cuando se entrenan entre 1500 y 3000 pasos.

Hay varias formas de lograrlo, pero primero comprendamos cómo se calculan los pasos:

**pasos totales =** ( **number of images** * **repeats** * **epochs**  * **regularization multiplier** ) / **batch size**

- **==numero de imagenes==** se explica por sí mismo, es la cantidad de imágenes de entrenamiento que recopiló anteriormente y colocó en una subcarpeta.
- **==repite==** es el número que usamos en el nombre de esta carpeta que contiene nuestras imágenes de entrenamiento. En mi ejemplo, se trataba de 6_lisabp woman, siendo **6** el número de repeticiones.
- **==épocas==** es una configuración que puedes cambiar en el `Parameters` subpestaña. Muestra cuántas pasadas completas realiza el algoritmo de aprendizaje a través de todo el conjunto de datos de entrenamiento.
- **==multiplicador de regularización==** es 1 o 2. Si no está utilizando imágenes de regularización, este es 1 (no sucede nada). Si está utilizando imágenes de regularización, esto es 2 (los pasos se duplican).
- **==tamaño del lote==** es una configuración que puedes cambiar en el `Parameters` subpestaña. Se refiere a cuántas imágenes se entrenan a la vez.

**Puede utilizar su número de imágenes como punto de partida para calcular estos otros números.**

**Las épocas** son bastante arbitrarias y en realidad no son necesarias. Son simplemente una forma de dividir su entrenamiento en partes, de modo que pueda generar "modelos de progreso" en cada época durante el proceso de entrenamiento para verificar en qué punto su modelo se sobreentrena.

Volvamos a mi ejemplo: tengo 34 imágenes de lisabp y mi carpeta se llama `**6_lisabp**`. Eso le dice a Kohya que repita cada imagen 6 veces, por lo que con una época obtienes 204 pasos (34 imágenes * 6 repeticiones = 204 pasos).

Si configuro las épocas en 10, ejecutaré el entrenamiento durante un total de 2040 pasos (34 imágenes * 6 repeticiones * 10 épocas = 2040 pasos), lo que se encuentra dentro de mi rango de pasos óptimo de 1500-3000.

Ahora, ¿por qué no establecería mis repeticiones en 60 y mis épocas en 1? ¿No daría eso exactamente el mismo resultado? (60 repeticiones * 34 imágenes * 1 época = 2040 pasos)

**Sí, lo sería** . No hay diferencia técnica si entrenamos para 1 repetición y 100 épocas en comparación con 100 repeticiones y 1 época.

Sin embargo, en la práctica hay una gran diferencia. Hay una configuración que le permite **generar un modelo en cada época** . Si solo tuvieras una época, solo obtendrías el modelo final. Si tengo 10 épocas, obtendré 10 versiones del modelo, generadas cada 204 pasos.

Esto me permite probar cada modelo para ver en qué punto se entrena mejor y en qué punto el modelo se sobreajusta.

Por lo tanto, cuantas menos repeticiones tengamos, más épocas podamos tener, más modelos podremos generar a lo largo del proceso de entrenamiento, lo que nos ayudará a elegir el mejor número real de pasos para entrenar nuestro modelo.

Es por eso que recomendé ajustar las **repeticiones** para que una sola época tenga entre 200 y 400 pasos. Esto le permitirá tener muchos modelos para elegir.
#### ¡Empezar a entrenar!

Golpear `Train model` y comenzará el entrenamiento. En la ventana del símbolo del sistema, verá una barra de progreso:
![[Pasted image 20230924170301.png]]

La capacitación durará entre 15 minutos y 2 horas, según su GPU y el tamaño de su conjunto de datos.

Una vez finalizado su LoRA, puede usarlos como [se describió anteriormente en esta guía](https://aituts.com/stable-diffusion-lora/#usage) con AUTOMATIC1111 WebUI.

Asegúrese de incluir la frase clave LoRA como palabra desencadenante en su mensaje. Como ejemplo:

(Lo más probable es que no quieras establecer el peso en un máximo de 1)

```
lisabp with long black hair golden hour light <lora:lisabp:0.85>
```

![[Pasted image 20230924170342.png]]

Puedes probar tu LoRA con diferentes modelos de puntos de control (incluido el modelo que usaste para entrenarlo). Mucho de esto es aleatorio: algunos LoRA simplemente funcionan mucho mejor con algunos modelos que con otros.

### Configuración de Koya
No existen ajustes de entrenamiento "perfectos": los ajustes siempre dependerán del sujeto y de tus imágenes.

Profundicemos en los que quizás queramos cambiar:
![[Pasted image 20230924170429.png]]


#### 1. Tamaño del lote

Cuántas imágenes se entrenan simultáneamente.

Los valores más altos aceleran el entrenamiento a costa del uso de VRAM.

Si usted tiene:

- 6-8 GB de VRAM: déjelo en 1
- 10 GB: configurado en 2
- 12 GB: configurado en 3

(NOTA: deberá cambiar la tasa de aprendizaje proporcional al tamaño del lote, consulte **4** )

#### 2. Época

El número de **_épocas_** es la cantidad de pases completos que realiza el algoritmo de aprendizaje a través de todo el conjunto de datos de entrenamiento.

En cada época, el algoritmo revisa todos los datos de entrenamiento y actualiza el LoRA en función de la información acumulada.

**_Las repeticiones_** se refieren a cuántas veces se entrena cada imagen individual _dentro de una época_ .

El número de repeticiones lo establece el nombre de esta carpeta dentro del imgcarpeta: `**11_lisabp woman**`. Esto significa que tendremos 11 repeticiones por imagen.

Si tengo 34 imágenes y 11 repeticiones, una época será 34 * 11 = 374 pasos.

Si especifico 8 épocas, entrenaré en un total de 8 * 374 = 2958 pasos.

**Más épocas** suelen producir mejores resultados.

Recomiendo no exceder los 3500 **pasos totales** para un LoRA.

##### **Guardar cada n épocas**

Esta es una excelente manera de generar modelos a mitad de camino durante la capacitación.

A veces los modelos entrenados en demasiados pasos quedan _demasiado cocidos_ .

Es posible que el modelo que desee no sea el modelo final, sino uno de los anteriores.

Si tengo 986 pasos por época, 3 épocas, y configuro mi `Save every n epoch`a 1, obtendré 3 modelos entrenados en 986, 1972 y 2958 pasos.

#### 3. Precisión mixta/Guardar precisión

**Precisión mixta** : bf16 entrena más rápido que fp16, pero solo funciona en GPU 30XX y 40XX.

Sin embargo , mantenga siempre **Guardar precisión** como fp16.

#### 4. Tasa de aprendizaje/Tasa de aprendizaje del codificador de texto/Tasa de aprendizaje Unet

Debe ajustar estos tres parámetros de acuerdo con el tamaño de su lote. Serán el tamaño de su lote dividido por 1000.  
Ejemplo: tamaño de lote de **3**

- Tasa de aprendizaje: **0,0003**
- Tasa de aprendizaje del codificador de texto: **0,0003**
- Tasa de aprendizaje unet: **0,0003**

#### 5. Optimizador

En GPU 10XX, no podrás usar AdamW8bit

En su lugar, cambie esto a AdamW

#### 6. Rango de red (dimensión) / Alfa de red

Generalmente, es mejor mantener el rango de red (dimensión) y el alfa de red iguales.

Para los LoRA de estilo, 256 es un buen número para usar tanto para Network Rank como para Network Alpha.

Los personajes LoRA no necesitarán más de 128 tanto para Network Rank como para Network Alpha.

#### 7. Resolución máxima

Si tienes una gran cantidad de VRAM, puedes entrenar con una resolución más alta, como 768x768. De lo contrario, déjelo en 512x152.

### Generando imágenes de muestra

Puede optar por generar muestras cada X número de pasos en `Sample images config`

![[Pasted image 20230924170806.png]]

Cuanto más frecuentemente hagas muestras, más lento se entrenará LoRA. Sin embargo, esta es una buena manera de ver si LoRA va como usted desea.

Generalmente, una muestra cada 200-400 pasos es adecuada para medir el progreso del entrenamiento.

Simplemente incluya un mensaje de muestra relevante seguido de:

```
--n low quality, worst quality, bad anatomy, --w 512 --h 512 --d 1 --l 7.5 --s 20
```

Las muestras se generarán dentro de una carpeta dentro del directorio de salida que especificó anteriormente.

(Nota: muchas muestras, especialmente las primeras, pueden resultar distorsionadas, esto es normal)

## Otras lecturas

Civitai. "[Making a LoRA is like baking a cake](https://civitai.com/articles/138/making-a-lora-is-like-baking-a-cake), https://civitai.com/articles/138/making-a-lora-is-like-baking-a-cake."

Zoomy Izumi. "[My Lora Experiment Part 4](https://www.zoomyizumi.com/my-lora-experiment-part-4/), https://www.zoomyizumi.com/my-lora-experiment-part-4/."


## Preguntas más frecuentes

****¿Cuántas imágenes necesito?**  


Se recomienda tener entre 30 y 150 imágenes bien etiquetadas, aunque puedes crear un LoRA perfectamente útil con tan solo 10 imágenes.  

****¿Necesito recortar imágenes?**  


No, se pueden entrenar imágenes de cualquier relación de aspecto y tamaño, el script cambia su tamaño automáticamente y las entrena de manera que conserve su relación de aspecto. Algunos utilizan [herramientas de recorte de imágenes masivas](https://www.birme.net/?target_width=512&target_height=512) para hacer que sus datos de entrenamiento sean cuadrados uniformes, pero es en gran medida redundante y puede recortar partes importantes de la imagen.  

****¿Qué define las "imágenes de alta calidad"?**  


Para un personaje, debe haber una variación saludable de ángulos, poses y vestimenta.  
Debe ser una mezcla de imágenes estáticas y dinámicas, con fondos más simples y un solo sujeto. No debes tener objetos complejos; debes evitar que el sujeto sostenga objetos.  
  
Los subtítulos son los reyes: 50 imágenes bien etiquetadas generarán un LoRA mejor que 150 imágenes mal etiquetadas.

****¿ Cuánto tiempo** tardan los LoRA **en entrenarse?**  


Con esta configuración, puede tardar entre 15 minutos y aproximadamente 2 horas como máximo, dependiendo de su GPU.




















































___
%%
Vínculos:
[[000-Menú Stable Diffusion XL 📃|Menú Stable diffusion XL]]

tags:
#pagstable_diffusion_xl #stable_diffusion_xl #stable_diffusion 
%%