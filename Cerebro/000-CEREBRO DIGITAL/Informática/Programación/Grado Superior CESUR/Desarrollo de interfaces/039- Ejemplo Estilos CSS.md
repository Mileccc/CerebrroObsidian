---
ID: 39
nombre: Ejemplo Estilos CSS
tags:
  - pagdesarrollo_de_interfaces
---
___

### App.java
```java
package com.aula.estilos;

import javafx.application.Application;
import javafx.application.Platform;
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

        // cargamos el FXML desde la carpeta resources
        Parent root = FXMLLoader.load(getClass().getResource("/com/aula/estilos/ventanaPrincipal.fxml"));
        Scene scene = new Scene(root, 500, 400);
        scene.getStylesheets().add(getClass().getResource("/css/estilosVentanaPrincipal1.css").toExternalForm());

        // configuramos ventana principal
        ventanaPrincipal.setTitle("Ventana Principal");
        ventanaPrincipal.setScene(scene);
        ventanaPrincipal.show();

        // método para mostrar una segunda ventana
        abrirVentanaSecundaria();

        // evento para cerrar la App al cerrar la ventana principal
        ventanaPrincipal.setOnCloseRequest(e -> {
            Platform.exit();
            System.exit(0);
        });
    }

    private void abrirVentanaSecundaria() throws Exception {

        // creamos un nuevo Stage (ventana)
        Stage ventanaSecundaria = new Stage();

        // cargamos el FXML desde la carpeta resources
        Parent root = FXMLLoader.load(getClass().getResource("ventanaSecundaria.fxml"));
        Scene scene = new Scene(root, 300, 200);
        scene.getStylesheets().add(getClass().getResource("/css/estilosVentanaSecundaria.css").toExternalForm());

        // configuramos ventana secundaria
        ventanaSecundaria.setTitle("Ventana Secundaria");
        ventanaSecundaria.setScene(scene);
        ventanaSecundaria.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```


### ControladorVentanaPrincipal.java

```java
package com.aula.estilos;

import javafx.fxml.FXML;
import javafx.scene.control.Alert;
import javafx.scene.control.Alert.AlertType;
import javafx.scene.control.Button;

public class ControladorVentanaPrincipal {

    private int estiloBoton = 0;

    @FXML
    private Button botonPrincipal;

    @FXML
    private Button botonSecundario;

    @FXML
    public void saludo() {
        Alert alerta = new Alert(AlertType.INFORMATION);
        alerta.setTitle("Saludo");
        alerta.setHeaderText(null);
        alerta.setContentText("Hola mundo desde JAVA FX!");
        alerta.show();
    }

    @FXML
    public void modificarEstilo() {

        if (estiloBoton % 2 == 0) {
            botonSecundario.getScene().getStylesheets().clear();
            botonSecundario.getScene().getStylesheets().add(getClass().getResource("/css/estilosVentanaPrincipal2.css").toExternalForm());                 
        } else {
            botonSecundario.getScene().getStylesheets().clear();
            botonSecundario.getScene().getStylesheets().add(getClass().getResource("/css/estilosVentanaPrincipal1.css").toExternalForm());  
        }
        estiloBoton++;
    }
}
```

### ControladorVentanaSecundaria

```java
package com.aula.estilos;

import javafx.fxml.FXML;
import javafx.scene.control.Button;
import javafx.stage.Stage;

public class ControladorVentanaSecundaria {

    @FXML
    private Button botonCerrar;

    @FXML
    public void cerrarVentana() {
        Stage ventanaActual = (Stage)botonCerrar.getScene().getWindow();
        ventanaActual.close(); 
    }    
}
```

### estilosVentanaPrincipal1.css

```css
#etiquetaPrincipal {
	-fx-text-fill: #670000;  
	-fx-font-size: 24px; 	
	-fx-font-weight: bold;
}

.boton {
    -fx-background-color: #4a29b0; 
	-fx-text-fill: white;      	
	-fx-border-radius: 5px;    	
	-fx-background-radius: 5px;	
	-fx-padding: 5px 15px;  
}


```

### estilosVentanaPrincipal2.css

```css
#etiquetaPrincipal {
	-fx-text-fill: #2c3e50;  
	-fx-font-size: 18px; 	
	-fx-font-weight: bold;
}

.boton {
    -fx-background-color: #ee8c23; 
	-fx-text-fill: black;      	
	-fx-border-radius: 0px;    	
	-fx-background-radius: 0px;	
	-fx-padding: 5px 15px;   
	-fx-border-color: rgb(0, 56, 102);
    -fx-border-width: 5px;
	-fx-font-weight: bold;    
}

```


### estilosVentanaSecundaria.css

```css
Label {
	-fx-text-fill: #2c3e50;  
	-fx-font-size: 18px; 	
	-fx-font-weight: bold;
}

#botonCerrar {
	-fx-background-color: #3498db; 
	-fx-font-size: 14px; 	
	-fx-text-fill: white;      	
	-fx-border-radius: 5px;    	
	-fx-background-radius: 5px;	
	-fx-padding: 5px 15px;     	
}

```


### ventanaPrincipal.fxml

