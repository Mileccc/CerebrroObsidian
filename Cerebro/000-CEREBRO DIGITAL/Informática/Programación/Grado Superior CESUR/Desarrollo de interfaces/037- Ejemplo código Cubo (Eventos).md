---
ID: 37
nombre: Ejemplo código Cubo
tags:
  - pagdesarrollo_de_interfaces
---
___

```java
package com.aula.cubo;

import javafx.application.Application;
import javafx.geometry.Point3D;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.image.Image;
import javafx.scene.input.KeyCode;
import javafx.scene.input.MouseButton;
import javafx.scene.input.ScrollEvent;
import javafx.scene.layout.VBox;
import javafx.scene.paint.Color;
import javafx.scene.paint.PhongMaterial;
import javafx.scene.shape.Box;
import javafx.scene.transform.Rotate;
import javafx.stage.Stage;

public class App extends Application {

    private double puntoAnclajeX, puntoAnclajeY;
    private double anguloAnclajeX = 0;
    private double anguloAnclajeY = 0;
    private double factorZoom = 1;

    private final Rotate rotacionX = new Rotate(0, Rotate.X_AXIS);
    private final Rotate rotacionY = new Rotate(0, Rotate.Y_AXIS);    

    // parte colores
    private final Color[] coloresCubo = {
            Color.RED, Color.DODGERBLUE, Color.PALEGREEN, Color.YELLOW, Color.ORANGE, Color.PURPLE
    };
    private int indiceColorActual = 0;

    @Override
    public void start(Stage ventanaPrincipal) {

        Box cubo = new Box();
        cubo.setWidth(200.0);
        cubo.setHeight(200.0);
        cubo.setDepth(200.0);

        PhongMaterial material = new PhongMaterial();
        //material.setDiffuseColor(Color.PALEGREEN);   
        material.setDiffuseMap(new Image("texture2.jpg"));
        cubo.setMaterial(material);

        VBox root = new VBox();
        root.getChildren().add(cubo);
        root.setAlignment(Pos.CENTER);
        
        Scene scene = new Scene(root, 600, 400);        
        scene.setFill(Color.SILVER);

        // inicializar la rotación
        cubo.getTransforms().addAll(rotacionX, rotacionY);

        // configuramos la ventana
        ventanaPrincipal.setTitle("Ejemplo de Cubo 3D con Zoom en JavaFX");
        ventanaPrincipal.setScene(scene);
        ventanaPrincipal.show();

        // creamos los eventos
        crearEventos(root, scene, cubo);
    }

    private void crearEventos(VBox vbox, Scene scene, Box cubo) {

        Rotate xRotate = new Rotate(0, new Point3D(0, 0, 0)); 
        Rotate yRotate = new Rotate(0, new Point3D(0, 0, 0));

        vbox.getTransforms().addAll(xRotate, yRotate);

        // bindings para la rotación
        xRotate.angleProperty().bind(rotacionX.angleProperty());
        yRotate.angleProperty().bind(rotacionY.angleProperty());

        // evento al hacer click en la escena, define en punto de inicio
        scene.setOnMousePressed(event -> {
            puntoAnclajeX = event.getSceneX();
            puntoAnclajeY = event.getSceneY();
            anguloAnclajeX = rotacionX.getAngle();
            anguloAnclajeY = rotacionY.getAngle();
        });

        // evento al arrastrar para girar el cubo
        scene.setOnMouseDragged(event -> {
            rotacionX.setAngle(anguloAnclajeX - (puntoAnclajeY - event.getSceneY()));
            rotacionY.setAngle(anguloAnclajeY + (puntoAnclajeX - event.getSceneX()));
        });

        // evento scroll para cambiar el tamaño del cubo
        scene.addEventHandler(ScrollEvent.SCROLL, event -> {
            factorZoom = 1.1;
            double deltaY = event.getDeltaY();

            if (deltaY < 0) {
                factorZoom = 1 / factorZoom;
            }

            cubo.setScaleX(cubo.getScaleX() * factorZoom);
            cubo.setScaleY(cubo.getScaleY() * factorZoom);
            cubo.setScaleZ(cubo.getScaleZ() * factorZoom);
        });

        // evento click derecho para cambiar el color del cubo
        cubo.setOnMouseClicked(event -> {
            if (event.getButton() == MouseButton.SECONDARY) {
                cambiarColorCubo(cubo);
            }
        });

        // evento con teclado para hacer zoom
        scene.setOnKeyPressed(e -> {

            factorZoom = 1.1;

            if (e.isControlDown() && e.getCode() == KeyCode.PLUS) {
                cubo.setScaleX(cubo.getScaleX() * factorZoom);
                cubo.setScaleY(cubo.getScaleY() * factorZoom);
                cubo.setScaleZ(cubo.getScaleZ() * factorZoom);
            }
            if (e.isControlDown() && e.getCode() == KeyCode.MINUS) {
                factorZoom = 1 / factorZoom;
                cubo.setScaleX(cubo.getScaleX() * factorZoom);
                cubo.setScaleY(cubo.getScaleY() * factorZoom);
                cubo.setScaleZ(cubo.getScaleZ() * factorZoom);
            }
        });
    }

    private void cambiarColorCubo(Box cubo) {
        indiceColorActual = (indiceColorActual + 1) % coloresCubo.length;
        PhongMaterial material = (PhongMaterial) cubo.getMaterial();
        material.setDiffuseColor(coloresCubo[indiceColorActual]);
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```

