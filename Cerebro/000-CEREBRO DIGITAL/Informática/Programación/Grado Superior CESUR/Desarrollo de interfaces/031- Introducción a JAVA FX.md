---
ID: 31
nombre: Introducción a JAVA FX
tags:
  - pagdesarrollo_de_interfaces
---
___
## 🌟 Introducción a JavaFX

![](https://www.youtube.com/watch?v=HOr5djeytsA&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=211&ab_channel=Aulaenlanube)

### 📚 Preámbulo: Requisitos Previos
Antes de adentrarnos en el mundo de JavaFX, es crucial que estés familiarizado con el concepto de Mabel, como se discutió en el vídeo anterior del curso. Si no tienes claro qué es Mabel, te recomendamos que revises ese material primero.

### 🌱 Origen y Evolución de JavaFX
JavaFX se originó como una evolución de Java Swing, que comenzó a mostrar sus limitaciones con la aparición de nuevos dispositivos como móviles y tablets. Lanzado inicialmente en la versión 8 de Java en 2014, JavaFX ofrecía una gama más amplia de capacidades gráficas.

#### 🎨 Características Gráficas
- Creación de formas en 2D y 3D
- Trabajo avanzado con imágenes
- Incorporación de contenido multimedia
- Uso de hojas de estilo CSS para el diseño de interfaces

### 🔄 Cambios en la Mantenimiento: De Oracle a OpenJFX
Aunque inicialmente fue desarrollado y mantenido por Oracle y formaba parte del JDK oficial, a partir de la versión 11 de Java, Oracle descontinuó su soporte. Desde entonces, JavaFX se ha convertido en un proyecto de código abierto bajo el nombre de OpenJFX, mantenido por la comunidad de desarrolladores.

### 🛠 Herramientas y Versiones
- **OpenJFX**: Versión de código abierto que utilizaremos en este curso.
- **Gluon**: Una implementación comercial con herramientas especializadas, por ejemplo, para el desarrollo móvil.

### 📐 Arquitectura: Modelo Vista Controlador (MVC)
En este curso, abordaremos el desarrollo de aplicaciones JavaFX utilizando el patrón de diseño Modelo-Vista-Controlador (MVC).

#### 📂 Diseño de la Interfaz: Uso de FXML
Para el diseño de la interfaz, utilizaremos archivos FXML, que permiten una organización más clara y modular del código de la interfaz de usuario.

___
## Ejemplo App

### 🛠 API de OpenJFX: Núcleo para Aplicaciones JavaFX

#### 🏗 Componentes Clave
La API de OpenJFX nos ofrece clases e interfaces fundamentales para desarrollar aplicaciones JavaFX. Aquí hay algunos componentes clave:

- **Stage**: Representa la ventana principal de la aplicación.
- **Scene**: Contiene todos los elementos que se muestran en una ventana. Puedes tener múltiples escenas y cambiar entre ellas.
- **Nodes**: Elementos individuales como botones, tablas, etiquetas, etc.

#### 📝 Ejemplo: "Hola Mundo" en JavaFX

```java
// Clase principal que hereda de 'Application'
public class HelloWorld extends Application {
    // Método 'start' que se llama después de inicializar JavaFX
    public void start(Stage primaryStage) {
        // Creación de un botón
        Button btn = new Button("Saludar");
        // Acción al hacer clic en el botón
        btn.setOnAction(e -> System.out.println("Hola Mundo desde JavaFX"));
        
        // Creación de una escena
        Scene scene = new Scene(btn, 200, 100);
        
        // Configuración de la ventana principal
        primaryStage.setScene(scene);
        primaryStage.setTitle("Mi Primera Aplicación");
        primaryStage.show();
    }
    
    // Método 'main' que inicia la aplicación
    public static void main(String[] args) {
        launch(args);
    }
}
```

Este ejemplo muestra cómo crear una ventana con un botón que, al hacer clic, muestra un mensaje en la consola.

### 🚀 Inicialización y Punto de Entrada

#### 🌱 Método `main`
El método `main` invoca al método `launch`, que es el punto de entrada de cualquier aplicación JavaFX. Este método inicializa el entorno de JavaFX y luego llama al método `start`.

```java
// Método 'main' que sirve como punto de entrada
public static void main(String[] args) {
    launch(args);
}
```

#### 🌟 Método `start`
El método `start` es donde generalmente configuramos la interfaz de usuario y mostramos la ventana principal. Este método recibe una instancia de la clase `Stage`, que representa la ventana principal.

### 📚 Documentación y Recursos Adicionales

Si deseas explorar más, la API de OpenJFX ofrece documentación detallada y ejemplos para cada clase y método. Puedes buscar clases específicas o navegar por los distintos módulos para encontrar lo que necesitas.

---
## 🌟 Modelo-Vista-Controlador (MVC) en JavaFX

### 📚 Introducción al MVC en JavaFX

Aunque es posible crear aplicaciones JavaFX de manera sencilla, la práctica común es utilizar la arquitectura Modelo-Vista-Controlador (MVC). Este patrón de diseño es especialmente útil para separar la lógica de negocio de la interfaz de usuario, lo que facilita la gestión y el mantenimiento del código.

### 🏗 Componentes del MVC

#### 📊 Modelo (Model)
- **Definición**: Representa la lógica de negocio y los datos en la aplicación.
- **Características**:
  - Compuesto por métodos y objetos necesarios para el funcionamiento de la aplicación.
  - No tiene conocimiento de la interfaz de usuario.
  - Se comunica con la vista a través del controlador.

#### 🖼 Vista (View)
- **Definición**: Es la interfaz de usuario que interactúa con el usuario.
- **Características**:
  - Compuesta por elementos de la interfaz como botones, cajas de texto, tablas, imágenes, etc.
  - Obtiene datos del modelo para representarlos.
  - Envía las acciones del usuario al controlador.

#### 🎛 Controlador (Controller)
- **Definición**: Actúa como intermediario entre el modelo y la vista.
- **Características**:
  - Recibe las acciones del usuario desde la vista.
  - Invoca métodos del modelo según las acciones del usuario.
  - Actualiza la vista en función de los cambios en el modelo.

### 🔄 Flujo de Interacción en MVC

1. El usuario interactúa con la **Vista**.
2. La **Vista** envía las acciones del usuario al **Controlador**.
3. El **Controlador** procesa la acción y solicita cambios al **Modelo** si es necesario.
4. El **Modelo** actualiza su estado y notifica al **Controlador**.
5. El **Controlador** actualiza la **Vista** en función de los cambios en el **Modelo**.

___
## 🎨 Diseño de la UI con FXML en JavaFX

### 📄 Introducción al Uso de FXML

En el desarrollo de aplicaciones JavaFX, una práctica común es diseñar la interfaz de usuario utilizando archivos FXML. Estos archivos son similares al `pom.xml` que se usa en Maven y están escritos en un lenguaje de marcado basado en XML. La ventaja de usar FXML es que permite separar la lógica de la aplicación de su interfaz gráfica, lo que facilita la organización del código.

#### 📁 Estructura de un Archivo FXML

Un archivo FXML típico comienza con la definición del tipo de versión de XML y la codificación de caracteres, que generalmente es UTF-8. A continuación, se pueden añadir distintos componentes a la vista. Por ejemplo:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<AnchorPane fx:controller="MyController">
    <Button fx:id="myButton"/>
</AnchorPane>
```

En este ejemplo, se crea un contenedor `AnchorPane` y dentro de él, se coloca un botón. Cada componente se define mediante etiquetas. El `AnchorPane` tiene una etiqueta de apertura y otra de cierre, mientras que el botón tiene una única etiqueta auto-cerrada.

### 🎛 Controladores en FXML

#### 🔄 Asociación de Controladores

Para controlar el comportamiento de los componentes de la vista, se asigna un controlador a ellos. En el ejemplo anterior, el controlador se asigna al `AnchorPane` mediante la instrucción `fx:controller="MyController"`. Aquí, `MyController` es una clase Java que controlará este componente.

#### 🆔 Identificadores de Componentes

Los componentes también pueden tener identificadores, que se definen con `fx:id`. Estos identificadores permiten acceder a los componentes desde el código Java para manipularlos. En el ejemplo, el botón tiene un `fx:id` de `myButton`.

### 🕹 Ejemplo de Clase Controladora en Java

```java
public class MyController {
    @FXML
    private Button myButton;
    
	@FXML
    public void initialize() {
        myButton.setOnAction(e -> {
            System.out.println("Botón pulsado");
        });
    }
}
```

En esta clase controladora, se utiliza la anotación `@FXML` para enlazar el botón definido en el archivo FXML con un campo en la clase Java. El método `initialize` se ejecuta automáticamente después de que todos los elementos de la UI se han cargado desde el archivo FXML. Dentro de este método, se define un evento `setOnAction` para el botón, que mostrará "Botón pulsado" en la consola cuando se haga clic en él.

#### 📝 Notas Adicionales

* Generalmente, hay una única clase controladora asociada a cada archivo FXML.
* Es común asignar el controlador al elemento raíz del archivo FXML, que en este caso es el `AnchorPane`.

Con estos elementos en su lugar, tienes una arquitectura limpia y bien organizada para desarrollar aplicaciones JavaFX más complejas.

### Ejemplo de MVC en JavaFX

```java
// modelo
public class Contador{
	private int n = 0;
	
	public void incrementar() {
		n++;
	}
	
	public int get() {
		return n;
	}
}

// Vista(FXML)
<Button fx:id="botonIncrementar" text="Incrementar" />

// Controlador
public class ContadorControlador {
	@FXML private Button botonIncrementar;
	private Contador contador;
	@FXML
	public void initialize() {
		contador = new Contador();
		botonIncrementar.setOnAction(e -> {
			contador.incrementar();
			System.out.println("Contador: " + contador.get());
		});
	}

}
```

___
## 🛠️ Funcionamiento de una App Maven en JavaFX

### 🌐 Introducción a Maven y JavaFX

Maven es una herramienta de gestión de proyectos que facilita la creación y el mantenimiento de aplicaciones JavaFX. En este contexto, vamos a explorar cómo funciona una aplicación JavaFX sencilla que utiliza Maven para su gestión.

### 📦 Creación del Proyecto en Visual Studio Code

Para empezar, se crea un nuevo proyecto en Visual Studio Code. Se puede optar por un arquetipo predefinido de JavaFX o configurarlo manualmente a través de Maven. En este caso, se elige un arquetipo predefinido de JavaFX para generar un proyecto de ejemplo.

1. Seleccionar el arquetipo `JavaFX Archetype FXML`.
2. Nombrar el proyecto, por ejemplo, `AulaFX.Prueba1`.
3. Elegir la versión inicial del proyecto, generalmente `1.0`.

Una vez creado el proyecto, se generará una estructura de carpetas que incluye:

- Carpeta `Java` con el paquete `AulaFX.Prueba1`.
- Carpeta `resources` con dos archivos FXML para representar dos escenas.
- Carpeta `target` con archivos compilados.
- Archivo `pom.xml` para la configuración de Maven.

#### 📝 Nota

Se añade un archivo `module-info.java` si la aplicación está modularizada. Este archivo especifica qué módulos del JDK o de terceros son necesarios para la aplicación.
Para que no de error podemos añadir al código ``transitive`` :

```java
module com.aulafx.prueba1 {
    requires transitive javafx.controls;
    requires javafx.fxml;
  
    opens com.aulafx.prueba1 to javafx.fxml;
    exports com.aulafx.prueba1;
}
```


### 🔄 Cambio entre Vistas

La aplicación de ejemplo tiene dos vistas: `primary` y `secondary`. Cada vista tiene su propio controlador, y estos controladores se encargan de cambiar entre las vistas.

#### 📄 Código de Controladores

```java
// PrimaryController.java
public class PrimaryController {
    @FXML
    private void switchToSecondary() throws IOException {
        App.setRoot("secondary");
    }
}

// SecondaryController.java
public class SecondaryController {
    @FXML
    private void switchToPrimary() throws IOException {
        App.setRoot("primary");
    }
}
```

#### 📄 Código de Vistas (FXML)

```xml
<!-- primary.fxml -->
<VBox fx:controller="com.aulafx.prueba1.PrimaryController">
    <Label text="Primary View" />
    <Button text="Switch to Secondary View" onAction="#switchToSecondary"/>
</VBox>

<!-- secondary.fxml -->
<VBox fx:controller="com.aulafx.prueba1.SecondaryController">
    <Label text="Secondary View" />
    <Button text="Switch to Primary View" onAction="#switchToPrimary" />
</VBox>
```

### 🎮 Funcionamiento de la Aplicación

La aplicación inicia con la vista `primary`. Al hacer clic en el botón "Switch to Secondary View", se cambia a la vista `secondary`. Este cambio se realiza a través de los métodos en los controladores, que invocan al método `setRoot` de la clase `App`.

#### 📄 Código de la Clase Principal (App.java)

```java
public class App extends Application {
    private static Scene scene;

    @Override
    public void start(Stage stage) throws IOException {
        scene = new Scene(loadFXML("primary"), 640, 480);
        stage.setScene(scene);
        stage.show();
    }

    static void setRoot(String fxml) throws IOException {
        scene.setRoot(loadFXML(fxml));
    }

    private static Parent loadFXML(String fxml) throws IOException {
        FXMLLoader fxmlLoader = new FXMLLoader(App.class.getResource(fxml + ".fxml"));
        return fxmlLoader.load();
    }

	public static void main(String[] args) {
        launch();
    }
}
```

Con estos elementos, se tiene una base sólida para desarrollar aplicaciones más complejas en JavaFX utilizando Maven.


___
%%
tags: #pagdesarrollo_de_interfaces 
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%