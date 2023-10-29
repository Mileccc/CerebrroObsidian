---
ID: 2
nombre: Class Application
tags:
  - pagdesarrollo_de_interfaces
---
___
La clase Application es el punto de entrada para las aplicaciones de JavaFX. El ciclo de vida incluye la inicialización, inicio y cierre de la aplicación. Las excepciones se manejan en el hilo de la aplicación de JavaFX.

### Métodos más importantes Class Application
1. `start(Stage primaryStage)`: Este es el método principal de una aplicación JavaFX y se debe sobrescribir. Se llama cuando se inicia la aplicación y se utiliza para configurar la escena principal y mostrarla en la ventana primaria (`Stage`).

2. `init()`: Este método se llama antes de que se inicie la aplicación principal y se utiliza para realizar cualquier inicialización necesaria.

3. `stop()`: Se llama cuando la aplicación se cierra y se utiliza para realizar la limpieza o liberación de recursos necesarios antes de que la aplicación finalice.

4. `getParameters()`: Devuelve un objeto `Parameters` que proporciona acceso a los parámetros pasados a la aplicación en la línea de comandos.

5. `getHostServices()`: Devuelve un objeto `HostServices` que proporciona servicios relacionados con el host, como abrir documentos o acceder a la página web.

6. `setUserAgentStylesheet(String userAgentStylesheet)`: Permite establecer una hoja de estilo personalizada para la aplicación, lo que afecta a la apariencia de los controles y elementos de la interfaz de usuario.

7. `launch(String... args)`: Este método estático se utiliza para iniciar una aplicación JavaFX. Es llamado desde el método `main` de la clase principal de la aplicación.

8. `notifyPreloader(Preloader.PreloaderNotification notification)`: Se utiliza para notificar al cargador previo (preloader) acerca del progreso de la carga de la aplicación.

### Paquetes y Clases más importantes Class Application

1. `javafx.application.Preloader`: Contiene clases relacionadas con la implementación de pre-cargadores personalizados que pueden mostrar una interfaz de usuario mientras se carga una aplicación JavaFX.

2. `javafx.application.Application`: Esta es la clase principal que debes extender para crear una aplicación JavaFX. Contiene los métodos `start`, `init`, y `stop`, que son esenciales para el ciclo de vida de la aplicación.

3. `javafx.application.Platform`: Proporciona acceso a la plataforma JavaFX y a métodos estáticos útiles para realizar tareas específicas de la plataforma, como ejecutar código en el hilo de la aplicación de JavaFX.

4. `javafx.application.Application.Parameters`: Un objeto que proporciona acceso a los parámetros pasados a la aplicación en la línea de comandos.

#### Ejemplo

```java
import javafx.application.Application;
import javafx.stage.Stage;
  
public class Main extends Application{
	@Override
	public void start(Stage primaryStage) throws Exception{
	
	}
	  
	public static void main(String[] args) {
		launch(args);
	  
}
```

___
%%
tags:  #pagdesarrollo_de_interfaces  #JavaFX #ClassApplication #Métodos #start #init #stop #getParameters #getHostServices #setUserAgentStylesheet #launch #notifyPreloader #Paquetes #javafx #Ejemplo #CicloDeVida #Excepciones #HiloDeAplicación 
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%