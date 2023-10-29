---
ID: 15
nombre: Ejemplo primera interfaz
tags:
  - pagdesarrollo_de_interfaces
---
___
### Configuraciones iniciales importantes
En ``Window/Preferences/Java/Build Path/User Libraries`` debemos asegurarnos de tener añadidas las librerías de JavaFX

![[Pasted image 20231017162418.png]]

Y en ``Window/Preferences/JavaFX`` el Path del ``SceneBuilder`` y el Path de las librerías del sdk de ``JavaFX``:

![[Pasted image 20231017162642.png]]


### Creación del proyecto y Archivos

![[Pasted image 20231017162819.png]]

Eliminamos el ``module-info.java``:

![[Pasted image 20231017162934.png]]

Creamos el resto de ``archivos``:

![[Pasted image 20231017155602.png|600]]
### Main 

```java
package application;
	
import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.stage.Stage;
import javafx.scene.Parent;
import javafx.scene.Scene;


public class Main extends Application {
	@Override
	public void start(Stage primaryStage) {
		try {
			Parent root = FXMLLoader.load(getClass().getResource("EscenaPrincipal.fxml"));
			Scene scene = new Scene(root);
			primaryStage.setTitle("Mi primer proyecto JavaFX");
			primaryStage.setScene(scene);
			primaryStage.show();
		} catch(Exception e) {
			e.printStackTrace();
		}
	}
	
	public static void main(String[] args) {
		launch(args);
	}
}
```


### Controlador (EscenaPrincipalController.java)

```java
package application;

import javafx.fxml.FXML;

import javafx.event.ActionEvent;

import javafx.scene.control.Label;

public class EscenaPrincipalController {
	@FXML
	private Label labMensaje;

	// Event Listener on Button.onAction
	@FXML
	public void btnPresionado(ActionEvent event) {
		labMensaje.setText("¡¡¡Hola Mundo!!!");
	}
}
```


### View (EscenaPrincipal.fxml )
Este archivo se abre con ``Open with SceneBuilder``:
![[Pasted image 20231017160109.png]]

Aquí se añade un ``botón`` y un ``label`` y se modifican sus propiedades en ``properties``.

![[Pasted image 20231017160502.png]]

En ``code`` al ``botón`` se le da funcionalidad y al ``label`` un ``id``:

![[Pasted image 20231017160639.png]]

![[Pasted image 20231017160711.png]]

Por ultimo añadimos el Path del ``controller`` , guardamos y reiniciamos el archivo ``fxml`` con el el ``SceneBuilder``:

![[Pasted image 20231017160941.png]]

```xml
<?xml version="1.0" encoding="UTF-8"?>
  
<?import javafx.scene.control.Button?>
<?import javafx.scene.control.Label?>
<?import javafx.scene.layout.AnchorPane?>
<?import javafx.scene.text.Font?>
  
<AnchorPane maxHeight="-Infinity" maxWidth="-Infinity" minHeight="-Infinity" minWidth="-Infinity" prefHeight="400.0" prefWidth="600.0" xmlns="http://javafx.com/javafx/20.0.1" xmlns:fx="http://javafx.com/fxml/1" fx:controller="application.EscenaPrincipalController">
	<children>
	<Button layoutX="217.0" layoutY="289.0" mnemonicParsing="false" onAction="#btnPresionado" prefHeight="0.0" prefWidth="167.0" text="Presioname" />
	<Label fx:id="labMensaje" alignment="CENTER" layoutX="183.0" layoutY="188.0" prefHeight="25.0" prefWidth="258.0">
		<font>
			<Font size="36.0" />
		</font>
	</Label>
	</children>
</AnchorPane>
```


### Resultad Ejecución 

![[Pasted image 20231017161033.png]]


### Algunas posibles configuraciones

_Nota_: Quizás sea necesario modificar la configuración de ``Run``:

![[Pasted image 20231017161140.png]]

![[Pasted image 20231017161258.png]]

Aquí iremos a ``Arguments`` y en ``VM arguments`` añadiremos de la página oficial de ``openjfx``:  [link](https://openjfx.io/openjfx-docs/) del punto 3 ``add VM arguments``

```
--module-path "\path\to\javafx-sdk-21\lib" --add-modules javafx.controls,javafx.fxml
```

![[Pasted image 20231017161828.png]]

Entre las comillas del ``Path`` debemos poner la dirección nuestra de donde tenemos la librería de ``JavaFX``.



___
%%
tags: #pagdesarrollo_de_interfaces #ConfiguracionesIniciales #UserLibraries #JavaFX #SceneBuilder #CreaciónProyecto #Archivos #Main #Controlador #EscenaPrincipalController #View #EscenaPrincipalFXML #ResultadosEjecución #ConfiguracionesAdicionales #VMArguments #OpenJFX
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%