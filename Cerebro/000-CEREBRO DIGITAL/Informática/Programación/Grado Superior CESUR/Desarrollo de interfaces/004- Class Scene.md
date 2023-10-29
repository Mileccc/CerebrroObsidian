---
ID: 4
nombre: Class Scene
tags:
  - pagdesarrollo_de_interfaces
---
___

La clase Scene de JavaFX es un contenedor para el contenido en un gráfico de escena. Debe especificarse el nodo raíz. Puede controlar el tamaño de la escena y solicitar soporte de búfer de profundidad o antialiasing. También se agrega una luz predeterminada en ciertas condiciones. La modificación de la escena debe realizarse en el JavaFX Application Thread.

### Métodos más importantes Class Scene
1. `setRoot(Node root)`: Este método establece el nodo raíz para el gráfico de escena.

2. `getRoot()`: Devuelve el nodo raíz actualmente establecido en la escena.

3. `setFill(Paint fill)`: Establece el fondo de la escena con el color o relleno especificado.

4. `getWidth()`: Devuelve el ancho de la escena.

5. `getHeight()`: Devuelve la altura de la escena.

6. `getWindow()`: Devuelve la ventana a la que está adjunta la escena.

7. `setOnKeyPressed(EventHandler<? super KeyEvent> value)`: Permite establecer un manejador de eventos para eventos de teclado en la escena.

8. `setOnMouseClicked(EventHandler<? super MouseEvent> value)`: Permite establecer un manejador de eventos para eventos de clic del ratón en la escena.

9. `setOnMouseMoved(EventHandler<? super MouseEvent> value)`: Establece un manejador de eventos para eventos de movimiento del ratón en la escena.

10. `setCursor(Cursor value)`: Establece el cursor que se mostrará cuando el ratón esté sobre la escena.

11. `setCamera(Camera camera)`: Establece la cámara que se utilizará para la representación 3D en la escena.

12. `setDepthTest(DepthTest depthTest)`: Establece la prueba de profundidad para la escena en caso de representación 3D.

### Paquetes y clases mas importantes Class Scene

1. `javafx.scene.control`: Este paquete contiene controles de interfaz de usuario que a menudo se utilizan dentro de escenas, como botones, cuadros de texto y listas desplegables.

2. `javafx.scene.layout`: Aquí encontrarás clases para gestionar el diseño y la disposición de elementos dentro de una escena, como `Pane`, `HBox`, `VBox`, entre otros.

3. `javafx.scene.paint`: Este paquete contiene clases relacionadas con la pintura y el color en JavaFX, lo que incluye la clase `Paint` que se utiliza en la propiedad `fill` de una escena.

4. `javafx.scene.input`: Contiene clases para manejar eventos de entrada, como `MouseEvent` y `KeyEvent`, que son importantes para la interacción del usuario con la escena.

6. `javafx.scene.shape`: Este es el paquete principal que contiene la clase `Shape` y muchas otras clases relacionadas con formas geométricas 2D. Algunas de las subclases comunes de `Shape` incluyen `Rectangle`, `Circle`, `Ellipse`, `Line`, `Polygon`, `Polyline`, y más.

8. `javafx.scene.transform`: Aquí encontrarás clases para aplicar transformaciones a las formas, como rotaciones, escalas y traslaciones.



___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #Scene #Métodos #setRoot #getRoot #setFill #getWidth #getHeight #getWindow #setOnKeyPressed #setOnMouseClicked #setOnMouseMoved #setCursor #setCamera #setDepthTest #Paquetes  #javafx #JavaFXApplicationThread #NodoRaíz #EventosDeEntrada #Transformaciones #Layout #Colores #FormasGeométricas #3DRendering
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%