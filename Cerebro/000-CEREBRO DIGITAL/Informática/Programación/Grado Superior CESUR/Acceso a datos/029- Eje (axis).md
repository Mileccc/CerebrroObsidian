---
ID: 29
nombre: Eje (axis)
tags:
  - pagacceso_a_datos
---
___
### Eje (en inglés, axis)

El eje nos permite seleccionar un subconjunto de nodos del documento y corresponde a recorridos en el árbol del documento. Los nodos elemento se indican mediante el nombre del elemento. Los nodos atributo se indican mediante @ y el nombre del atributo.

- **/**: si está al principio de la expresión, indica el nodo raíz, si no, indica "hijo". Debe ir seguida del nombre de un elemento.


```path
/biblioteca/libro/autor
```
$$Regresa$$
```xml
<autor>Milan Kundera</autor>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
```
___
___

```
/autor
```
$$Regresa$$
```xml
No devuelve nada porque <autor> no es hijo del nodo raíz.
```
___
___

```
/biblioteca/autor
```
$$Regresa$$
```xml
No devuelve nada porque <autor> no es hijo de <biblioteca>.
```
___
___

```
/biblioteca/libro/autor/@fechaNacimiento
```
$$Regresa$$
```xml
 fechaNacimiento="28/03/1936"
 fechaNacimiento="28/03/1936"
```
___
___


```
/biblioteca/libro/@fechaNacimiento
```
$$Regresa$$
```xml
No devuelve nada porque <libro> no tiene el atributo fechaNacimiento.
```
___
___


- **Nota**: En XPath 1.0 no se puede seleccionar únicamente el valor del atributo, sino que se obtienen respuestas del tipo nombreDelAtributo=ValorDelAtributo
    
- **/****/**: indica "descendiente" (hijos, hijos de hijos, etc.).


```
/biblioteca//autor
```
$$Regresa$$
```xml
<autor>Milan Kundera</autor>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
```
___
___


```
//autor
```
$$Regresa$$
```xml
<autor>Milan Kundera</autor>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
```
___
___


```
//autor//libro
```
$$Regresa$$
```xml
No devuelve nada porque <libro> no es descendiente de <autor>.
```
___
___


```
//@año
```
$$Regresa$$
```xml
año="1973"
año="1973"
año="1969"
```
___
___

**/..**: indica el elemento padre.

**Nota**: En el resultado de los ejemplos siguientes se obtienen únicamente los nodos que tienen el atributo fechaNacimiento.


```
/biblioteca/libro/autor/@fechaNacimiento/..
```
$$Regresa$$
```xml
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
```
___
___

```
//@fechaNacimiento/../..
```
$$Regresa$$
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


```
//autor|//titulo
```
$$Regresa$$
```xml
<titulo>La vida está en otra parte</titulo>
<autor>Milan Kundera</autor>
<titulo>Pantaleón y las visitadoras</titulo>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
<titulo>Conversación en la catedral</titulo>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
```
___
___


```
//autor|//titulo|//@año
```
$$Regresa$$
```xml
<titulo>La vida está en otra parte</titulo>
<autor>Milan Kundera</autor>
 año="1973"
<titulo>Pantaleón y las visitadoras</titulo>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
 año="1973"
<titulo>Conversación en la catedral</titulo>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
 año="1969"
```



___
%%
tags: #java  #pagacceso_a_datos  #XPath #Eje #Nodos #Atributos #NodoRaíz #Descendiente #ElementoPadre #Sintaxis #XML #fechaNacimiento #año #titulo #autor #Ejemplos #Nota
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%