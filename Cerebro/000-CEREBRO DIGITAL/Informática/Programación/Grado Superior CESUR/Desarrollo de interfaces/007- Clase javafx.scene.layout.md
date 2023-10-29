---
ID: 7
nombre: Clase javafx.scene.layout
tags:
  - pagdesarrollo_de_interfaces
---
___
## .layout
#### Clase javafx.scene.layout
El paquete `javafx.scene.layout` en JavaFX proporciona un conjunto de clases que te ayudan a gestionar la disposición y el diseño de los elementos gráficos en una interfaz de usuario. Esto es esencial para crear interfaces de usuario más complejas y controlar cómo se distribuyen y organizan los nodos gráficos en una escena. Aquí tienes información sobre algunos de los métodos y clases más importantes en este paquete:

**Clases Principales**:

1. `Pane`: `Pane` es una clase abstracta que es la base para varios tipos de contenedores de diseño en JavaFX, como `AnchorPane`, `BorderPane`, `HBox`, `VBox`, y más. Proporciona métodos para agregar y organizar nodos secundarios en un diseño.

2. `Region`: `Region` es una subclase de `Pane` que se utiliza para crear contenedores de diseño más avanzados con capacidades de gestión de tamaño y estilo más completas. Proporciona propiedades y métodos para controlar la apariencia y el comportamiento de la región.

3. `HBox` y `VBox`: Estos son contenedores de diseño horizontal (`HBox`) y vertical (`VBox`) respectivamente. Se utilizan para organizar nodos secundarios en una fila (horizontal) o columna (vertical). Puedes agregar nodos secundarios a estos contenedores y controlar su alineación y relleno.

4. `BorderPane`: `BorderPane` divide su área en cinco regiones: superior, inferior, izquierda, derecha y centro, lo que facilita la creación de diseños tipo marco (frame-like) comunes en aplicaciones.

5. `GridPane`: `GridPane` permite organizar nodos secundarios en una cuadrícula de filas y columnas. Es útil para crear diseños tabulares y complejos.

6. `AnchorPane`: `AnchorPane` permite posicionar nodos secundarios en relación con las esquinas o bordes del contenedor utilizando anclajes (anclajes de arriba, abajo, izquierda, derecha, etc.).

**Métodos y Propiedades Importantes**:

1. `getChildren()`: Todos los contenedores de diseño en este paquete tienen un método `getChildren()` que devuelve una lista observable de nodos secundarios. Puedes usar este método para agregar, eliminar y manipular nodos en el diseño.

2. Propiedades de restricción de tamaño: Muchas clases de diseño en este paquete proporcionan propiedades para controlar la restricción de tamaño de sus nodos secundarios. Estas propiedades incluyen `minWidth`, `minHeight`, `prefWidth`, `prefHeight`, `maxWidth`, y `maxHeight`.

3. Propiedades de alineación y espaciado: Los contenedores de diseño también proporcionan propiedades relacionadas con la alineación y el espaciado de sus nodos secundarios, como `alignment`, `spacing`, y `margin`.

En resumen, el paquete `javafx.scene.layout` en JavaFX es fundamental para crear interfaces de usuario con diseños complejos y controlar cómo se organizan y presentan los elementos gráficos. Las clases y métodos mencionados anteriormente te permiten crear diseños flexibles y personalizados para tus aplicaciones JavaFX.


___
%%
tags:  #pagdesarrollo_de_interfaces 
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%