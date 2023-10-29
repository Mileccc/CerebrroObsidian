---
ID: 30
nombre: Predicado (predicate)
tags:
  - pagacceso_a_datos
---
___
### Predicado (en inglés, predicate)

El predicado se escribe entre corchetes, a continuación del eje. Si el eje ha seleccionado unos nodos, el predicado permite restringir esa selección a los que cumplan determinadas condiciones.

- **[@atributo]**: selecciona los elementos que tienen el atributo

```
//autor**[@fechaNacimiento]**
```
$$Resultado$$
```xml
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor> 
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
```

___
___

**[número]**: si hay varios resultados selecciona uno de ellos por número de orden; **last()** selecciona el último de ellos

```
//libro**[1]**
```
$$Resultado$$
```xml
<libro>
  <titulo>La vida está en otra parte</titulo>
  <autor>Milan Kundera</autor>
  <fechaPublicacion año="1973"/>
</libro>
```

___
___


```
//libro**[last()]**
```
$$Resultado$$
```xml
<libro>
  <titulo>Conversación en la catedral</titulo>
  <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
  <fechaPublicacion año="1969"/>
</libro>
```

___
___


```
//libro**[last()-1]**
```
$$Resultado$$
```xml
<libro>
  <titulo>Pantaleón y las visitadoras</titulo>
  <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
  <fechaPublicacion año="1973"/>
</libro>
```

___
___

**[condicion]**: selecciona los nodos que cumplen la condición.

Los predicados permiten definir condiciones sobre los valores de los atributos. En las condiciones se pueden utilizar los operadores siguientes:

- operadores lógicos: and, or, not()
- operadores aritméticos: +, -, \*, div, mod
- operadores de comparación: =, !=, <, >, <=, >=

Las comparaciones se pueden hacer entre valores de nodos y atributos o con cadenas de texto o numéricas. Las cadenas de texto deben escribirse entre comillas simples o dobles. En el caso de las cadenas numéricas, las comillas son optativas.

- La condición puede utilizar el valor de un atributo (utilizando @) o el texto que contiene el elemento.  
    En los ejemplos siguientes se obtienen respectivamente los elementos \<fechaPublicacion> cuyo atributo año es posterior/mayor a 1970 y los elementos \<libro> cuyo subelemento \<autor> tiene como contenido "Mario Vargas Llosa":


___


```
//fechaPublicacion**[@año>1970]**
```
$$Resultado$$
```xml
<fechaPublicacion año="1973"/>
<fechaPublicacion año="1973"/>
```

___
___


```
//libro**[autor="Mario Vargas Llosa"]**
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

Para hacer referencia al propio valor del elemento seleccionado se utiliza el punto (.).

```
//@año**[.>1970]**
```
$$Resultado$$
```xml
 año="1973"
 año="1973"
```

___
___


```
//autor**[.="Mario Vargas Llosa"]**
```
$$Resultado$$
```xml
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
<autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
```

___
___

- Un predicado puede contener condiciones compuestas.  
	En los ejemplos siguientes se seleccionan, respectivamente , los libros escritos por Mario Vargas Llosa **y** publicados en 1973 (primer ejemplo) y los libros escritos por Mario Vargas Llosa **o** publicados en 1973 (segundo ejemplo):

```
//libro[autor="Mario Vargas Llosa" **and** fechaPublicacion/@año="1973"]
```
$$Resultado$$
```xml
<libro>
  <titulo>Pantaleón y las visitadoras</titulo>
  <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
  <fechaPublicacion año="1973"/>
</libro>
```

___
___


```
//libro[autor="Mario Vargas Llosa" **or** fechaPublicacion/@año="1973"]
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

- Se pueden escribir varios predicados seguidos, cada uno de los cuales restringe los resultados del anterior, como si estuvieran encadenados por la operación lógica and.  
En el ejemplo siguiente se seleccionan los libros escritos por Mario Vargas Llosa y publicados en 1973:

```
//libro[autor="Mario Vargas Llosa"][fechaPublicacion/@año="1973"]
```
$$Resultado$$
```xml
<libro>
  <titulo>Pantaleón y las visitadoras</titulo>
  <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
  <fechaPublicacion año="1973"/>
</libro>
```


___
%%
tags: #java  #pagacceso_a_datos  #Predicado #Corchetes #Atributo #Número #Last #Condición #OperadoresLógicos #OperadoresAritméticos #OperadoresDeComparación #CondicionesCompuestas #Encadenamiento #Resultado #XML #XPath #fechaNacimiento #año #titulo #autor #Ejemplos
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%