```xml
<?xml version="1.0" encoding="UTF-8"?>

<?import javafx.scene.layout.VBox?>
<?import javafx.scene.control.Label?>
<?import javafx.scene.control.Button?>
<?import javafx.geometry.Insets?>

<VBox alignment="CENTER" spacing="20.0" xmlns="http://javafx.com/javafx/8.0.171" xmlns:fx="http://javafx.com/fxml/1" fx:controller="com.aula.estilos.ControladorVentanaPrincipal">
   <children>
      <Label fx:id="etiquetaPrincipal" text="Ejemplos CSS con JAVA FX y FXML" />
      <Button styleClass="boton" fx:id="botonPrincipal" text="Saludar" onAction="#saludo"/>
      <Button styleClass="boton" fx:id="botonSecundario" text="Modificar Estilo" onAction="#modificarEstilo"/>
   </children>
   <padding>
      <Insets bottom="20.0" left="20.0" right="20.0" top="20.0" />
   </padding>
</VBox>
```

### ventanaSecundaria.fxml

```xml
<?xml version="1.0" encoding="UTF-8"?>

<?import javafx.scene.layout.VBox?>
<?import javafx.scene.control.Label?>
<?import javafx.scene.control.Button?>
<?import javafx.geometry.Insets?>

<VBox alignment="CENTER" spacing="20.0" xmlns="http://javafx.com/javafx/8.0.171" xmlns:fx="http://javafx.com/fxml/1" fx:controller="com.aula.estilos.ControladorVentanaSecundaria">
    <children>
        <Label text="Ventana Secundaria" />
        <Button fx:id="botonCerrar" text="Cerrar ventana" onAction="#cerrarVentana" />
    </children>
    <padding>
        <Insets bottom="20.0" left="20.0" right="20.0" top="20.0" />
    </padding>
</VBox>
```


### pom.xml

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.aula.estilos</groupId>
    <artifactId>estilos</artifactId>
    <version>1.0</version>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>11</maven.compiler.source>
        <maven.compiler.target>11</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.openjfx</groupId>
            <artifactId>javafx-controls</artifactId>
            <version>13</version>
        </dependency>
        <dependency>
            <groupId>org.openjfx</groupId>
            <artifactId>javafx-fxml</artifactId>
            <version>13</version>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.0</version>
                <configuration>
                    <release>11</release>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.openjfx</groupId>
                <artifactId>javafx-maven-plugin</artifactId>
                <version>0.0.6</version>
                <executions>
                    <execution>
                        <!-- Default configuration for running -->
                        <!-- Usage: mvn clean javafx:run -->
                        <id>default-cli</id>
                        <configuration>
                            <mainClass>com.aula.estilos.App</mainClass>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
</project>
```

___
___
## Explicación del código

Este es un proyecto JavaFX que utiliza Maven para su gestión de dependencias. El proyecto incluye dos ventanas: una principal y una secundaria, ambas con sus propios controladores y estilos CSS. También utiliza archivos FXML para definir la estructura de las ventanas.

### App.java
1. `package com.aula.estilos;`: Define el paquete en el que se encuentra esta clase.
2. `import ...`: Importa las bibliotecas necesarias para la aplicación.
3. `public class App extends Application`: Declara la clase principal `App` que hereda de la clase `Application` de JavaFX.
4. `public void start(Stage ventanaPrincipal) throws Exception`: Método que se ejecuta al iniciar la aplicación.
5. `Parent root = FXMLLoader.load(...);`: Carga el archivo FXML de la ventana principal.
6. `Scene scene = new Scene(root, 500, 400);`: Crea una nueva escena con el nodo raíz y el tamaño de la ventana.
7. `scene.getStylesheets().add(...);`: Añade la hoja de estilo CSS a la escena.
8. `ventanaPrincipal.setTitle("Ventana Principal");`: Establece el título de la ventana principal.
9. `ventanaPrincipal.setScene(scene);`: Establece la escena para la ventana principal.
10. `ventanaPrincipal.show();`: Muestra la ventana principal.
11. `abrirVentanaSecundaria();`: Llama al método para abrir la ventana secundaria.
12. `ventanaPrincipal.setOnCloseRequest(e -> {...});`: Establece la acción que se ejecutará cuando se cierre la ventana principal.
13. `private void abrirVentanaSecundaria() throws Exception`: Método que abre una ventana secundaria.
14. `public static void main(String[] args)`: Método `main`, punto de entrada de la aplicación.

### ControladorVentanaPrincipal.java
1. `private int estiloBoton = 0;`: Variable que controla el estilo del botón.
2. `@FXML private Button botonPrincipal;`: Declara un botón que está en el archivo FXML.
3. `@FXML public void saludo()`: Método que muestra una alerta.
4. `@FXML public void modificarEstilo()`: Método que cambia el estilo del botón secundario.

### ControladorVentanaSecundaria
1. `@FXML private Button botonCerrar;`: Declara un botón que está en el archivo FXML.
2. `@FXML public void cerrarVentana()`: Método que cierra la ventana actual.

### estilosVentanaPrincipal1.css, estilosVentanaPrincipal2.css, estilosVentanaSecundaria.css
- Estas son las hojas de estilo CSS que definen el aspecto de la aplicación.

### ventanaPrincipal.fxml y ventanaSecundaria.fxml
- Estos archivos XML definen la estructura de la ventana principal y la ventana secundaria.

### pom.xml
- Este es el archivo de configuración de Maven. Define las dependencias y otras configuraciones para la compilación del proyecto.

___
%%
tags: #pagdesarrollo_de_interfaces #Java #JavaFX #FXML #CSS #Maven #Stage #Scene #Controller #Stylesheets #Alert #Button #EventHandling #Dependency #pom #xml #AppLifecycle #MultiWindow #UIComponents #StyleModification
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%