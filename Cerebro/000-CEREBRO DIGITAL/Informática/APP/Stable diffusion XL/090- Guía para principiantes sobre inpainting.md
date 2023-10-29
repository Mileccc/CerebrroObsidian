---
ID: 
-nombre: Guía para principiantes sobre inpainting
"-tags:":
---
___
# Guía para principiantes sobre inpainting
No importa qué tan buenos sean su mensaje y modelo, es raro obtener una imagen perfecta de una sola vez.

Inpainting es una forma indispensable de corregir pequeños defectos. En esta publicación, analizaré algunos ejemplos básicos para usar **inpainting** para corregir defectos.

Si eres nuevo en el mundo de las imágenes de IA, quizás quieras leer primero la [guía para principiantes](https://stable-diffusion-art.com/beginners-guide/) .

## Modelo de imagen y GUI

Usaremos Stable Diffusion AI y AUTOMATIC1111 GUI. Consulte mi [guía de inicio rápido](https://andrewongai.gumroad.com/l/stable_diffusion_quick_start) para configurar en el servidor en la nube de Google.

## Configuración básica de pintura

En esta sección, te mostraré paso a paso cómo utilizar inpainting para corregir pequeños defectos.

Usaré una imagen original del [mensaje de Lonely Palace](https://stable-diffusion-art.com/lonely-palace/) :

```
[emma watson: amber heard: 0.5], (long hair:0.5), headLeaf, wearing stola, vast roman palace, large window, medieval renaissance palace, ((large room)), 4k, arstation, intricate, elegant, highly detailed
```
> 
> (La configuración detallada se puede encontrar [aquí](https://stable-diffusion-art.com/lonely-palace/) ).

![[Pasted image 20230924201818.png]]


Es una buena imagen pero me gustaría solucionar los siguientes problemas.

- El rostro parece antinatural.
- Falta el brazo derecho.

### Utilice un modelo para pintar (opcional)

¿Sabe que existe un modelo de Difusión Estable entrenado para pintar? Puedes usarlo si quieres obtener el mejor resultado. Pero normalmente, está bien usar el mismo modelo con el que generaste la imagen para pintar.

Para instalar el [modelo inpainting v1.5](https://huggingface.co/runwayml/stable-diffusion-inpainting) , descargue el [archivo de punto de control](https://huggingface.co/runwayml/stable-diffusion-inpainting/resolve/main/sd-v1-5-inpainting.ckpt) del modelo y colóquelo en la carpeta

```
stable-diffusion-webui/models/Stable-diffusion
```

En AUTOMATIC1111, presione el ícono de actualización al lado del cuadro desplegable de selección de puntos de control en la parte superior izquierda. Seleccionar `sd-v1-5-inpainting.ckpt`para habilitar el modelo.

![[Pasted image 20230924201947.png]]

### Creando una máscara en pintura

En la GUI de AUTOMATIC1111, seleccione la **img2img** pestaña **Inpaint** y seleccione la subpestaña . Sube la imagen al lienzo de pintura.

![[Pasted image 20230924202056.png]]

Pintaremos tanto el brazo derecho como la cara al mismo tiempo. Utilice la herramienta Pincel para crear una **máscara** . Esta es el área donde desea que Stable Diffusion regenere la imagen.


![[Pasted image 20230924202129.png]]

### Configuraciones para pintar

#### Inmediato

Puede **reutilizar el mensaje original** para corregir defectos. Esto es como generar múltiples imágenes pero sólo en un área particular.

#### Tamaño de la imagen

Es necesario ajustar el tamaño de la imagen para que sea el mismo que el de la imagen original. (704 x 512 en este caso).

#### Restauración facial

Si está pintando caras, puede activar **restaurar caras** . También deberá seleccionar y aplicar el **modelo de restauración facial** que se utilizará en la **pestaña Configuración** . **CodeFormer** es bueno.

Tenga en cuenta que esta opción puede generar apariencias poco naturales. También puede generar algo inconsistente con el estilo del modelo.

#### Contenido de la máscara

La siguiente configuración importante es **Contenido de máscara** .

Selecciona **original** si quieres que el resultado se guíe por el color y la forma del contenido original. **Original se utiliza a menudo al pintar caras** porque la forma general y la anatomía estaban bien. Sólo queremos que se vea un poco diferente.

En la mayoría de los casos, utilizará **Original** y cambiará **denoising strength** para lograr diferentes efectos.

Puedes usar **latent noise** o **latent nothing** si quieres regenerar algo completamente diferente del original, por ejemplo, quitar una extremidad u ocultar una mano. Estas opciones inicializan el área enmascarada con algo distinto a la imagen original. Producirá algo completamente diferente.

#### Fuerza de eliminación de ruido

**Denoising strength** controla cuánto cambio realizará en comparación con la imagen original. Nada cambiará cuando lo establezcas en 0. Obtendrás una pintura no relacionada cuando lo establezcas en 1.

0,75 suele ser un buen punto de partida. Disminuya si desea cambiar menos.

#### Batch size

Asegúrate de **generate a few images at a time** para que puedas elegir las mejores. Establece la **semilla** en -1 para que cada imagen sea diferente.
![[Pasted image 20230924202703.png]]

### Resultados de pintura

A continuación se muestran algunas de las imágenes pintadas.

![[Pasted image 20230924202816.png]]

![[Pasted image 20230924202831.png]]

![[Pasted image 20230924202844.png]]


### Una ronda más de pintura

Me gusta el último, pero hay una mano extra debajo del brazo recién pintado. Siga pasos similares para cargar esta imagen y crear una máscara. **Masked content** debe configurarse con **latent noise** para generar algo completamente diferente.

La mano debajo del brazo se retira con la segunda ronda de pintura:

![[Pasted image 20230924202950.png]]

Y esta es mi imagen final.

Una comparación lado a lado

![[Pasted image 20230924203007.png]]

Inpainting es un proceso iterativo. Puedes aplicarlo tantas veces como quieras para refinar una imagen.

Consulte esta [publicación](https://stable-diffusion-art.com/how-to-remove-a-person-with-ai-inpainting/) para ver otro ejemplo más extremo de pintura interna.

Consulte el [tutorial para eliminar extremidades adicionales con pintura interna](https://stable-diffusion-art.com/inpainting-remove-extra-limbs/) .


## Agregar nuevos objetos

A veces quieres agregar algo nuevo a la imagen.

Intentemos agregar un abanico a la imagen.

Primero, cargue la imagen en el lienzo de pintura y cree una máscara alrededor del pecho y el brazo derecho.

Agregue el mensaje "sosteniendo un abanico" al comienzo del mensaje original. El mensaje para pintar es

```
(holding a hand fan: 1.2), [emma watson: amber heard: 0.5], (long hair:0.5), headLeaf, wearing stola, vast roman palace, large window, medieval renaissance palace, ((large room)), 4k, arstation, intricate, elegant, highly detailed
```

Agregar nuevos objetos al mensaje original garantiza la coherencia del estilo. Puede ajustar el [peso de la palabra clave](https://stable-diffusion-art.com/fine-tune-your-ai-images-with-these-simple-prompting-techniques/#Adjust_keyword_strength_using_weight) (1.2 arriba) para que el fan se muestre.

Establecer **contenido enmascarado** como **ruido latente** .

Ajuste **la intensidad de la eliminación de ruido** y **la escala CFG** para ajustar las imágenes pintadas.

Después de un poco de experimentación, nuestra misión está cumplida:

![[Pasted image 20230924203720.png]]

## Explicación de los parámetros de pintura.
### Denoising strength

La intensidad de eliminación de ruido controla el respeto que la imagen final debe rendir al contenido original. Establecerlo en 0 no cambia nada. Al configurar en 1, obtienes una imagen no relacionada.

Establezca un valor bajo si desea un cambio pequeño y un valor alto si desea un cambio grande.

![[Pasted image 20230924204107.png]]


### CFG scale
De manera similar al uso en [texto a imagen](https://stable-diffusion-art.com/know-these-important-parameters-for-stunning-ai-images/#CFG_Scale) , la **Classifier Free Guidance scale** es un parámetro para controlar cuánto debe respetar el modelo su indicación.

1 – Principalmente ignora tu prompt.  
3 – Sea más creativo.  
7 – Un buen equilibrio entre seguir la indicación y libertad.  
15 – Cíñete más al mensaje.  
30 – Sigue estrictamente las indicaciones.

### Masked content
El contenido enmascarado controla cómo se inicializa el área enmascarada.

- **Relleno** : Inicializa con una imagen muy borrosa de la imagen original.
- **Original** : Sin modificar.
- **Ruido latente** : el área enmascarada se inicializa con **relleno** y se agrega ruido aleatorio al espacio latente.
- **Nada latente** : como el ruido latente, excepto que no se agrega ruido al espacio latente.

A continuación se muestra el contenido de la máscara inicial antes de cualquier paso de muestreo. Esto te da una idea de cuáles son.
![[Pasted image 20230924204416.png]]

## Consejos para pintar

Una pintura exitosa requiere paciencia y habilidad. Aquí hay algunos productos para llevar a casa para usar en pintura.

- Un área pequeña a la vez.
- Mantener **el contenido enmascarado** en **Original** y ajustar la intensidad de eliminación de ruido funciona el 90% del tiempo.
- Juega con **contenido enmascarado** para ver cuál funciona mejor.
- Si nada funciona bien en la configuración de AUTOMATIC1111, utilice un software de edición de fotografías como Photoshop o GIMP para pintar el área de interés con la forma y el color aproximado que desee. Sube esa imagen y píntala con contenido original.


___
%%
Vínculos:
[[000-Menú Stable Diffusion XL 📃|Menú Stable diffusion XL]]

tags:
#pagstable_diffusion_xl #stable_diffusion_xl #stable_diffusion 
%%