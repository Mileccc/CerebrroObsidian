---
ID: 27
nombre: XPath
tags:
  - pagacceso_a_datos
---
___
## 🌐 Explorando XPath: Un Viaje a través de los Nodos XML 🌐

![[d JjyqXHqE.svg]]

### 🎯 Propósito de XPath 🎯

XPath es un lenguaje especializado en la selección de nodos dentro de un documento XML. Además, permite calcular valores basados en el contenido de estos nodos. Está respaldado por múltiples versiones aprobadas por el W3C.

### 🌳 La Visión de Árbol en XPath 🌳

#### 📊 Conceptos de Árbol y Grafo 📊

- **Grafo**: Conjunto de objetos, conocidos como nodos o vértices, conectados por enlaces llamados arcos o aristas.

![[Pasted image 20231014171648.png]]

- **Grafo Dirigido**: Un grafo donde los arcos tienen una dirección específica.

![[Pasted image 20231014171719.png]]

- **Nodo Padre e Hijo**: En un grafo dirigido, el nodo de origen es el padre y el nodo de destino es el hijo.

![[Pasted image 20231014171739.png]]

- **Árbol**: Un grafo sin ciclos, donde cualquier par de vértices está conectado por un único camino.
- **Árbol Dirigido**: Un árbol donde las aristas tienen dirección y todos los nodos, excepto uno, tienen un único padre.

#### 🌱 Terminología Específica en XPath 🌱

- **Nodo Raíz**: El único nodo en un árbol dirigido que no tiene un padre.
- **Nodos Hermanos**: Nodos que comparten el mismo nodo padre.

![[Pasted image 20231014171804.png]]

- **Nodos Descendientes**: Todos los nodos accesibles desde un nodo específico.

![[Pasted image 20231014171848.png]]

- **Nodos Ascendientes**: Todos los nodos desde los cuales un nodo específico es accesible.

![[Pasted image 20231014171859.png]]

### 📜 Tipos de Nodos en XPath 📜

Un documento XML se puede representar como un árbol dirigido. En XPath, existen siete tipos de nodos:

1. `Raíz`
2. `Elemento`
3. `Atributo`
4. `Texto`
5. `Comentario`
6. `Instrucción de Procesamiento`
7. `Espacio de Nombres`

> 📌 Nota: La declaración DOCTYPE no se considera un nodo.

#### 📘 Ejemplo de Documento XML 📘


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

### 🎨 Visualización de Nodos 🎨

![[Pasted image 20231014172020.png|1300]]

> 📌 Nota: Los nodos de atributo y texto tienen características especiales. Por ejemplo, no pueden tener descendientes y se consideran más como etiquetas adosadas a los elementos.

Con esta estructura, se espera que el universo de XPath sea más accesible y comprensible, permitiendo una navegación eficiente a través de los intrincados nodos de un documento XML.

___
%%
tags: #java  #pagacceso_a_datos  #XPath #W3C #Árbol #Grafo #GrafoDirigido #NodoPadre #NodoHijo #ÁrbolDirigido #NodoRaíz #NodosHermanos #NodosDescendientes #NodosAscendientes #TiposDeNodos #Raíz #Elemento #Atributo #Texto #Comentario #InstrucciónDeProcesamiento #EspacioDeNombres #XML #Documentación #VisualizaciónDeNodos
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%