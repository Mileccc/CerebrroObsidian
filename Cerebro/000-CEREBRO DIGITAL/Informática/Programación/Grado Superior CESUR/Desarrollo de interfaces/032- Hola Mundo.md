---
ID: 32
nombre: Hola Mundo
tags:
  - pagdesarrollo_de_interfaces
---
___
## 🌟 Creando un "Hola Mundo" Personalizado

![](https://www.youtube.com/watch?v=oxqKvOvTn6c&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=213&t=406s&ab_channel=Aulaenlanube)

### 📦 Preparativos Iniciales

Antes de sumergirnos en los ejemplos, es crucial entender que estamos trabajando en el tema 9 del curso de programación. En este tema, nos enfocamos en JavaFX y cómo crear interfaces gráficas de usuario (GUI) en Java.

### 🛠 Herramientas Utilizadas

- **JavaFX**: Biblioteca para crear interfaces gráficas.
- **FXML**: Archivo para el diseño de la interfaz (en el segundo ejemplo).

---

## 🎯 Primer Ejemplo: Sin Uso de FXML

#### 📝 Descripción General

En este primer ejemplo, creamos una aplicación JavaFX que muestra una caja de texto y un botón. Al ingresar un nombre en la caja de texto y hacer clic en el botón, aparece una ventana emergente con un saludo personalizado.

#### 🏗 Estructura del Código

1. **Clase Principal**: `App` que hereda de `Application`.
2. **Método `start`**: Punto de entrada para la aplicación JavaFX.
3. **Método `main`**: Invoca al método `launch` para inicializar JavaFX.

```java
public class App extends Application {
    public void start(Stage ventanaPrincipal) {
        // Código aquí
    }
    public static void main(String[] args) {
        launch();
    }
}
```

#### 🧩 Componentes de la Interfaz

1. **TextField**: Caja de texto para ingresar el nombre.
2. **Button**: Botón para activar el saludo.

```java
TextField texto = new TextField();
Button boton = new Button("Saludar");
```

#### 🎬 Acciones y Eventos

- **Evento de Botón**: Al hacer clic en el botón, se ejecuta un bloque de código que muestra una ventana emergente.

```java
boton.setOnAction(e -> {
    // Código para mostrar ventana emergente
    String nombre = texto.getText();
    Alert alerta = new Alert(AlertType.WARNING);
    alerta.setTitle("Saludo Personalizado");    
    alerta.setHeaderText(null);        
    alerta.setContentText("Hola mundo " + nombre);
    alerta.show();
});
```

#### 🌐 Diseño y Layout

- **VBox**: Contenedor para alinear los componentes.
- **Scene**: Define el área de contenido de la ventana.

```java
VBox vbox = new VBox(10);
Scene scene = new Scene(vbox, 300, 150);
```

#### 🖼 Ventana Principal

- **Stage**: Representa la ventana principal de la aplicación.

```java
ventanaPrincipal.setTitle("Ejemplo sin FXML");
ventanaPrincipal.setScene(scene);
ventanaPrincipal.show();
```

---

#### Código Completo del Ejemplo

```java
package com.aula.saludo1;

import javafx.application.Application;
import javafx.geometry.Insets;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.Alert;
import javafx.scene.control.Alert.AlertType;
import javafx.scene.control.Button;
import javafx.scene.control.TextField;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;


/**
 * JavaFX App
 */
public class App extends Application {

    public void start(Stage ventanaPrincipal) {
        TextField texto = new TextField();
        Button boton = new Button("Saludar");

        boton.setOnAction(e -> {
            String nombre = texto.getText();
            Alert alerta = new Alert(AlertType.WARNING);
            alerta.setTitle("Saludo Personalizado");    
            alerta.setHeaderText(null);        
            alerta.setContentText("Hola mundo " + nombre);
            alerta.show();
        });

        VBox vbox = new VBox(10);     
        vbox.setAlignment(Pos.CENTER);
        vbox.setPadding(new Insets(20, 20, 20, 20));  
        vbox.getChildren().addAll(texto, boton);
        
        Scene scene = new Scene(vbox, 300, 150);
        ventanaPrincipal.setTitle("Ejemplo sin FXML");
        ventanaPrincipal.setScene(scene);
        ventanaPrincipal.show();
    } 


    public static void main(String[] args) {
        launch();
    }

}
```



## 🎯 Segundo Ejemplo: Con Uso de FXML

### 🛠 Configuración Inicial: Preparando el Proyecto 🛠
1. Crear un nuevo proyecto en tu editor de elección, y elegir el arquetipo `FXML` ya que se utilizará un archivo FXML para diseñar la interfaz.
2. Establecer la versión y el `artifact ID` para el proyecto.
3. Generar la carpeta del proyecto y hacer clic en `Open`.

#### 💻 Código y Estructura de Carpetas 💻
- Carpeta `resources`: Contiene el archivo `vista.fxml`.
- Carpeta `com`: Contiene las clases `ControladorVentana.java` y `App.java`.

### 📜 Uso de FXML para Diseño de Interfaz 📜
- En el archivo `vista.fxml`, especificamos la versión de XML y la codificación.
- Incluimos un `VBox` como elemento raíz, y dentro de él, colocamos un `TextField` y un `Button`.

```xml
<!-- vista.fxml -->
<VBox fx:controller="com.ejemplo02.ControladorVentana">
  <TextField fx:id="texto" />
  <Button fx:id="boton" onAction="#saludar" text="Saludar" />
</VBox>
```

### 🕹 Controlador de la Vista: Enlazando con FXML 🕹
1. En el `VBox` raíz del archivo `vista.fxml`, especificamos el controlador asociado usando `fx:controller`.
2. Asignamos identificadores (`fx:id`) a los componentes `TextField` y `Button`.
3. Establecemos una acción (`onAction`) al botón para que invoque un método específico en el controlador.

```java
// ControladorVentana.java
public class ControladorVentana {
  @FXML
  private TextField texto;
  @FXML
  private Button boton;
  
  @FXML
  public void saludar() {
    String nombre = texto.getText();
    // Código para mostrar alerta
  }
}
```

### 🚀 Inicio de la Aplicación: Configuración y Ejecución 🚀
1. En la clase `App`, en el método `start()`, cargamos el archivo FXML y creamos una `Scene`.
2. Ajustamos la `Scene` al `Stage` y mostramos la ventana.

```java
// App.java
public class App extends Application {
  public void start(Stage primaryStage) {
    Parent root = FXMLLoader.load(getClass().getResource("vista.fxml"));
    Scene scene = new Scene(root, 300, 150);
    primaryStage.setTitle("Ejemplo con FXML");
    primaryStage.setScene(scene);
    primaryStage.show();
  }
  
  public static void main(String[] args) {
    launch(args);
  }
}
```

### 🌈 Mejorando la Interacción 🌈
- Se puede añadir un método `initialize()` en el controlador que se ejecutará después de que se cargue el archivo FXML.

```java
// ControladorVentana.java
public class ControladorVentana {
  @FXML
  public void initialize() {
    boton.setOnAction(e -> saludar());
  }
}
```

### 📝 Detalles Finales y Personalización 📝
- Se pueden capturar detalles del evento de clic del botón y usarlos para, por ejemplo, cambiar el color del botón.

```java
// ControladorVentana.java
public void saludar(ActionEvent e) {
  Button botonPulsado = (Button)e.getSource();
  botonPulsado.setStyle("-fx-background-color: #00FF00;");
}
```


#### Código Completo del Ejemplo 2

##### App.java
```java
package com.ejemplo02;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.scene.Parent;
import javafx.scene.Scene;
import javafx.stage.Stage;

/**
 * JavaFX App
 */
public class App extends Application {

    @Override
    public void start(Stage ventanaPrincipal) throws Exception {

        Parent root = FXMLLoader.load(getClass().getResource("vista.fxml"));
        Scene scene = new Scene(root, 300, 150);
        ventanaPrincipal.setScene(scene);
        ventanaPrincipal.setTitle("Ejemplo con FXML");        
        ventanaPrincipal.show();
    }

    public static void main(String[] args) {
        launch(args);
    }

}
```

##### ControladorVentana.java
```java
package com.ejemplo02;

import javafx.event.ActionEvent;
import javafx.fxml.FXML;
import javafx.scene.control.Alert;
import javafx.scene.control.Button;
import javafx.scene.control.TextField;
import javafx.scene.control.Alert.AlertType;

public class ControladorVentana {

    @FXML
    private TextField texto;
    
    @FXML
    private Button boton;

    @FXML
    public void initialize() {
        boton.setOnAction(e -> saludar(e));
    }

    @FXML
    public void saludar(ActionEvent e) {
        
        Button botonPulsado = (Button)e.getSource();
        botonPulsado.setStyle("-fx-background-color: #ffff00");
        

        String nombre = texto.getText();
        Alert alert = new Alert(AlertType.INFORMATION);
        alert.setTitle("Saludo Personalizado");
        alert.setHeaderText(null);
        alert.setContentText("Hola mundo " + nombre);
        alert.show();
    }
}
```


##### vista.fxml
```xml
<?xml version="1.0" encoding="UTF-8"?>

<?import javafx.scene.layout.VBox?>
<?import javafx.scene.control.Label?>
<?import javafx.scene.control.Button?>
<?import javafx.scene.control.TextField?>
<?import javafx.geometry.Insets?>

<VBox xmlns="http://javafx.com/javafx" xmlns:fx="http://javafx.com/fxml" fx:controller="com.ejemplo02.ControladorVentana">
    <TextField fx:id="texto" />
    <Button fx:id="boton" text="Saludar"  />
    <padding>
        <Insets bottom="20.0" left="20.0" right="20.0" top="20.0" />
    </padding>
</VBox>
```

___
%%
tags: #pagdesarrollo_de_interfaces 
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%