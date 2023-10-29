---
ID: 25
nombre: Propiedades Específicas de Componentes en JavaFX
tags:
  - pagdesarrollo_de_interfaces
---
___
### 📦 Componentes y Sus Características Únicas

En el desarrollo de interfaces con JavaFX, cada componente tiene su propio conjunto de propiedades y métodos que lo hacen único. Estas características específicas se describen en la documentación oficial, que es una herramienta invaluable para cualquier desarrollador.

#### 📐 Rectángulos en JavaFX

Para ilustrar cómo funcionan estas propiedades específicas, consideremos el caso de añadir un rectángulo a una escena. Este componente se encuentra en el paquete `javafx.scene.shape`, específicamente en la clase `javafx.scene.shape.Rectangle`.

##### Propiedades del Rectángulo

- **Posicionamiento**: Utilizamos los métodos `setX` y `setY` para definir la posición.
- **Dimensiones**: Los métodos `setWidth` y `setHeight` nos permiten establecer las dimensiones.
- **Esquinas Redondeadas**: La propiedad `setArcHeight` y `setArcWidth` nos permite redondear las esquinas.

```java
import javafx.scene.shape.*;
Rectangle r = new Rectangle();
r.setX(50);
r.setY(50);
r.setWidth(200);
r.setHeight(100);
r.setArcWidth(20);
r.setArcHeight(20);
```

#### 📊 GridPane: Un Ejemplo de Contenedor

Los contenedores como `GridPane` también tienen propiedades específicas que dependen de los nodos que contienen.

##### Propiedades del GridPane

- **Posicionamiento de Nodos**: Utilizamos `setRowIndex` y `setColumnIndex` para posicionar los nodos dentro de la matriz.

```java
GridPane gridpane = new GridPane();
Button button = new Button();
GridPane.setRowIndex(button, 0);
GridPane.setColumnIndex(button, 1);
```

### 📘 Ejemplo Práctico: Migración desde Java Swing a JavaFX

Si estás considerando migrar de Java Swing a JavaFX, aquí hay un ejemplo práctico que no requiere la definición a través de FXML, controladores o modelos.

#### Pasos para Configurar el Proyecto en Eclipse

1. Crear un nuevo proyecto.
2. Añadir las librerías de JavaFX 14.
3. Crear un fichero `Main.java` basado en ejemplos de la documentación de JavaFX.

```java
import javafx.application.Application;
import javafx.scene.Group;
import javafx.scene.Scene;
import javafx.scene.shape.Rectangle;
import javafx.scene.shape.Line;
import javafx.scene.paint.Color;
import javafx.stage.Stage;

public class Main extends Application {
    @Override
    public void start(Stage primaryStage) throws Exception {
        Group g = new Group();
        for (int i = 0; i < 5; i++) {
            Rectangle r = new Rectangle();
            r.setY(i * 20);
            r.setWidth(100);
            r.setHeight(10);
            r.setFill(Color.RED);
            g.getChildren().add(r);
            
            Line l = new Line(0, 0, i * 50, 0);
            l.setStrokeWidth(1.0);
            g.getChildren().add(l);
        }
        primaryStage.setScene(new Scene(g, 400, 300));
        primaryStage.show();
    }
    public static void main(String[] args) {
        launch(args);
    }
}
```

4. Establecer los argumentos necesarios para la ejecución en la VM.

___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #Componentes #PropiedadesEspecíficas #DocumentaciónOficial #Rectángulo #GridPane #Migración #JavaSwing #Eclipse #ConfiguraciónProyecto #Posicionamiento #Dimensiones #EsquinasRedondeadas #PosicionamientoDeNodos #LibreríasJavaFX #EjemploPráctico
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%