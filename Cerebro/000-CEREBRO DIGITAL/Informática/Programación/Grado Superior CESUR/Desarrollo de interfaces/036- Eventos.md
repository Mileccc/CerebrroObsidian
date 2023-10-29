---
ID: 36
nombre: Eventos
tags:
  - pagdesarrollo_de_interfaces
---
___
## 🌟 Introducción a Eventos en JavaFX

![](https://www.youtube.com/watch?v=dUbNtI4bQZo&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=216&ab_channel=Aulaenlanube)

### 🎯 Objetivo del Tema

El objetivo es comprender el funcionamiento de los eventos en JavaFX, un aspecto crucial en el desarrollo de interfaces gráficas interactivas. Aprenderemos sobre el modelo de propagación de eventos, tipos de eventos y cómo gestionarlos a través de ejemplos prácticos.

### 🌐 Modelo de Propagación de Eventos

El modelo de propagación de eventos en JavaFX es de tipo burbuja. En este modelo, un evento se inicia en un nodo específico y se propaga hacia arriba, pasando por cada nivel de anidamiento hasta llegar a la raíz de la escena.

- **Nodo Origen**: El nodo donde se genera el evento inicial.
- **Raíz de la Escena**: El punto final donde el evento llega después de haberse propagado.

### 🎨 Tipos de Eventos Comunes

#### 🖱️ Eventos de Ratón

Los eventos relacionados con las acciones del ratón incluyen:

1. **Click Izquierdo**: Acción de presionar y soltar el botón izquierdo del ratón.
2. **Click Derecho**: Similar al click izquierdo pero con el botón derecho.
3. **Arrastrar**: Mover el ratón mientras se presiona un botón.
4. **Scroll**: Usar la rueda del ratón para desplazarse verticalmente.

```java
// Ejemplo de cómo capturar un click izquierdo en JavaFX
node.setOnMouseClicked(e -> {
    if (e.getButton() == MouseButton.PRIMARY) {
        System.out.println("Click izquierdo capturado!");
    }
});
```

#### ⌨️ Eventos de Teclado

Para el teclado, se pueden capturar eventos como:

1. **Captura de una Tecla**: Registrar cuando se pulsa una tecla específica.
2. **Combinación de Teclas**: Capturar cuando se pulsan dos o más teclas juntas, como `Ctrl+Z`.

```java
// Ejemplo de cómo capturar una tecla en JavaFX
scene.setOnKeyPressed(e -> {
    if (e.getCode() == KeyCode.A) {
        System.out.println("Tecla 'A' presionada!");
    }
});
```

### 🎲 Ejemplo Práctico: Cubo 3D Interactivo

Para consolidar lo aprendido, crearemos un cubo 3D que responderá a varios tipos de eventos.

- **Rotación**: Podremos rotar el cubo haciendo clic y arrastrando con el ratón.
- **Cambiar Tamaño**: Utilizaremos la rueda del ratón o la combinación `Ctrl+Plus` y `Ctrl+Minus` para ajustar el tamaño del cubo.
- **Aplicar Texturas**: Un método adicional permitirá aplicar diferentes texturas al cubo.

```java
// Ejemplo de cómo rotar un cubo 3D con el ratón en JavaFX
cube.setOnMouseDragged(e -> {
    cube.setRotate(e.getSceneX());
});
```


___
## 🌠 Profundizando en Eventos en JavaFX

### 🎯 Enfoque del Tema

El tema aborda la manipulación de eventos en JavaFX, enfocándose en las clases y métodos que permiten manejar eventos. Además, se detalla el ciclo de vida de un evento en JavaFX, desde su origen hasta su finalización, pasando por diferentes fases.

### 📚 Clases y Subclases para Manejar Eventos

En JavaFX, los eventos son instancias de la clase `Event` de la librería `javafx.event`. Esta clase es la base para trabajar con eventos, y cuenta con diversas subclases que nos permiten programar distintos tipos de eventos. Algunas de estas subclases son:

- `ActionEvent`: Para eventos generados a partir de acciones como clics de botón.
- `KeyEvent`: Para eventos de teclado.
- `MouseEvent`: Para eventos relacionados con el ratón.

```java
// Ejemplo de cómo crear un manejador de eventos para un botón usando ActionEvent
Button btn = new Button("Haz clic en el botón");
btn.setOnAction(e -> {
    System.out.println("Botón presionado");
});
```

### 🌐 Modelo de Propagación de Eventos en Burbuja

JavaFX utiliza un modelo de propagación de eventos de tipo burbuja. En este modelo, el ciclo de vida de un evento se puede dividir en tres fases principales:

1. **Fase de Captura**: En esta fase, el evento viaja desde el nodo raíz hasta el nodo objetivo. Todos los nodos intermedios tienen la oportunidad de capturar el evento antes de que llegue a su destino.

2. **Fase Objetivo**: Es el momento en que el nodo objetivo tiene la oportunidad de manejar el evento.

3. **Fase de Burbuja**: Después de la fase objetivo, el evento burbujea de regreso al nodo raíz. Cada nodo intermedio también tiene la opción de manejar el evento en este trayecto de regreso.

### 🛠️ Registro y Manejo de Eventos

Para registrar un manejador de eventos en JavaFX, se utilizan métodos que siguen el patrón `setOn<Event>`. Por ejemplo, el método más típicamente utilizado para manejar clics de botón es `setOnAction`.

- **Instancia del Evento**: El parámetro `e` en el manejador de eventos representa una instancia de la clase de evento correspondiente. Esta instancia contiene información detallada del evento, la cual puede ser utilizada dentro del bloque de código del manejador.

```java
// Ejemplo de cómo capturar una tecla usando KeyEvent
Scene scene = new Scene(...);
scene.setOnKeyPressed(e -> {
    System.out.println("Tecla presionada: " + e.getCode());
});
```


___
## 🌠 Filtrado de Eventos 

### 🎯 Enfoque del Tema 

En este tema, abordaremos el concepto de **filtrado de eventos** en JavaFX. Este proceso nos permite interceptar y manipular eventos antes de que lleguen a su manejador final, ofreciendo un control más fino sobre el flujo de la interacción del usuario.

### 📑 Conceptos Fundamentales de Filtrado de Eventos

El filtrado de eventos se realiza a través del método `addEventFilter`. Este método permite definir un bloque de código que se ejecutará antes de que el evento llegue a su manejador final, representado generalmente por el método `addEventHandler`.

- `addEventFilter`: Método para interceptar eventos antes de su manejo final.
- `addEventHandler`: Método para manejar el evento en su destino final.

### 🎛️ Mecánica del Filtrado y Manejo de Eventos 

La mecánica básica de filtrado de eventos y su manejo en JavaFX se puede entender mejor con un ejemplo práctico. Supongamos que tenemos un objeto `VBox` llamado `vbox`.

```java
// Ejemplo de filtrado y manejo de eventos en un VBox
VBox vbox = new VBox();

// Fase de Filtrado
vbox.addEventFilter(MouseEvent.MOUSE_CLICKED, e -> {
    System.out.println("Has pulsado en el vbox pero todavía no has llegado al destino");
});

// Fase de Manejo
vbox.addEventHandler(MouseEvent.MOUSE_CLICKED, e -> {
    System.out.println("Has pulsado en el vbox: Has llegado al destino");
});
```

1. **Fase de Filtrado**: En esta fase, el código dentro de `addEventFilter` se ejecutará primero. Este código puede realizar acciones intermedias, como validaciones o registros.

2. **Fase de Manejo**: El código dentro de `addEventHandler` se ejecutará después del filtrado, y aquí es donde generalmente se manejará el evento. 

### 🚦 Control del Flujo de Eventos

Una de las ventajas del filtrado de eventos es la posibilidad de controlar el flujo del evento. Por ejemplo, se puede decidir si el evento debe continuar su propagación o detenerse por completo.

Para detener la propagación de un evento, podemos utilizar el método `consume` sobre la instancia del evento en el filtro o en el manejador.

```java
// Ejemplo de consumo de un evento para detener su propagación
vbox.addEventFilter(MouseEvent.MOUSE_CLICKED, e -> {
    e.consume();
    System.out.println("Evento consumido, no llegará al manejador final");
});
```

Este enfoque es especialmente útil cuando deseamos realizar comprobaciones o tomar medidas antes de que el evento alcance su destino final.

### 🛠️ Casos de Uso y Consideraciones 

- El filtrado de eventos es útil para realizar comprobaciones de seguridad, registro de actividad, o modificación del evento antes de su manejo final.
- El manejo de eventos sigue siendo necesario para ejecutar la lógica de negocio principal relacionada con el evento.

___
## 🌠 Eventos: Buenas Prácticas 🛠️

### 🎯 Enfoque del Tema 

Este tema está dedicado a las buenas prácticas a seguir cuando trabajamos con eventos en JavaFX. El objetivo es presentar métodos y técnicas que contribuyan a crear un código más limpio, mantenible y eficiente.

### 📘 Uso de Lambdas para Manejo de Eventos

Las expresiones lambda en Java simplifican enormemente el código relacionado con el manejo de eventos. Estas expresiones son posibles gracias a las **interfaces funcionales**, que son interfaces con un solo método abstracto. 

```java
// Uso de lambdas en manejadores de eventos
button.setOnAction(e -> {
    System.out.println("Botón presionado");
});
```

* **Sintaxis Básica**: La sintaxis de una lambda comienza con los parámetros del método abstracto (si tiene alguno), seguidos por una flecha (`->`) y luego el cuerpo del método.
    - Si el método abstracto no tiene parámetros, se usan paréntesis vacíos `()`.

### 🧩 Separación de Lógica en Manejadores de Eventos

Es importante separar la lógica de manejo de eventos del resto de su aplicación, especialmente en proyectos más grandes.

* **Beneficios**:
    - Mejora la mantenibilidad del código.
    - Facilita las pruebas unitarias.
    - Mejora la legibilidad y la estructura del código.

```java
// Separación de lógica de manejo de eventos
public class MyEventHandler implements EventHandler<ActionEvent> {
    @Override
    public void handle(ActionEvent event) {
        // Código del manejador de eventos
    }
}

// Asignar el manejador de eventos a un botón
button.setOnAction(new MyEventHandler());
```

### 🏷️ Uso de Constantes para Tipos de Eventos

Utilizar constantes para representar diferentes tipos de eventos puede ser extremadamente útil, especialmente cuando se utilizan en múltiples lugares dentro de la aplicación.

```java
// Uso de constantes para tipos de eventos
public static final String BUTTON_PRESSED = "buttonPressed";

// Asignación del tipo de evento como constante
button.addEventHandler(BUTTON_PRESSED, new MyButtonHandler());
```

* **Ventajas**:
    - Hace que el código sea más fácil de entender.
    - Facilita el cambio de tipos de eventos en una sola ubicación.

___

## Ejemplo inicial de Evento ( Menu click derecho y cambiar color)

```java
package com.aula.eventos;

import javafx.application.Application;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.ContextMenu;
import javafx.scene.control.MenuItem;
import javafx.scene.input.MouseButton;
import javafx.scene.input.MouseEvent;
import javafx.scene.layout.VBox;
import javafx.scene.paint.Color;
import javafx.scene.shape.Rectangle;
import javafx.stage.Stage;

/**
 * JavaFX App
 */
public class App extends Application {

    @Override
    public void start(Stage primaryStage) {

        // creamos contenedor con un rectángulo dentro
        VBox root = new VBox();
        root.setAlignment(Pos.CENTER);
        Rectangle rectangulo = new Rectangle(100, 50, Color.GOLD);
        root.getChildren().addAll(rectangulo);
        Scene scene = new Scene(root, 400, 400);

        // ContextMenu para el botón derecho del ratón
        ContextMenu contextMenu = new ContextMenu();
        MenuItem menuItem1 = new MenuItem("Rectángulo Azul");
        MenuItem menuItem2 = new MenuItem("Rectángulo Verde");
        contextMenu.getItems().addAll(menuItem1, menuItem2);

        // establecemos manejadores de eventos para la captura y burbuja
        rectangulo.addEventHandler(MouseEvent.MOUSE_CLICKED, e -> {
            System.out.println("Evento en el rectángulo");
        });
        
        root.addEventHandler(MouseEvent.MOUSE_CLICKED, e -> {            
            if (e.getButton() == MouseButton.SECONDARY) {
                System.out.println("Evento en el VBox: Has pulsado con el botón derecho");
            } else
                System.out.println("Evento en el VBox: Has pulsado con el izquierdo");
        });

        // evento filtrado clic derecho del ratón
        root.addEventFilter(MouseEvent.MOUSE_CLICKED, e -> {
            if (e.getButton() == MouseButton.SECONDARY) {
                System.out.println("Mostrando menú contextual");
                contextMenu.show(root, e.getScreenX(), e.getScreenY());
            }
            else System.out.println("Clic izquierdo filtrado");
            e.consume();
        });

        // acciones sobre las opciones del menú contextual
        menuItem1.setOnAction(e -> rectangulo.setFill(Color.DODGERBLUE));
        menuItem2.setOnAction(e -> rectangulo.setFill(Color.PALEGREEN));

        // configurar escena y ventana
        primaryStage.setTitle("Ejemplo de Manejo de Eventos de Teclado y Ratón");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }

}
```

___
## 🖱️ Eventos en Programación de Interfaces Gráficas

### 🐁 Eventos de Ratón

#### 🎯 `setOnMouseClicked`
Se dispara cuando se hace clic con el ratón en la escena. Se pueden identificar los botones izquierdo y derecho del ratón.

```java
// Detectar clic izquierdo o derecho
escena.setOnMouseClicked(e -> {
    if (e.getButton() == MouseButton.PRIMARY) {
        etiqueta.setText("Has hecho clic izquierdo");
    } else if (e.getButton() == MouseButton.SECONDARY) {
        etiqueta.setText("Has hecho clic derecho");
    }
});
```

#### 📦 `setOnMouseDragged`
Se activa al arrastrar el ratón sobre la escena.

```java
// arrastrar
escena.setOnMouseDragged(e -> {
    etiqueta.setText("Estás arrastrando el ratón. posición: X=" + e.getX() + ", Y = " + e.getY());
});
```

#### 🎡 `setOnScroll`
Este evento se dispara cuando se gira la rueda del ratón.

```java
// girar rueda
escena.setOnScroll(e -> {
    etiqueta.setText("Has girado la rueda. Cambio en Y: " + e.getDeltaY());
});
```

#### 📍 `setOnMouseMoved`
Este evento se activa cuando se mueve el ratón.

```java
// mover ratón
escena.setOnMouseMoved(e -> {
    etiqueta.setText("Estás moviendo el ratón. posición: X=" + e.getX() + ", Y = " + e.getY());
});
```

### ⌨️ Eventos de Teclado

#### 🎹 `setOnKeyPressed`
Detecta cuando una tecla ha sido pulsada.

```java
// Detectar tecla "Enter"
escena.setOnKeyPressed(evento -> {
    if (evento.getCode() == KeyCode.ENTER) {
        System.out.println("Se presionó Enter");
    }
});
```

#### 🎹 `setOnKeyReleased`
Este evento se activa cuando se suelta una tecla.

```java
// Detectar tecla "Espacio" liberada
escena.setOnKeyReleased(evento -> {
    if (evento.getCode() == KeyCode.SPACE) {
        System.out.println("Se soltó la barra espaciadora");
    }
});
```

### 🛠️ Combinaciones de Teclas

#### 🎹 Combinaciones Básicas
Se pueden detectar combinaciones de teclas como Control+S.

***Evento para detectar si se ha pulsado la combinación "CTRL+S"***
```java
// Detectar "Control + S"
escena.setOnKeyPressed(evento -> {
    if (evento.isControlDown() && evento.getCode() == KeyCode.S) {
        System.out.println("Se presionó Control + S");
    }
});
```


***Evento para detectar si se ha pulsado la combinación "CTRL+S" con*** ``KeyCombination``
```java
final KeyCombination combo = new KeyCodeCombination (KeyCode.S, KeyCombination.CONTROL_DOWN);
escena.addEventHandler (KeyEvent.KEY_PRESSED, evento -> {
	if(combo.match(evento)){
		System.out.println("Combinación CTRL + S detectada");
	}
})
```

***Evento para detectar se se ha pulsado la combinación "CTRL + SHIFT + K"***
```java
escena.setOnKeyPressed(evento -> {
    if (evento.isControlDown() && evento.isShiftDown() && evento.getCode() == KeyCode.K) {
        System.out.println("Se presionaron las teclas CTRL + SHIFT + K al mismo tiempo");
    }
});
```


#### 🎹 Combinaciones Avanzadas
Se puede comprobar si se han pulsado múltiples teclas a la vez mediante una colección `Set`.

```java
// Combinación de múltiples teclas
private final Set<KeyCode> teclasActivas = new HashSet<>();

@Override
public void start(Stage stage) {
	// ... creación de la escena -> escena
	escena.setOnKeyPressed(evento -> {
	    teclasActivas.add(evento.getCode());  // Añadir la tecla presionada al Set
	    if (teclasActivas.contains(KeyCode.A) && teclasActivas.contains(KeyCode.B) && 
	    teclasActivas.contains(KeyCode.C)) {
	        System.out.println("Las teclas A, B y C han sido presionadas");
	    }
	});
	escena.setOnKeyReleased(evento -> {
	    teclasActivas.remove(evento.getCode()); // Eliminar la tecla liberada del Set
	});
	// Resto del método start
}
```


___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #Eventos #ModeloDePropagación #TiposDeEventos #EventosDeRatón #EventosDeTeclado #EjemploPráctico #ClasesYSubclases #RegistroDeEventos #FiltradoDeEventos #ControlDeFlujo #BuenasPrácticas #Lambdas #SeparaciónDeLógica #Constantes #InterfacesGráficas
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%