Este código es un ejemplo de una aplicación JavaFX que crea una caja 3D (o cubo) y permite al usuario interactuar con ella a través de varios eventos de mouse y teclado.

### Descripción de las partes principales del código:

1. **Importaciones**: Importa las clases y paquetes necesarios de JavaFX y otras bibliotecas.

2. **Variables de instancia**: 
    - `puntoAnclajeX, puntoAnclajeY`: Almacenan la posición del mouse cuando se hace clic en la escena.
    - `anguloAnclajeX, anguloAnclajeY`: Almacenan los ángulos de rotación del cubo.
    - `factorZoom`: Almacena el factor de zoom.
    - `rotacionX, rotacionY`: Rotaciones alrededor de los ejes X y Y.
    - `coloresCubo`: Un array de colores que se pueden aplicar al cubo.
    - `indiceColorActual`: Índice para el color actual del cubo.

3. **Método `start`**: 
    - Crea el cubo y lo configura.
    - Crea una `Scene` y una `VBox` para contener el cubo.
    - Añade transformaciones de rotación al cubo.
    - Configura y muestra la ventana principal (`Stage`).

4. **Método `crearEventos`**: 
    - Define varios eventos de mouse y teclado para interactuar con el cubo.
    - `setOnMousePressed`: Guarda la posición y los ángulos de rotación actuales.
    - `setOnMouseDragged`: Actualiza los ángulos de rotación basados en el movimiento del mouse.
    - `addEventHandler(ScrollEvent.SCROLL)`: Cambia el tamaño del cubo con el scroll del mouse.
    - `setOnMouseClicked`: Cambia el color del cubo con un clic derecho.
    - `setOnKeyPressed`: Cambia el tamaño del cubo con teclas de teclado.

5. **Método `cambiarColorCubo`**: Cambia el color del cubo, circulando a través del array `coloresCubo`.

6. **Método `main`**: Ejecuta la aplicación.

### Eventos y Comportamientos
- Puedes girar el cubo arrastrando el mouse.
- Puedes hacer zoom en el cubo usando la rueda del mouse o las teclas `+` y `-` con la tecla `Ctrl` presionada.
- Puedes cambiar el color del cubo con un clic derecho.


___
%%
tags: #pagdesarrollo_de_interfaces #Java #JavaFX #3D #Cubo #Rotación #Zoom #Eventos #MouseEvents #KeyEvents #ScrollEvent #Scene #VBox #PhongMaterial #Texture #Color #Box #Transforms #Point3D #Rotate #KeyCode #Binding #Scale
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%