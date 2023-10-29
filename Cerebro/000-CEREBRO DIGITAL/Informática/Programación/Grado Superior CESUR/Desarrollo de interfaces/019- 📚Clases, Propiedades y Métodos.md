---
ID: 19
nombre: Clases, Propiedades y Métodos
tags:
  - pagdesarrollo_de_interfaces
---
___
### 🌐 Introducción a OpenJFX

OpenJFX, también conocido como Open JavaFX 14, es una tecnología de código abierto que facilita el desarrollo de aplicaciones de cliente para escritorio, dispositivos móviles y sistemas embebidos basados en Java. Es una librería extensa y versátil que permite desarrollar aplicaciones de diversas categorías.

### 📦 Paquetes en OpenJFX

OpenJFX se compone de varios paquetes que ayudan en el diseño y planificación de proyectos visuales. A continuación se detallan estos paquetes:

1. **javafx.base**: 
   - **Contiene**: Eventos, propiedades y colecciones principales.
   
2. **javafx.controls**: 
   - **Contiene**: Controles, gráficos y skins disponibles.
   
3. **javafx.fxml**: 
   - **Contiene**: API para el manejo e interpretación de archivos FXML.
   
4. **javafx.graphics**: 
   - **Contiene**: Entorno de layouts y contenedores.
   
5. **javafx.media**: 
   - **Contiene**: API para la gestión de material audiovisual.
   
6. **javafx.swing**: 
   - **Contiene**: Inclusión de Swing en JavaFX.
   
7. **javafx.web**: 
   - **Contiene**: API para contenedores tipo WebView, típicos de dispositivos móviles.

### 🛠️ Estructura de Proyecto en OpenJFX

Para iniciar un nuevo proyecto en OpenJFX, se recomienda seguir una estructura tipo MVC (Modelo-Vista-Controlador). La clase principal del proyecto debe extender de la clase `Application` para poder crear un nuevo entorno basado en OpenJFX.

#### Clase Application

- **Responsabilidad**: Crear una nueva escena.
- **Métodos Importantes**: 
  - `start()`: Método que debe ser implementado.
  - `init()`: Método para configuración inicial.

```java
import javafx.application.Application;
import javafx.stage.Stage;

public class Main extends Application {
    @Override
    public void start(Stage primaryStage) {
        // Código aquí
    }
}
```

![Introducción JAVAFX/OPENJFX v14 - 04 - Primer proyecto. Application - YouTube](https://www.youtube.com/watch?v=N6OqTlSmV0Y)

### 🎭 Concepto de Escena en OpenJFX

En OpenJFX, todo se centra en el concepto de escena. Dentro de cada escena se incluyen diferentes nodos y elementos.

#### Clases Importantes para la Gestión de Escenas

1. **Clase Stage** (*javafx.stage.Stage*): 
   - **Responsabilidad**: Actuar como contenedor padre.
   
2. **Clase Scene** (*javafx.scene.Scene*): 
   - **Responsabilidad**: Contener el resto de controles y elementos.

```java
import javafx.application.Application;
import javafx.scene.Group;
import javafx.scene.Scene;
import javafx.scene.shape.Circle;
import javafx.stage.Stage;

public class Main extends Application {
    @Override
    public void start(Stage primaryStage) {
        // Crear la escena
        Circle circ = new Circle(40, 40, 30);
        Group root = new Group(circ);
        Scene scene = new Scene(root, 800, 600);
        
        // Añadir la escena al escenario
        primaryStage.setTitle("Mi primera aplicación");
        primaryStage.setScene(scene);
        primaryStage.show();
    }
}
```

![Introducción JAVAFX/OPENJFX v14 - 05 - Primer proyecto. Stage/Scene - YouTube](https://www.youtube.com/watch?v=MeuL448pHWE)

#### Puntos a Destacar en el Ejemplo

- `new Scene`: Se crea una nueva escena y se le añade un grupo de componentes visuales.
- `setScene`: Se utiliza este método dentro de `Stage` para añadir la nueva escena.

Con esta estructura y clarificación, se espera que el desarrollo en OpenJFX sea más comprensible y eficiente.

___
%%
tags: #pagdesarrollo_de_interfaces #OpenJFX #JavaFX #Clases #Propiedades #Métodos #Paquetes #EstructuraDeProyecto #MVC #ClaseApplication #Escena #ClaseStage #ClaseScene #CódigoEjemplo
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%