---
ID: 34
nombre: Layouts
tags:
  - pagdesarrollo_de_interfaces
---
___
## 🌟 Introducción a Layouts en JavaFX 

![](https://www.youtube.com/watch?v=ZqFSvySxVBM&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=214&ab_channel=Aulaenlanube)

### 📦 ¿Qué son los Layouts en JavaFX?

Los Layouts en JavaFX actúan como contenedores que organizan un conjunto de componentes de la interfaz de usuario en un diseño particular. Estos contenedores determinan la forma en que los elementos se disponen en la ventana de la aplicación. 

#### 🔄 Comparación con Java Swing
Al igual que en Java Swing, JavaFX ofrece una serie de layouts prediseñados para facilitar la organización de componentes. 

### 🖼️ Organización de Componentes
Puedes colocar múltiples botones o cualquier otro componente de la interfaz de usuario de la siguiente manera:

- Uno al lado del otro (*Horizontal*)
- Uno debajo del otro (*Vertical*)
- En una cuadrícula (*Grid*)
### 🎭 Combinación de Diferentes Layouts

Es común enfrentar escenarios donde necesitamos más de un tipo de layout para diseñar interfaces de usuario complejas. En estos casos, podemos incrustar diferentes tipos de layouts dentro de un "layout principal".

___
## 🌟 JavaFX Layouts: Explorando los Tipos de Contenedores 

### 📦 Comprendiendo la Clase Base: `Pane`

La clase `Pane` en JavaFX es el punto de partida para todos los demás layouts y representa el contenedor más básico y flexible. Esta clase no impone ningún esquema de diseño en particular y permite el posicionamiento manual de los nodos.

#### 🌱 Jerarquía de Clases

- **Clase `Pane`**: Raíz de todos los layouts
  - `StackPane`
  - `HBox`
  - `VBox`
  - ... y más

### 🗂️ Tipos de Layouts y sus Características

A continuación, exploramos diferentes tipos de layouts heredados de la clase `Pane`:

#### 📚 `StackPane`

- **Funcionalidad**: Coloca los nodos en una pila, uno encima del otro.
  
#### 📊 `VBox`

- **Funcionalidad**: Alinea los nodos verticalmente, uno debajo del otro.

#### ↔️ `HBox`

- **Funcionalidad**: Alinea los nodos horizontalmente, uno al lado del otro.

#### 📝 `GridPane`

- **Funcionalidad**: Organiza los nodos en una cuadrícula bidimensional con filas y columnas.
- **Uso típico**: Cuando se necesita una organización en forma de tabla.

#### 🌐 `BorderPane`

- **Funcionalidad**: Divide el área en cinco regiones: arriba, abajo, izquierda, derecha y centro.
- **Similitud**: Funciona de manera similar a su contraparte en Java Swing.

#### 🌊 `FlowPane`

- **Funcionalidad**: Coloca los elementos en una fila o columna y los traslada a la siguiente fila al llegar al borde del contenedor.
- **Comportamiento**: Los elementos se reorganizan al escalar la ventana.

#### 🎲 `TilePane`

- **Funcionalidad**: Posiciona los nodos en una cuadrícula con dimensiones uniformes.
- **Comparación con `GridPane`**: Menos control sobre las dimensiones individuales de las filas y columnas.

#### 📌 `AnchorPane`

- **Funcionalidad**: Permite anclar nodos a los bordes del layout.
- **Uso típico**: Útil para diseños adaptables al cambio de tamaño de la ventana.

### 🎯 Ejemplos de Código

Ejemplo de un `GridPane` para colocar botones:

```java
GridPane grid = new GridPane();
Button btn1 = new Button("Button 1");
Button btn2 = new Button("Button 2");
grid.add(btn1, 0, 0);
grid.add(btn2, 1, 0);
```

Ejemplo de un `VBox` para alinear elementos verticalmente:

```java
VBox vbox = new VBox();
Button btn1 = new Button("Button 1");
Button btn2 = new Button("Button 2");
vbox.getChildren().addAll(btn1, btn2);
```

### 🛠️ Herramientas para Diseños Complejos

Para diseños más complejos, es común utilizar un `BorderPane` como contenedor principal y añadir otros tipos de layouts en sus diferentes regiones.

#### 🏗️ Diseño Anidado

- Utilizar `BorderPane` como layout principal.
- Añadir diferentes tipos de layouts en las regiones del `BorderPane`.

___
## 🎨 JavaFX: Combinando Diferentes Tipos de Layouts en un Ejemplo Práctico

### 🎯 Contexto: Diseñando una Interfaz Compleja

En aplicaciones más avanzadas, es raro que se utilice un único tipo de layout para toda la interfaz. Generalmente, se combina una variedad de layouts para lograr una disposición más compleja y funcional. 

### 📝 Escenario del Ejemplo

Imaginemos que queremos diseñar una ventana con una barra de botones en la parte superior y un área principal debajo de ella. Para este diseño, se planea usar:

1. Un `VBox` como contenedor principal
2. Un `HBox` para la barra de botones en la parte superior
3. Un `FlowPane` para el área principal debajo de la barra de botones

### 💡 Implementación Paso a Paso

#### 👉 Creación de la Barra de Botones usando `HBox`

1. **Crear Botones**: Crear tres botones con identificadores `btn1`, `btn2` y `btn3`.
2. **Inicializar `HBox`**: Crear un contenedor de tipo `HBox`.
3. **Añadir Botones al `HBox`**: Incluir los tres botones en este contenedor.

```java
Button btn1 = new Button("Button 1");
Button btn2 = new Button("Button 2");
Button btn3 = new Button("Button 3");
HBox hbox = new HBox();
hbox.getChildren().addAll(btn1, btn2, btn3);
```

#### 👉 Creación del Área Principal usando `FlowPane`

1. **Crear Etiqueta**: Crear una etiqueta con el texto "Etiqueta".
2. **Inicializar `FlowPane`**: Crear un contenedor de tipo `FlowPane`.
3. **Añadir Etiqueta al `FlowPane`**: Incluir la etiqueta en este contenedor.

```java
Label label = new Label("Etiqueta");
FlowPane flowPane = new FlowPane();
flowPane.getChildren().add(label);
```

#### 👉 Integración en el `VBox` Principal

1. **Inicializar `VBox`**: Crear el contenedor principal de tipo `VBox`.
2. **Agregar Contenedores**: Añadir el `HBox` y el `FlowPane` como hijos del `VBox`.

```java
VBox vbox = new VBox();
vbox.getChildren().addAll(hbox, flowPane);
```

#### 👉 Creación de la Escena

Finalmente, crear una escena especificando el contenedor principal, que en este caso es el `VBox`.

```java
Scene scene = new Scene(vbox);
```

### 🎭 Resultados

- El `HBox` con los botones aparecerá en la parte superior de la ventana.
- El `FlowPane` con la etiqueta se ubicará debajo del `HBox`, conformando así el área principal de la ventana.

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.layout.FlowPane;
import javafx.scene.layout.HBox;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class CombinedLayoutsExample extends Application {
    
    @Override
    public void start(Stage primaryStage) {
        
        // Crear los botones
        Button btn1 = new Button("Button 1");
        Button btn2 = new Button("Button 2");
        Button btn3 = new Button("Button 3");
        
        // Inicializar HBox y añadir los botones
        HBox hbox = new HBox();
        hbox.getChildren().addAll(btn1, btn2, btn3);
        
        // Crear una etiqueta
        Label label = new Label("Etiqueta");
        
        // Inicializar FlowPane y añadir la etiqueta
        FlowPane flowPane = new FlowPane();
        flowPane.getChildren().add(label);
        
        // Inicializar VBox y añadir HBox y FlowPane como hijos
        VBox vbox = new VBox();
        vbox.getChildren().addAll(hbox, flowPane);
        
        // Crear la escena y especificar el VBox como el contenedor principal
        Scene scene = new Scene(vbox, 400, 300);
        
        // Configuración del Stage
        primaryStage.setTitle("JavaFX Combined Layouts Example");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}

```

En resumen, mediante la combinación de `VBox`, `HBox` y `FlowPane`, se ha conseguido una disposición de elementos más rica y adaptable a diferentes necesidades.

___
## Otro ejemplo Complejo
```java
package com.aula.layouts;

import javafx.application.Application;
import javafx.geometry.Insets;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.scene.layout.BorderPane;
import javafx.scene.layout.HBox;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

/**
 * JavaFX App
 */
public class App extends Application {

    @Override
    public void start(Stage ventanaPrincipal) {

        //botones
        Button btn1 = new Button("Insertar");
        Button btn2 = new Button("Modificar");
        Button btn3 = new Button("Listar");
        Button btn4 = new Button("Borrar");
        Button btn5 = new Button("Reiniciar");

        //hbox para la parte superior
        HBox hbox1 = new HBox(10);
        hbox1.getChildren().addAll(btn1, btn2, btn3);
        hbox1.setAlignment(Pos.CENTER);

        //vbox con etiqueta e imagen para la parte central
        Label etiqueta = new Label("Esto es una etiqueta dentro de un Vbox");
        ImageView imagen = new ImageView(new Image(getClass().getResourceAsStream("/JavaFXLogo.png")));
        VBox vbox = new VBox(10);
        vbox.getChildren().addAll(etiqueta, imagen);
        vbox.setAlignment(Pos.CENTER);
        
        //hbox para la parte inferior
        HBox hbox2 = new HBox(10);
        hbox2.getChildren().addAll(btn4, btn5);
        hbox2.setAlignment(Pos.CENTER);
        
        //BorderPane con los 3 contenedores
        BorderPane borderPane = new BorderPane();
        borderPane.setTop(hbox1);
        borderPane.setCenter(vbox);
        borderPane.setBottom(hbox2);
        borderPane.setPadding(new Insets(20, 20, 20, 20));

        //creamos la escena y mostramos
        Scene scene = new Scene(borderPane, 600, 400);
        ventanaPrincipal.setScene(scene);
        ventanaPrincipal.setTitle("Ejemplos Layouts");
        ventanaPrincipal.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```

___
%%
tags: #pagdesarrollo_de_interfaces #Layouts #JavaFX #Comparación #JavaSwing #Organización #Componentes #Combinación #ClaseBase #Pane #Jerarquía #Tipos #Características #StackPane #VBox #HBox #GridPane #BorderPane #FlowPane #TilePane #AnchorPane #Ejemplos #Código #Herramientas #DiseñoAnidado #Contexto #Escenario #Implementación #Resultados
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%