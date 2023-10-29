---
ID: 41
nombre: Código ejemplo Ejercicio de Lineas y Figuras
tags:
  - pagdesarrollo_de_interfaces
---
___

## App
```java
package com.casopractico1;
  
import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.scene.Parent;
import javafx.scene.Scene;
import javafx.stage.Stage;
  
public class App extends Application {
    @Override
    public void start(Stage primaryStage) throws Exception {
        Parent root = FXMLLoader.load(getClass().getResource("vista.fxml"));
  
        Scene scene = new Scene(root, 600, 500);
        scene.getStylesheets().add(getClass().getResource("/css/style.css").toExternalForm());
  
        primaryStage.setTitle("Ejercicio de Manejo de Figuras");
        primaryStage.setScene(scene);
        primaryStage.show();
    }
  
    public static void main(String[] args) {
        launch(args);
    }
}
```


## Controlador
```java
package com.casopractico1;
  
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import javafx.fxml.FXML;
import javafx.scene.Group;
import javafx.scene.paint.Color;
import javafx.scene.shape.Circle;
import javafx.scene.shape.Line;
import javafx.scene.shape.Polygon;
import javafx.scene.shape.Rectangle;
  
public class controlador {
    @FXML
    private Group grupoLineas;
    @FXML
    private Group grupoGeometricas;
    @FXML
    private Line line1;
    @FXML
    private Line line2;
    @FXML
    private Line line3;
    @FXML
    private Polygon penta1;
    @FXML
    private Circle circle1;
    @FXML
    private Rectangle square1;


    @FXML
    public void initialize() { // Método que se ejecuta después de cargar el FXML
        Integer numLineas = 5;
        List<String> listaColores = new ArrayList<>(Arrays.asList("RED","BLUE","GREEN","PINK","PURPLE","BROWN","BLACK","YELLOW","CYAN","LIME"));
        List<Double> listaGrosores = new ArrayList<>(Arrays.asList(0.0,1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0));
        for (int i = 1; i <= numLineas; i++) { // Cambia 5 al número de líneas que quieres añadir
            Line newLine = new Line();
            newLine.setStartX(line1.getStartX());
            newLine.setStartY(line1.getStartY() + i * 10);
            newLine.setEndX(line1.getEndX());
            newLine.setEndY(line1.getEndY() + i * 10);
  
            // Utilizar el módulo para volver al inicio de la lista de colores si i es mayor que su tamaño
            int colorIndex = i % listaColores.size();
            int grosorIndex = i % listaGrosores.size();
            // Aplicar el color usando la propiedad de color de JavaFX
            newLine.setStroke(Color.valueOf(listaColores.get(colorIndex)));
  
            // Aplicar el grosor
            newLine.setStrokeWidth(listaGrosores.get(grosorIndex));
            grupoLineas.getChildren().add(newLine); // Añade la nueva línea al grupo
        }
    }
}
```


## vista
```xml
<?xml version="1.0" encoding="UTF-8"?>
<?import javafx.scene.layout.BorderPane?>
<?import javafx.scene.Group?>
<?import javafx.scene.shape.Line?>
<?import javafx.scene.shape.Polygon?>
<?import javafx.scene.shape.Circle?>
<?import javafx.scene.shape.Rectangle?>
  
<BorderPane xmlns="http://javafx.com/javafx" xmlns:fx="http://javafx.com/fxml"
   fx:controller="com.casopractico1.controlador">
   <top>
      <Group fx:id="grupoLineas">
         <Line fx:id="line1" styleClass="linea1" startX="1" startY="50" endX="150" endY="150" />
         <Line fx:id="line2" styleClass="linea2" startX="350" startY="100" endX="450" endY="10" />
         <Line fx:id="line3" styleClass="linea3" startX="200" startY="150" endX="550" endY="200" />
      </Group>
   </top>
   <bottom>
      <Group fx:id="grupoGeometricas">
         <Polygon fx:id="penta1" styleClass="poligono1"
            points="100.0,50.0, 130.0,90.0, 120.0,130.0, 80.0,130.0, 70.0,90.0 " scaleX="2.0" scaleY="1.5" />
         <Circle fx:id="circle1" styleClass="circulo1" centerX="0" centerY="0" radius="80" translateX="300" />
         <Rectangle fx:id="square1" styleClass="cuadrado1" x="500" y="-100" width="80" height="80" rotate="45" />
      </Group>
  
   </bottom>
</BorderPane>
```

## style
```css
/* Definir el estilo para las líneas */
.linea1 {
    -fx-stroke: blue;
    -fx-stroke-width: 5;
}
.linea2 {
    -fx-stroke: red;
    -fx-stroke-width: 3;
}
.linea3 {
    -fx-stroke: pink;
    -fx-stroke-width: 2;
}
  
/* Definir el estilo para los polígonos */
.poligono1 {
    -fx-fill: purple;
}

/* Definir el estilo para los círculos */
.circulo1 {
    -fx-fill: yellow;
}
  
/* Definir el estilo para los rectángulos */
.cuadrado1 {
    -fx-fill: orange;
}
```


___
%%
tags: #pagdesarrollo_de_interfaces #Java #JavaFX #FXML #CSS #App #Controlador #Vista #Style #GrupoLineas #GrupoGeometricas #Poligono #Circulo #Rectangulo #Linea #Initialize #Métodos #Clases #Paquetes #Estilos
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%