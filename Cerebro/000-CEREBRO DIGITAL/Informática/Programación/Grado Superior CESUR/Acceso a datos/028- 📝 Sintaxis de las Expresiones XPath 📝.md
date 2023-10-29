---
ID: 28
nombre: Sintaxis de las Expresiones XPath
tags:
  - pagacceso_a_datos
---
___
![[d pEWjvLDE.svg]]

### 🎯 Objetivo de las Expresiones XPath 🎯

Una expresión XPath es esencialmente una cadena de texto que actúa como un mapa de ruta para navegar por el árbol de un documento XML. El propósito es encontrar nodos que coincidan con el patrón definido en la expresión.

### 📜 Requisitos para la Evaluación 📜

Para que una expresión XPath sea evaluada, el documento XML debe estar bien formado. El resultado de la evaluación será un conjunto de nodos que coincidan con la expresión.

### 🛠️ Tipos de Sintaxis 🛠️

Las expresiones XPath pueden adoptar dos formas:

1. **Sintaxis Abreviada**: Más compacta y fácil de leer.
2. **Sintaxis Completa**: Ofrece más opciones pero es más extensa.

### 🧭 Pasos de Búsqueda en las Expresiones 🧭

Una expresión XPath se descompone en pasos de búsqueda, y cada paso puede dividirse en tres componentes:

1. **Eje**: Selecciona nodos de elementos o atributos basados en sus nombres.
2. **Predicado**: Restringe la selección del eje para que los nodos cumplan ciertas condiciones.
3. **Selección de Nodos**: De los nodos filtrados por el eje y el predicado, selecciona los elementos, el texto que contienen, o ambos.

### 📖 Ejemplos de Sintaxis Abreviada 📖


```xml
<?xml version="1.0" encoding="UTF-8"?>
<biblioteca>
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
</biblioteca>
```


En este documento XML, una expresión XPath de sintaxis abreviada podría ser algo como `/biblioteca/libro/titulo`, que seleccionaría todos los títulos de los libros en la biblioteca.

### 📌 Notas Adicionales 📌

* Las expresiones XPath son sensibles a mayúsculas y minúsculas.
* Los nodos seleccionados son devueltos en el orden en que aparecen en el documento.

Con esta estructura, se espera que las expresiones XPath sean más accesibles y fáciles de entender, permitiendo una navegación eficiente a través de los documentos XML.

___
%%
tags: #java  #pagacceso_a_datos  #XPath #ExpresionesXPath #Objetivo #RequisitosEvaluación #TiposSintaxis #SintaxisAbreviada #SintaxisCompleta #PasosBúsqueda #Eje #Predicado #SelecciónNodos #Ejemplos #XML #NotasAdicionales
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%