---
ID: 32
nombre: Pasos de búsqueda consecutivos
tags:
  - pagacceso_a_datos
---
___
### Pasos de búsqueda consecutivos

Una expresión XPath puede contener varios pasos de búsqueda consecutivos. Cada uno incluirá su eje (y en su caso, su predicado) y el último paso de búsqueda incluirá en su caso una selección de nodos. Cada paso de búsqueda trabaja a partir de los nodos seleccionados por el paso de búsqueda anterior.

En el ejemplo siguiente se obtienen los títulos de los libros publicados después de 1970, mediante dos pasos de búsqueda:

- en el **primer paso** (//fechaPublicacion[@año>1970]) se seleccionan los elementos \<fechaPublicacion> cuyo atributo año es superior a 1970.
- en el **segundo paso** (/../titulo), se seleccionan primero los elementos padre (/..) de los \<fechaPublicacion> seleccionados en el primer paso de búsqueda (es decir, elementos \<libro>) y a continuación sus subelementos \<titulo>.

```
//fechaPublicacion[@año>1970]/../titulo
```
$$Resultado$$
```xml
<titulo>La vida está en otra parte</titulo>
<titulo>Pantaleón y las visitadoras</titulo>
```

___
___

Un determinado resultado se puede obtener mediante un sólo paso de búsqueda o mediante varios pasos.

- En los ejemplos siguientes se obtienen los libros escritos por Mario Vargas Llosa de dos formas distintas:
    - mediante un sólo paso de búsqueda. Se seleccionan los elementos \<libro> cuyo subelemento \<autor> tiene como contenido la cadena "Mario Vargas Llosa".

```
//libro[autor="Mario Vargas Llosa"]
```
$$Resultado$$
```xml
<libro>
  <titulo>Pantaleón y las visitadoras</titulo>
  <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
  <fechaPublicacion año="1973"/>
</libro>
<libro>
  <titulo>Conversación en la catedral</titulo>
  <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
  <fechaPublicacion año="1969"/>
</libro>
```

___
___

mediante dos pasos de búsqueda. En el primer paso se seleccionan los elementos \<autor> cuyo contenido es la cadena "Mario Vargas Llosa". En el segundo paso de búsqueda se seleccionan los elementos padre (es decir, los elementos \<libro>).

```
//autor[.="Mario Vargas Llosa"]/..
```
$$Resultado$$
```xml
<libro>
  <titulo>Pantaleón y las visitadoras</titulo>
  <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
  <fechaPublicacion año="1973"/>
</libro>
<libro>
  <titulo>Conversación en la catedral</titulo>
  <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
  <fechaPublicacion año="1969"/>
</libro>
```

___
___

- En los ejemplos siguientes se obtiene el autor que ha publicado libros en 1969 de varias formas distintas:

```
//@año[.=1969]/../../autor
```
$$Resultado$$
```xml
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
```

___
___


```
//libro[fechaPublicacion/@año=1969]/autor
```
$$Resultado$$
```xml
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
```

___
___


```
//fechaPublicacion[@año=1969]/../autor
```
$$Resultado$$
```xml
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
```

___
___


```
//autor[../fechaPublicacion/@año=1969]
```
$$Resultado$$
```xml
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
```


___
%%
tags: #java  #pagacceso_a_datos  #PasosDeBúsqueda #Consecutivos #XPath #Eje #Predicado #SelecciónDeNodos #Resultado #XML #fechaPublicacion #año #titulo #libro #autor #MarioVargasLlosa #Ejemplos #UnPaso #VariosPasos
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%