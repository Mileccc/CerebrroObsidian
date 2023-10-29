---
ID: 31
nombre: nodos (node test)
tags:
  - pagacceso_a_datos
---
___
### Selección de nodos (en inglés, node test)

La selección de nodos se escribe a continuación del eje y el predicado. Si el eje y el predicado han seleccionado unos nodos, la selección de nodos indica con qué parte de esos nodos nos quedamos.

- **/node()**: selecciona todos los hijos (elementos o texto) del nodo.  
    **//node()**: selecciona todos los descendientes (elementos o texto) del nodo.

```
//libro/node()
```
$$Resultado$$
```xml
<titulo>La vida está en otra parte</titulo>
<autor>Milan Kundera</autor>
<fechaPublicacion año="1973"/>
<titulo>Pantaleón y las visitadoras</titulo>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
<fechaPublicacion año="1973"/>
<titulo>Conversación en la catedral</titulo>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
<fechaPublicacion año="1969"/>
```

___
___

```
//autor/node()
```
$$Resultado$$
```xml
Milan Kundera
Mario Vargas Llosa
Mario Vargas Llosa
```

___
___


```
//libro//node()
```
$$Resultado$$
```xml
<titulo>La vida está en otra parte</titulo>
La vida está en otra parte
<autor>Milan Kundera</autor>
Milan Kundera
<fechaPublicacion año="1973"/>
<titulo>Pantaleón y las visitadoras</titulo>
Pantaleón y las visitadoras
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
Mario Vargas Llosa
<fechaPublicacion año="1973"/>
<titulo>Conversación en la catedral</titulo>
Conversación en la catedral
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
Mario Vargas Llosa
<fechaPublicacion año="1969"/>
```

___
___

- **/text()**: selecciona únicamente el texto contenido en el nodo.  
	**//text()**: selecciona únicamente el texto contenido en el nodo y todos sus descendientes.

```
//autor/text()
```
$$Resultado$$
```xml
Milan Kundera
Mario Vargas Llosa
Mario Vargas Llosa
```

___
___


```
//libro/text()
```
$$Resultado$$
```xml
No devuelve nada porque <libro> no contiene texto.
```

___
___


```
//libro//text()
```
$$Resultado$$
```xml
La vida está en otra parte
Milan Kundera
Pantaleón y las visitadoras
Mario Vargas Llosa
Conversación en la catedral
Mario Vargas Llosa
```

___
___

- **/\***: selecciona todos los hijos (sólo elementos) del nodo.  
**//\***: selecciona todos los descendientes (sólo elementos) del nodo.

```
/biblioteca/*
```
$$Resultado$$
```xml
<libro>
  <titulo>La vida está en otra parte</titulo>
  <autor>Milan Kundera</autor>
  <fechaPublicacion año="1973"/>
</libro>
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


```
//autor/*
```
$$Resultado$$
```xml
No devuelve nada porque <autor> sólo contiene texto.
```

___
___


```
/biblioteca//*
```
$$Resultado$$
```xml
<libro>
  <titulo>La vida está en otra parte</titulo>
  <autor>Milan Kundera</autor>
  <fechaPublicacion año="1973"/>
</libro>
<titulo>La vida está en otra parte</titulo>
<autor>Milan Kundera</autor>
<fechaPublicacion año="1973"/>
<libro>
  <titulo>Pantaleón y las visitadoras</titulo>
  <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
  <fechaPublicacion año="1973"/>
</libro>
<titulo>Pantaleón y las visitadoras</titulo>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
<fechaPublicacion año="1973"/>
<libro>
  <titulo>Conversación en la catedral</titulo>
  <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
  <fechaPublicacion año="1969"/>
</libro>
<titulo>Conversación en la catedral</titulo>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
<fechaPublicacion año="1969"/>
```

___
___

**/@\***: selecciona todos los atributos del nodo.  
**//@\***: selecciona todos los atributos de los descendientes del nodo.

```
//@*
```
$$Resultado$$
```xml
año="1973"
fechaNacimiento="28/03/1936"
año="1973"
fechaNacimiento="28/03/1936"
año="1969"
```

___
___


```
//libro/@*
```
$$Resultado$$
```xml
No devuelve nada porque <libro> no tiene atributos.
```

___
___


```
//autor/@*
```
$$Resultado$$
```xml
 fechaNacimiento="28/03/1936"
 fechaNacimiento="28/03/1936"
```

___
___
- **Nota**: En XPath 1.0 no se puede seleccionar únicamente el valor del atributo, sino que se obtienen respuestas del tipo nombreDelAtributo=ValorDelAtributo 

___
%%
tags: #java  #pagacceso_a_datos  #SelecciónDeNodos #NodeTest #Node #Text #Asterisco #Atributos #Resultado #XML #XPath #Eje #Predicado #fechaNacimiento #año #titulo #autor #Ejemplos #Nota
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%