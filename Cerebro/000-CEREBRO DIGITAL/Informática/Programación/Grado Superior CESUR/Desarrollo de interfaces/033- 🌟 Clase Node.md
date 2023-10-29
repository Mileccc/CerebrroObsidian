---
ID: 32
nombre: Clase Node
tags:
  - pagdesarrollo_de_interfaces
---
___
## 🌟 Introducción a la Clase Node en JavaFX 

![](https://www.youtube.com/watch?v=3pRevR7Pml4&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=213&ab_channel=Aulaenlanube)

### 📚 Contexto General

JavaFX es una librería para la creación de interfaces gráficas en aplicaciones Java. Uno de los elementos cruciales de esta librería es la clase `Node`. Esta clase actúa como una superclase para todos los elementos que se pueden representar en una escena gráfica, lo que la convierte en un componente esencial para entender cómo funciona JavaFX.

### 🧱 Elementos Heredados de Node

La clase `Node` es la piedra angular desde la que heredan una variedad de componentes que se pueden renderizar en una escena de JavaFX. Estos componentes se dividen principalmente en las siguientes categorías:

1. **Controles de Usuario**: Botones, etiquetas, cajas de texto, etc.
2. **Formas Geométricas**: Rectángulos, círculos, líneas, etc.
3. **Contenedores**: Paneles, ventanas, etc.
4. **Otros Componentes**: ComboBox, tablas, etc.

### 🔍 Métodos Importantes de Node

Es crucial entender que todos los componentes que heredan de `Node` también heredan una serie de métodos fundamentales. Algunos de los métodos más relevantes son:

```java
setScaleX();  // Para cambiar la escala en el eje X
setScaleY();  // Para cambiar la escala en el eje Y
setRotate();  // Para rotar el nodo
```

### 🌲 Jerarquía y Clase Parent

También es vital hablar sobre la clase `Parent`, que es una extensión específica de la clase `Node`. Actúa como un contenedor que agrupa múltiples nodos. Además, se discutirá brevemente la jerarquía de clases de `Node` para tener una comprensión clara de cómo se organizan las subclases.

#### Subclases Importantes 

Las subclases se agrupan principalmente en función de su funcionalidad y características. Algunas de las subclases más comunes que se derivan de `Node` son:

- **UI Controls**: `Button`, `Label`, `TextField`
- **Shapes**: `Circle`, `Rectangle`, `Line`
- **Containers**: `Pane`, `HBox`, `VBox`

___
## 🌠 Detalles sobre la Clase Node 

### 🎯 Objetivo

Entender la clase `Node` en JavaFX es crucial para cualquier desarrollador que quiera trabajar con interfaces gráficas en Java. La `Node` es la superclase de todos los elementos que pueden ser renderizados en una escena de JavaFX. Aquí nos adentraremos en sus características más específicas y en cómo se utilizan.

---

### 🧭 Características Fundamentales de Node

#### 📌 Posición y Tamaño 

La clase `Node` proporciona propiedades para definir la posición y el tamaño de los elementos en una escena. Estas propiedades son heredadas por todas las clases que derivan de `Node`.

- **Posición en el Espacio**: Definida en un espacio tridimensional con coordenadas X, Y y Z.
- **Tamaño**: Determinado por los atributos `width` (ancho) y `height` (alto).

```java
node.setLayoutX(50); // Posición en el eje X
node.setLayoutY(50); // Posición en el eje Y
node.setLayoutZ(50); // Posición en el eje Z
node.setPrefWidth(100); // Ancho
node.setPrefHeight(100); // Alto
```

##### 🤔 ¿Por Qué Solo Dos Dimensiones para el Tamaño?

Aunque se utiliza un sistema de coordenadas tridimensional para la posición, el tamaño se define solo en dos dimensiones (ancho y alto). Esto se debe a que `Node` opera principalmente en un plano 2D.

💡 **Excepción**: Algunas subclases en paquetes específicos permiten definir el tamaño en profundidad (3D) a través del atributo `depth`.

#### 🎨 Estilo y Apariencia

La clase `Node` permite aplicar estilos utilizando JavaFX CSS. Esto incluye cambiar colores, aplicar sombras, desenfoques, etc.

```css
/* Ejemplo de JavaFX CSS */
.button {
  -fx-background-color: blue;
  -fx-text-fill: white;
}
```

#### 📣 Manejo de Eventos

`Node` viene con una API completa para manejar eventos, como clics del ratón y entrada de datos por teclado.

```java
node.setOnMouseClicked(e -> {
  System.out.println("Mouse clicked");
});
```

#### 🔄 Transformaciones

Se pueden aplicar diferentes tipos de transformaciones a los nodos:

- **Traslación**: Mover la posición del nodo.
- **Rotación**: Girar el nodo.
- **Escalado**: Cambiar el tamaño del nodo.

```java
node.setTranslateX(10); // Traslación en X
node.setRotate(45); // Rotación
node.setScaleX(2); // Escalado en X
```

#### 👀 Visibilidad y Accesibilidad

Puede controlar la visibilidad de los nodos y también deshabilitarlos para que no puedan interactuar con ellos.

```java
node.setVisible(false); // Hacer invisible
node.setDisable(true); // Deshabilitar
```

---

### 🌳 Estructura Jerárquica y Clase Parent

Un nodo en JavaFX no solo puede existir de forma aislada, sino que también puede ser parte de una estructura jerárquica, formando lo que se conoce como *gráfico de escena*. Esto se logra a través de la clase `Parent`, que permite que un nodo tenga un nodo padre y varios nodos hijos.

- **Clase Parent**: Especialización de `Node` que actúa como contenedor para otros nodos.

```java
Pane pane = new Pane();
pane.getChildren().add(node1);
pane.getChildren().add(node2);
```

Aquí, el `pane` actúa como el nodo padre y `node1` y `node2` son los nodos hijos. Esta estructura se visualiza como un árbol, lo que facilita la organización y manipulación de elementos en una escena de JavaFX.

___
## 🌟 Clase Node y sus Componentes 🌟

En Java FX, la Clase Node es fundamental, ya que es la superclase de todos los elementos gráficos que se pueden visualizar en una escena. Los componentes que heredan de esta clase son diversos y pueden abarcar desde contenedores hasta controles de usuario y formas geométricas. Sin más preámbulos, exploraremos estos componentes categorizados y detallaremos sus características.

---

### 📦 Contenedores (Layouts)

Los contenedores en Java FX se asemejan en funcionalidad a los vistos en Java Swing y son cruciales para organizar elementos gráficos en la interfaz de usuario. Aquí hay algunas clases de contenedores que heredan de Node:

1. **Pane**: Contenedor base para todos los paneles.
2. **AnchorPane**: Permite anclar nodos a los bordes de la ventana.
3. **HBox y VBox**: Estos son ideales para diseños horizontales y verticales, respectivamente.
4. **GridPane**: Útil para diseños en forma de cuadrícula o tabla.
5. **BorderPane**: Facilita el diseño dividiendo la ventana en áreas específicas (top, bottom, left, right, center).
6. **StackPane**: Apila nodos uno encima del otro.
7. **FlowPane**: Coloca nodos en un flujo, similar a como el texto fluye en un parrafo.
8. **TilePane**: Coloca nodos en una cuadrícula .

---

### 🎛 Controles de Usuario

Los controles de usuario permiten una interacción directa con la aplicación. Estos también heredan de la clase Node. Algunos de los controles más comunes incluyen:

- *Botón*: Para ejecutar acciones.
- *Etiqueta (Label)*: Para mostrar texto estático.
- *Campo de texto*: Para entrada de texto.
- *Checkbox / RadioButton*: Para selecciones múltiples y únicas.
- *ComboBox / ChoiceBox*: Para una lista desplegable de elementos
- *Sliders*: Para seleccionar un valor de un rango.
- *Barras de Progreso / ProgressBar / ProgressIndicator*: Para mostrar el estado de una tarea.
- *TableView / ListView / TreeView*: Para mostrar datos en forma tabular, lista o jerárquica.


---

### 📐 Formas Geométricas

La clase Node también abarca formas geométricas que son útiles para gráficos y diseño visual. Algunas de estas formas son:

- **Circle**: Un Círculo
- **Rectangle**: Un Rectángulo
- **Polygon**: Una figura geométrica con más de tres lados.
- **Line**: Línea recta 
- **Elipse**: Una elipse.
- **Path**: Compuestas por múltiples segmentos de líneas y curvas.

---

### 🌠 Componentes Misceláneos

Finalmente, tenemos una categoría que engloba otros tipos de componentes útiles pero menos convencionales:

- *ImagenView*: Para mostrar imágenes
- *MediaView*: Para mostrar contenido multimedia como videos.
- *WebView*: Para mostrar contenido web.
- *Text*: Para mostrar texto con estilos más avanzados a Label.
- *Canvas*: Para dibujo de bajo nivel.
- *Group*: Un contenedor especial que simplemente agrupa otros nodos sin aplicar un diseño específico.

---
## 🎯 Métodos en la Clase Node 
JavaFX ofrece una abundante cantidad de métodos que son parte de la clase Node. A continuación se detalla una guía enfocada en los métodos más comúnmente utilizados.

### 🌈 Métodos para Posicionamiento y Movimiento

1. **setTranslateX y setTranslateY**
   - **Qué hacen**: Mueven el nodo a lo largo de los ejes X y Y.
   - **Cómo usarlos**: Permiten posicionar el componente en un plano bidimensional.

```java
button.setTranslateX(50);
button.setTranslateY(50);
```

### 🔄 Métodos para Rotación

1. **setRotate**
   - **Qué hacen**: Rota el nodo un número determinado de grados.
   - **Cómo usarlos**: Se invoca sobre una instancia del nodo a rotar.

```java
button.setRotate(45);
```

### 📏 Métodos para Escalado

1. **setScaleX y setScaleY**
   - **Qué hacen**: Cambian el tamaño del nodo tanto en horizontal como en vertical.
   - **Cómo usarlos**: Se invoca con un valor decimal para determinar el factor de escalado.

```java
button.setScaleX(1.5);
```

### 🎭 Métodos para Control de Visibilidad y Accesibilidad

1. **setVisible**
   - **Qué hacen**: Controlan la visibilidad del nodo.
   - **Cómo usarlos**: Se invoca con un valor booleano.

2. **setDisable**
   - **Qué hacen**: Habilitan o deshabilitan el nodo para la interacción del usuario.
   - **Cómo usarlos**: Se invoca con un valor booleano.

```java
button.setVisible(true);
button.setDisable(false);
```

### 📜 Ejemplo Práctico

El siguiente código muestra cómo aplicar varios de estos métodos sobre un botón que es una instancia de la clase `Button`, que hereda de `Node`.

```java
// Dentro del método start
Button button = new Button("Pulsa");
button.setTranslateX(50);
button.setTranslateY(50);
button.setRotate(45);
button.setScaleX(1.5);
// Crear escena
Scene scene = new Scene(button, 500, 500);
stage.setScene(scene);
stage.show();
```

#### 🤔 Consideraciones Adicionales

- Aunque técnicamente es posible utilizar una instancia de `Node` directamente para crear una `Scene`, la práctica recomendada es encapsular el nodo dentro de un contenedor.
- Los contenedores ofrecen más flexibilidad y están diseñados para manejar el diseño de una manera más eficiente.
  
```java
// Es recomendable hacerlo de esta manera
Pane root = new Pane();
root.getChildren().add(button);
Scene scene = new Scene(root, 500, 500);
```

#### 🎬 Finalización

Una vez creada la escena, se establece en la instancia `stage`, que es la ventana principal de la aplicación y luego se muestra.

```java
stage.setScene(scene);
stage.show();
```

___
## 🎯 Clase Parent 

La clase `Parent` en JavaFX es esencial para entender la organización jerárquica y la manipulación de nodos en una interfaz gráfica de usuario. A continuación, se detallan sus características, funcionalidades y particularidades.

### 📦 Parent como Contenedor de Nodos

1. **Definición**
   - `Parent` es una subclase de `Node`.
   - Funciona como un contenedor para otros nodos, permitiendo la creación de estructuras jerárquicas.

2. **Naturaleza Abstracta**
   - La clase `Parent` es abstracta, lo que significa que no puede ser instanciada directamente.
   - En su lugar, se utilizan clases derivadas como `Pane`, `VBox`, `HBox`, etc.

```java
Pane root = new Pane();
VBox vbox = new VBox();
```

### 🌳 Jerarquía de Nodos

1. **Nodos Hijos**
   - Un objeto de una clase que hereda de `Parent` puede contener múltiples nodos hijos.
   - Estos nodos hijos, a su vez, pueden ser contenedores y tener más nodos hijos, permitiendo crear estructuras jerárquicas complejas.

```java
Pane root = new Pane();
Button button1 = new Button("Botón 1");
Button button2 = new Button("Botón 2");
root.getChildren().addAll(button1, button2);
```

### 🔄 Transformaciones y Estilo

1. **Transformaciones**
   - Si se aplica una transformación a un objeto `Parent`, esta afectará a todos los nodos hijos.
   - Por ejemplo, si se rota un `VBox` que contiene botones, todos los botones también rotarán.

2. **Estilo**
   - De manera similar, el estilo aplicado a un objeto `Parent` se propaga a todos los nodos hijos.
   - Ofrece flexibilidad en el diseño y la estética de la interfaz.

```java
// Si rotamos el VBox, los botones dentro también se rotarán
vbox.setRotate(45);
```

### 🚀 Manejo de Eventos

1. **Propagación de Eventos**
   - Un objeto `Parent` puede capturar eventos que se propagan a través de la jerarquía de nodos.
   - Esto permite manejar eventos a un nivel más alto en la estructura, si se requiere.

```java
root.setOnMouseClicked(event -> {
    System.out.println("Evento de clic capturado en el contenedor root");
});
```

Esta exploración de la clase `Parent` en JavaFX debería proporcionar una comprensión más profunda de su papel vital en la creación y manipulación de interfaces gráficas de usuario. Se trata de un componente que no solo aloja otros nodos sino que también afecta su comportamiento y estética, ofreciendo una gran cantidad de posibilidades para el diseño de aplicaciones.

___
## Jerarquía de Clases de Node

![[Pasted image 20231019113730.png]]


___
## Ejemplo Completo uso Clase Node

```java
package com.aula.node;
  
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;
  
  
/**
 * JavaFX App
 */
public class App extends Application {
  
    @Override
    public void start(Stage ventanaPrincipal) {
        Button boton1 = new Button("Botón 1");
        Button boton2 = new Button("Botón 2");
  
        boton1.setTranslateX(50);
        boton1.setTranslateY(50);
  
        boton2.setTranslateX(10);
        boton2.setTranslateY(50);
  
        VBox vbox = new VBox();
        vbox.getChildren().addAll(boton1,boton2);
        boton1.setRotate(45);
        vbox.setRotate(45);
        vbox.setTranslateY(100);
  
        Scene scene = new Scene(vbox, 500, 500);
        ventanaPrincipal.setTitle("Ejemplo Node");
        ventanaPrincipal.setScene(scene);
        ventanaPrincipal.show();
  
    }
  
    public static void main(String[] args) {
        launch();
    }
}
```


___
%%
tags: #pagdesarrollo_de_interfaces #HTML #CSS #JavaScript #Python #Java #Cplusplus #SQL #PHP #Ruby #Swift #Kotlin #Go #Rust #TypeScript #Nodejs #React #Angular #Vue #Django #Flask #Spring #Hibernate #MongoDB #MySQL #PostgreSQL #AWS #Azure #DevOps #Docker #Kubernetes #Nodes
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%