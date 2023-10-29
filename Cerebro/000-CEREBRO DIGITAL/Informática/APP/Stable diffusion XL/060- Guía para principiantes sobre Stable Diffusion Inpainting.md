---
ID: 60
-nombre: Guía para principiantes sobre Stable Diffusion Inpainting
"-tags:":
---
___
# Guía para principiantes sobre Stable Diffusion Inpainting
Inpainting es una parte esencial de cualquier flujo de trabajo de Stable Diffusion.

Permite corregir los pequeños defectos "pintando" sobre ellos y regenerando esa parte.

Tiene 2 usos principales:

1. Arreglando partes defectuosas de la imagen.
2. Modifique una imagen según sus requisitos exactos.

Al final de esta guía, podrá pasar de esto a esto:

![[Pasted image 20230924175342.png]]

Esta es la Parte 6 de la serie Difusión estable para principiantes:

## Requisitos
Deberías haber descargado AUTOMATIC1111. De lo contrario, utilice las siguientes guías de descarga:

- [Instalación de GPU NVIDIA](https://aituts.com/stable-diffusion-on-windows-automatic1111/)
- [Instalación de GPU AMD](https://aituts.com/stable-diffusion-amd/)
- [instalación mac](https://aituts.com/stable-diffusion-mac-m1/)

## Empezando
Genere su imagen como lo haría normalmente con cualquier [modelo](https://aituts.com/models/) y prompt.

![[Pasted image 20230924175437.png]]

**Modelo:** Dreamshaper

**Prompt:**
```
masterpiece, 1girl, medieval armor, waving to camera
```

Esta es una buena imagen para usar en la pintura porque las manos parecen fáciles de arreglar. La frente del personaje también es bastante grande, así que la arreglaré.

Clickea en el `Send to inpaint` acceso directo debajo de su imagen (esto envía la imagen al `Inpaint`  subpestaña debajo del `img2img` pestaña.

## Painting the Mask
Notarás muchas configuraciones en la pestaña Inpaint. Llegaremos a eso en un momento.

![[Pasted image 20230924180020.png]]


Por ahora, sólo deseas pintar sobre las partes que deseas regenerar. Esto se llama _máscara_ . Me gusta dejar un gran margen en mi área enmascarada, para que también se regenere un poco del contexto circundante.

![[Pasted image 20230924180031.png]]

## Prompting for Inpainting
Esto es muy confuso: ingresas un nuevo prompt para pintar en el mismo lugar donde escribes el prompt.

Digo confuso porque parece el mismo cuadro de entrada, pero verás que son entradas diferentes en pestañas diferentes.

Necesitará un mensaje especial que se centre en los elementos de la imagen que desea cambiar.

En el prompt negativo, estoy usando una [textual inversion (embedding)](https://aituts.com/textual-inversion/) . Esto no es necesario pero sí muy recomendable.

![[Pasted image 20230924180244.png]]

Aquí hay algunas sugerencias para arreglar partes específicas de la imagen:


![[Pasted image 20230924180455.png]]

Si está pintando algo más, por ejemplo, un peatón caminando en el fondo, simplemente describa eso en su mensaje.

Después de 2 o 3 tiradas repetidas, obtenemos un resultado con el que estamos satisfechos:

![[Pasted image 20230924182609.png]]

A continuación repetiré el mismo proceso con la frente. Guarde la nueva imagen y presione `X`en la imagen antigua.

![[Pasted image 20230924182629.png]]

Sube la nueva imagen en el cuadro que aparece:

![[Pasted image 20230924182647.png]]

Luego enmascare y avise. Aquí mi mensaje es simplemente " `beautiful bangs hair`".

![[Pasted image 20230924182709.png]]

## Inpainting Settings

Aquí hay un resumen de las configuraciones y cuáles es posible que desee cambiar:

**Just resize:** cambie el tamaño a una nueva resolución.
**Crop and resize:** cambie el tamaño para que la imagen se llene en su totalidad con la nueva resolución.
**Resize and fill**:cambie el tamaño para que toda la imagen anterior quepa dentro de la nueva. Llena cualquier espacio faltante con colores.
### Mask blur
**Inpaint masked:** pinta sobre la parte que pintaste de negro.
**Inpaint not masked:** pinta todo, _no_ la parte que estás pintando de negro

### Mask content
**Fill**: Inicializa la generación con los colores de la imagen.
**Original**:Inicializar la generación con lo que había antes.
**Latent noise** or **Lantent nothing**: inicializa la generación sin nada.

### Inpaint area
**Whole picture:** contexto de la imagen completa utilizada. Deberías usar este
**Only masked:** Sólo se utiliza el área enmascarada

### Configuraciones estándar
También notarás la configuración estándar de generación de Stable Diffusion debajo de la configuración de pintura.

`Sampling Steps`: configúrelo en lo que le proporcione buenos resultados.

`Batch count`: probablemente la IA necesitará algunos intentos para crear lo que usted desea, así que ¿por qué no acelerar el proceso generando varias imágenes de una sola vez?

`CFG Scale`: qué tan estrechamente se adhiere la IA a su indicación. Establezca lo que haya funcionado mejor para usted.

`Denoising strength`: determina el poco respeto que debe tener el algoritmo por el contenido de la imagen. En 0, nada cambiará y en 1 obtendrás una imagen no relacionada. Comience en 0.3 y avance desde allí.

`Height`& `Width`: establezca las dimensiones de su imagen.





















___
%%
Vínculos:
[[000-Menú Stable Diffusion XL 📃|Menú Stable diffusion XL]]

tags:
#pagstable_diffusion_xl #stable_diffusion_xl #stable_diffusion 
%%