---
ID: 20
-nombre: Guía de configuración de Stable Diffusion para principiantes (mejores configuraciones recomendadas)
"-tags:":
---
___
# Guía de configuración de Stable Diffusion para principiantes (mejores configuraciones recomendadas)
Si recién está comenzando con Stable Diffusion, es posible que se pregunte por qué sus imágenes no son tan buenas como las que ve en línea.

Ese fui yo, durante mucho tiempo. Inicialmente, pensé que mis indicaciones eran el problema. Entonces aprendí cómo [mejorar mis indicaciones](https://aituts.com/stable-diffusion-prompts/)  (prompts) y luego mejorar la imagen con [LoRAs](https://aituts.com/stable-diffusion-lora/) e [inversiones textuales](https://aituts.com/textual-inversion/) .

Sin embargo, en un momento descubrí que todo lo que tenía que hacer era modificar algunas configuraciones para obtener imágenes drásticamente mejoradas.

**Esta guía cubrirá todas las configuraciones básicas de Difusión estable y brindará recomendaciones para cada una.**

Como ejemplo, usaremos la misma imagen y le aplicaremos varias configuraciones.

Al final de esta guía, podrá pasar de la imagen de izquierda a la derecha:

![[Pasted image 20230924125724.png]]


**Conclusiones clave**

- **La configuración de mayor impacto que utilizará son las Hires. fix checkbox***  Probablemente esta sea la razón por la que su generación no se ve tan bien como las que ve en línea. Esto mejorará sus imágenes y aumentará mucho la calidad.
- **Para sampling method** : recomiendo ==DPM++ 2M Carras== como muestreador de uso general
- **Para sampling steps** : puede utilizar pasos de muestreo más bajos (20-30) con el muestreador Euler, pero la mayoría de los muestreos requieren un poco más de pasos (30-40) para obtener mejores resultados.

## Siguiendo adelante

Ya debería tener instalado AUTOMATIC1111 ( [instrucciones de NVIDIA](https://aituts.com/stable-diffusion-on-windows-automatic1111/) / [instrucciones de AMD](https://aituts.com/stable-diffusion-amd/) / [instrucciones de Mac](https://aituts.com/stable-diffusion-mac-m1/) / [instrucciones de Google Colab](https://aituts.com/stable-diffusion-google-colab/) ).

Esta guía utilizará el [modelo animado de ReV](https://civitai.com/models/7371/rev-animated) .

Elegí este modelo porque es muy versátil y las lecciones aprendidas de este modelo serán ampliamente aplicables a la mayoría de los modelos.

Para seguir mis ejemplos, estas son las indicaciones y configuraciones que estoy usando:

```
(elf:1.2) 1girl, flowing white dress, white cloak, flowing, (fabric with intricate pattern:1.2), (insanely detailed:1.2), ((masterpiece)), (painting:1.1), (digital painting:1.1)
Negative prompt: (worst quality:2), (low quality:2), (normal quality:2), (b&w:1.2), (black and white:1.2), (blurry:1.2), (out of frame:1.2), (ugly:1.2), (cross-eyed:1.2), (disfigured:1.2),(deformed:1.2), (extra limbs:1.2), (b&w:1.2), (blurry:1.2), (duplicate:1.2), (morbid:1.2), (mutilated:1.2), (poorly drawn hands:1.2), (poorly drawn face:1.2), (mutation:1.2), (deformed:1.2), (bad anatomy:1.2), (bad proportions:1.2), (watermark:1.5), (text:1.5), (logo:1.5)
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 2272519906, Size: 512x768, Model hash: 4199bcdd14, Model: revAnimated_v122, Version: v1.4.1
```

_No entraré en detalles sobre las indicaciones de esta guía. Si tienes curiosidad por saber qué hacen cosas como "(elf:1.2)", echa un vistazo a la [guía de indicaciones](https://aituts.com/stable-diffusion-prompts/) ._

**Cómo copiar estas configuraciones:**

Si copia todo el bloque anterior y lo pega en el campo Aviso de AUTOMATIC1111, luego hace clic en la flecha que apunta hacia abajo debajo del botón Generar, AUTOMATIC1111 leerá la configuración en su aviso y la aplicará a la interfaz.

![[Pasted image 20230924130904.png]]

Copie y pegue el bloque de texto de arriba, luego haga clic en la flecha azul debajo del botón Generar

![[Pasted image 20230924130935.png]]

AUTOMATIC1111 analizará el bloque de texto y aplicará la configuración a la interfaz.

![[Pasted image 20230924130957.png]]

Hay mucho camino por recorrer, ¡así que comencemos!

## Semilla

Comenzaremos con la configuración Semilla, aunque se encuentra en la parte inferior de la configuración.

La semilla es lo que le permite mantener la coherencia de sus imágenes a lo largo de varias generaciones.

Determina la imagen aleatoria de "ruido" latente que su generación utiliza como punto de partida.

Si 2 generaciones comparten la misma semilla y el mismo entorno, saldrán exactamente iguales.

Una técnica común es mantener la semilla igual pero modificar el mensaje y la configuración, para que pueda ver solo los efectos de esos cambios. Estas imágenes comparten la misma semilla con pequeñas variaciones de indicaciones:

![[Pasted image 20230924131315.png]]


El valor predeterminado es -1, que significa aleatorio. Esto aleatoriza la semilla cada vez que se genera una imagen.

![[Pasted image 20230924131725.png]]

El **Dice button** restablece el valor a -1.

El **Recycle button** reutiliza la semilla de la última generación. Haz clic en esto cuando llegues a una generación que te guste y con la que quieras experimentar. En la práctica, hacer clic aquí hará que la semilla sea constante porque siempre estás usando la última semilla.

==**Recomendación:** establezca la semilla en -1 (aleatorio), a menos que tenga una razón específica para no hacerlo. A veces las indicaciones funcionan bien con algunas semillas y no con otras, por lo que tiene sentido experimentar con diferentes semillas.==

==**Hágalo usted mismo:** utilicé la misma semilla para generar todas las imágenes de esta guía para que podamos ver el efecto de las configuraciones individuales. Si desea seguir y obtener las mismas imágenes, use la semilla 2272519906.==

La **casilla de verificación Extra** , cuando está marcada, le brinda un par de configuraciones más:

![[Pasted image 20230924132019.png]]

#### **Semilla de variación**

Piensa en ello como una semilla _dentro de_ tu semilla. Usarás esto cuando estés bastante satisfecho con tu imagen, pero aún quieras cambiarla ligeramente.

Compara estas imágenes. Todos usan la misma semilla, 2272519906. El primero no usa una semilla de variación y el resto usa semillas de variación aleatoria:

![[Pasted image 20230924132057.png]]

Semillas de variación aleatoria con una fuerza de variación de 0,5

Al igual que con la semilla de alto nivel, la semilla de variación viene con un **botón de dado** que la establecerá en -1 (al azar cada vez) y un **botón de reciclaje** que reutilizará la última semilla de variación utilizada.

#### **Fuerza de variación**

Establece la fuerza de la semilla de variación. Cuanto más bajo sea, más cerca de la imagen original estará la nueva imagen.

El valor predeterminado de 0 será el mismo que no utilizar una semilla de variación.

![[Pasted image 20230924132152.png]]


**Recomendación:** utiliza semillas de variación cuando realmente te guste una imagen pero no te guste un detalle específico. Configurar la semilla de variación le permitirá volver a rodar y obtener imágenes muy similares.

Consulte la [Guía de semillas de difusión estable](https://aituts.com/stable-diffusion-seed/) para ver más ejemplos.

## Método de muestreo

Este es el algoritmo que se utiliza para generar su imagen.

Aquí está la misma imagen generada con diferentes samplers (20 pasos de muestreo).

Notarás que algunos samplers parecen producir resultados de mayor calidad que otros. **Esto no está escrito en piedra.** Diferentes samplers funcionarán mejor para diferentes prompts y modelos.

![[Pasted image 20230924132457.png]]

![[Pasted image 20230924132508.png]]

![[Pasted image 20230924132518.png]]

**Recomendación:** _Euler a_ es un buen sampler para la creación de prototipos, pero los samplers de Karras pueden producir mejores resultados. Recomiendo _DPM++ 2M Karras_ como muestreador versátil y de alta calidad.

## Pasos de muestreo

Esta es la cantidad de pasos que está dando a Stable Diffusion para "dibujar" su imagen.

Para obtener una explicación más técnica, consulte esta [discusión de los pasos](https://jalammar.github.io/illustrated-stable-diffusion/#the-components-of-stable-diffusion) .

Más pasos no significa que la imagen saldrá mejor. Piense en ello como hornear un pastel. Hay un punto perfecto para sacar el bizcocho del horno. No querrás pasar por encima o por debajo.

El número de pasos óptimos también dependerá del método de muestreo que esté utilizando. Echa un vistazo a algunas de las imágenes que no quedaron tan bien con 20 pasos, cuando se generaron con pasos más altos:

### Prueba de pasos de muestreo con Euler a

![[Pasted image 20230924132626.png]]
![[Pasted image 20230924132635.png]]

El muestreador Euler a funciona mejor con pasos más bajos. En este ejemplo, creo que la imagen sale mejor con 30 y 40 pasos.

### Prueba de pasos de muestreo con DPM++ 2M Karras
![[Pasted image 20230924132720.png]]
![[Pasted image 20230924132729.png]]

Para la mayoría de los demás muestreadores, los pasos más altos funcionan mejor. Creo que el mejor aquí es el de 35 pasos.

==**Recomendación:** 35 pasos funcionan muy bien para la mayoría de los muestreadores.==

## Restore Faces
Puede utilizar esta casilla de verificación para reparar rápidamente caras estropeadas.

![[Pasted image 20230924132839.png]]


==**Recomendación:** utilice esta función únicamente si tiene poco tiempo. Hires Fix (abajo) es mucho más poderoso que Restore Faces.== I ==Tampoco recomiendo comprobar Restore Faces y Hires Fix: no funcionan bien juntos.==


## Tiling
Esto convertirá la imagen en un mosaico, de modo que puedas repetirla para crear patrones perfectos.

![[Pasted image 20230924133216.png]]
Frutas teseladas con modelo Stable Diffusion v1.5

Desafortunadamente, es completamente inutilizable con la mayoría de los modelos personalizados. Incluso si está utilizando el modelo base Stable Diffusion v1.5, solo puede utilizar indicaciones simples.

==**Recomendación:** compre Midjourney y use el [comando --tile](https://aituts.com/midjourney-tile/)==

## Hires Fix
![[Pasted image 20230924133303.png]]

Si solo pudiera recomendar a los principiantes una única configuración, sería esta.

Creo que el nombre es un poco vergonzoso, porque Hires Fix _está_ **mejorando** . Sin embargo, debes verificarlo para ver la palabra real "upscaler", y mucha gente termina perdiéndola.

Hires Fix mejora su imagen de acuerdo con la configuración que le proporciona. Estas son las configuraciones:

### Upscaler
AUTOMATIC1111 le ofrece varios escaladores de forma predeterminada.

También puede descargar y usar escaladores personalizados: aquí hay una [base de datos de escaladores](https://openmodeldb.info/) que puede usar.

Recomiendo los siguientes escaladores:

1. [4x-UltraSharp](https://mega.nz/folder/qZRBmaIY#nIG8KyWFcGNTuMX_XNbJ_g) (descarga el archivo .pth)
2. [4x_NMKD-Siax](https://icedrive.net/s/43GNBihZyi) (busque la carpeta "NMKD Siax" y descargue el archivo .pth que contiene)
3. [4x_NMKD-Superscale](https://icedrive.net/s/43GNBihZyi) (busque la carpeta "NMKD Superscale" y descargue el archivo .pth que contiene)

Colócalos en la carpeta. `stable-diffusion-webui/models/ESRGAN`y vuelva a cargar la interfaz de usuario (botón Recargar interfaz de usuario en la parte inferior de la pantalla) para verlos en el menú desplegable de Upscalers.

Echemos un vistazo a nuestra imagen generada con Hires Fix y diferentes escaladores:

![[Pasted image 20230924134223.png]]

![[Pasted image 20230924134232.png]]

Semillas de variación aleatoria con una fuerza de variación de 0,5

==**Recomendación:** descargue 4x-UltraSharp, 4x_NMKD-Siax y 4x_NMKD-Superscale. Estos son escaladores de propósito general que funcionarán bien con todo tipo de contenido. La diferencia real entre estos es sutil, pero cada uno tiene sus usos específicos.==

### Upscale by
Este es el múltiplo por el que le gustaría mejorar su imagen.

Junto a la casilla Hires fix checkbox, habrá una etiqueta que muestra la resolución de la imagen de salida.

512x768 -> Ampliado por 2 -> 1024x1536

512x768 -> Ampliado por 3 -> 1536x2304

512x768 -> Ampliado por 4 -> 2048x3072

¡La ampliación es computacionalmente costosa!

==**Recomendación** : Comience con 2x. Realmente sólo puedes ir más allá con una GPU potente.==

### Hires steps
Estos son los pasos de ampliación que se producen después de los pasos de muestreo.

Sampling steps + Hires steps = Total steps.

El valor predeterminado es 0, lo que significa: utilice el mismo número que los sampling steps.

Si sus sampling steps son 35 y tiene Hires steps en 0, obtendrá 35 Hires steps para un total de 70 image steps.

Los pasos de Hires son mucho más lentos que los pasos de muestreo, por lo que utilizar Hires Fix lleva mucho más tiempo que una generación normal.

Al igual que los pasos de muestreo, existe algo demasiado alto y demasiado bajo en los pasos de Hires.

Eche un vistazo a estos ejemplos:

![[Pasted image 20230924135004.png]]

No obtienes un resultado adecuado con 5 pasos de contratación, y después de 15 los resultados no son ninguna diferencia (en todo caso, las manos empeoran).

==**Recomendación** : 15 pasos de Hires es un buen punto óptimo entre velocidad y calidad. Aumentar más allá de este punto no le beneficiará demasiado.==

### Denoising strength
Piense en esto como la fortaleza del escalador durante los pasos de escalamiento.

Establecer esto en 0 significa que el escalador no hace nada y obtendrá el mismo resultado que si no hubiera usado Hires fix.

El valor predeterminado es 0,7.

La intensidad óptima de eliminación de ruido dependerá del escalador que esté utilizando.

A continuación se muestra una comparación de diferentes intensidades de eliminación de ruido de mejora:
![[Pasted image 20230924135152.png]]
![[Pasted image 20230924135159.png]]

**Recomendación** : el valor predeterminado de 0,7 suele ser demasiado alto. Experimente con valores de 0,3 a 0,5.

## Width & Height
Pasemos al resto de configuraciones.
![[Pasted image 20230924135304.png]]

El ancho y el alto son la resolución de la imagen antes de aplicar la ampliación.

==**Recomendación** : intenta no alejarte demasiado de 512x512 (a menos que estés usando modelos SDXL, cuya resolución predeterminada es 1024). X 1024). Resoluciones como 512x768 (relación de aspecto 3:4) también funcionan bien.==

## Batch size & Batch count
El tamaño del lote es la cantidad de imágenes que se deben crear por lote. Esto está limitado por su VRAM.

El recuento de lotes es cuántos lotes se deben hacer en total.

Utilice ambas configuraciones para producir más imágenes cada vez que haga clic en el botón Generar.

==`batch size x batch count = total images generated`==

==**Recomendación** : aumente el tamaño del lote hasta alcanzar el máximo (obtendrá un error de símbolo del sistema) y luego aumente el recuento de lotes en consecuencia, de modo que : 
`desired number of images = batch size x batch count`

## CFG Scale
La escala CFG es cuánto debe cumplir la generación con el mensaje. 0 significa ignorar completamente el mensaje y 30 significa cumplir EXTREMADAMENTE estricto con el mensaje.

![[Pasted image 20230924135754.png]]

**Recomendación** : el valor predeterminado de 7 funciona bien en la mayoría de los casos. Puedes experimentar dentro del rango 4-11.

## Saving Your Prompt & Settings

Al comienzo de esta guía, copiamos y pegamos un bloque de texto y usamos AUTOMATIC1111 para convertirlo en configuraciones e indicaciones.

Ahora ¿cómo hacemos lo contrario?

Una vez que hayamos creado el mensaje y la configuración perfectos, ¿cómo podemos reutilizarlos la próxima vez?

**Opción 1** : Cada vez que generas una imagen, este bloque de texto se genera debajo de tu imagen. Cópielo en su procesador de textos favorito y aplíquelo de la misma manera que antes, pegándolo en el campo Mensaje y haciendo clic en el botón de flecha azul debajo de Generar.

![[Pasted image 20230924140521.png]]

**Opción 2** : instalar la extensión [stable-diffusion-webui-state](https://github.com/ilian6806/stable-diffusion-webui-state) . Esto preservará su configuración entre recargas.

## Conclusión

¡Y esas son las configuraciones básicas de Stable Diffusion! Espero que esta guía te haya sido útil. Esto debe leerse como complemento de la [guía de indicaciones](https://aituts.com/stable-diffusion-prompts/) para ayudarle a sentar las bases para generaciones más grandes y mejores.


___
%%
Vínculos:
[[000-Menú Stable Diffusion XL 📃|Menú Stable diffusion XL]]

tags:
#pagstable_diffusion_xl #stable_diffusion_xl #stable_diffusion 
%%