---
ID: 50
-nombre: Cómo utilizar Stable Diffusion Embeddings (Textual Inversion) y las mejores
"-tags:":
---
___
# Cómo utilizar Stable Diffusion Embeddings (Textual Inversion) y las mejores
Las Embeddings (también conocidas como inversión textual) son pequeños archivos que contienen conceptos adicionales que puede agregar a su modelo base. Este concepto puede ser: una pose, un estilo artístico, una textura, etc.

Las incrustaciones negativas se entrenan en contenido indeseable: puedes usarlas en tus mensajes negativos para mejorar tus imágenes.

Esta es la parte 5 de la serie Difusión estable para principiantes:

## Usando Embeddings
Los Embeddings son `.pt`o `.bin`archivos.

Descárgalos (enlaces de descarga a continuación) y colócalos en la carpeta `stable-diffusion-webui/embeddings` ( `stable-diffusion-webui`es la ubicación de su [instalación AUTOMATIC1111](https://aituts.com/stable-diffusion-on-windows-automatic1111/) ).

Luego escriba el nombre de la inserción, sin la extensión del archivo, en el mensaje. ¡Eso es todo lo que tienes que hacer!

(Escriba el nombre de la incrustación en el mensaje negativo si está utilizando una incrustación negativa).

Atajo: haga clic en el botón de modelos rosa. En la pestaña `Textual Inversion` , verá cualquier incrustación que haya colocado en su `stable-diffusion-webui/embeddings` carpeta. Haga clic en el botón `Refresh` si no ve su modelo.

Si hace clic en la Embeddings, su nombre aparecerá en su prompt.

Tenga en cuenta que esto insertará los Embeddings en el `prompt`. Si desea el Embeddings en su `negative prompt`tendrás que moverlo manualmente.

![[Pasted image 20230924174627.png]]

## Negative Embeddings
Estas son Embeddings entrenadas en contenido indeseable, que usted coloca en su prompt negativo. No sólo eliminan las cosas malas: a menudo mejoran las imágenes en su conjunto.
### EasyNegative

![[Pasted image 20230924174722.png]]

![[Pasted image 20230924174747.png]]

[Enlace de descarga](https://civitai.com/models/71961/fast-negative-embedding-fastnegativev2)

Embedding negativo que mejora la calidad, detalles y colores de las imágenes. Creado para modelos de anime pero funciona bien para la mayoría de los modelos.

### Badhand

![[Pasted image 20230924174844.png]]
[Enlace de descarga](https://civitai.com/models/16993)

Embedding negativa entrenada en manos malas: mejorará en gran medida la calidad de la mano y reducirá las mutaciones.

### Fast Negative
![[Pasted image 20230924174919.png]]

[Enlace de descarga](https://civitai.com/models/71961)
El Embedding negativo entrenado en una variedad de imágenes incluye malas manos.

### Deep Negative

[Enlace de descarga](https://civitai.com/models/71961/fast-negative-embedding-fastnegativev2)

Embedding negativo entrenado en "imágenes repugnantes": cosas desagradables como mala anatomía, malas combinaciones de colores, imágenes al revés.

Excelente para mejorar la anatomía y la calidad general.
## Regular Embeddings
### Pure Eros Face

![[Pasted image 20230924175121.png]]

[Enlace de descarga](https://civitai.com/models/71961/fast-negative-embedding-fastnegativev2)

Incrustación de caras estilo ídolo Kpop.



___
%%
Vínculos:
[[000-Menú Stable Diffusion XL 📃|Menú Stable diffusion XL]]

tags:
#pagstable_diffusion_xl #stable_diffusion_xl #stable_diffusion 
%%