---
ID: 20
nombre: Explorando Componentes Contenedores de Controles
tags:
  - pagdesarrollo_de_interfaces
---
___

### 🌐 Introducción al Paquete `javafx.graphics`

El paquete `javafx.graphics` es el núcleo de la escenografía en OpenJFX. Este paquete es como el escenario donde se desarrolla toda la acción. Aquí es donde se definen elementos cruciales como:

- Layouts y contenedores
- Ciclo de vida de una aplicación
- Transformaciones y canvas
- Entrada y dibujo
- Manejo de imágenes y efectos
- Animaciones y CSS

```java
// Importando el paquete javafx.graphics
import javafx.graphics.*;
```

### 📦 Contenedores y Layouts en `javafx.scene.layout`

Dentro del paquete `javafx.graphics`, encontramos un subpaquete llamado `javafx.scene.layout`. Este subpaquete es el que contiene las clases que nos permiten organizar los controles y otros elementos en la interfaz de usuario. 

#### 🎨 Tipos de Contenedores (`Pane Classes`)

Los contenedores, también conocidos como `Pane Classes`, son los que definen cómo se organizan los controles hijos. Cada tipo de contenedor tiene su propio estilo y reglas para organizar los controles. Aquí hay una lista de las clases de contenedores más comunes:

1. **Pane**: 
   - *Uso*: Clase base para todos los demás contenedores.
   - *Características*: Permite una lista pública de controles hijos, lo que facilita la adición o eliminación de controles.

```java
// Ejemplo de uso de Pane
Pane root = new Pane();
```

2. **BorderPane**: 
   - *Uso*: Organiza elementos en posiciones fijas como top, left, right, bottom o center.
   
```java
// Ejemplo de uso de BorderPane
BorderPane borderPane = new BorderPane();
```

3. **FlowPane**: 
   - *Uso*: Los elementos fluyen de acuerdo con las características del contenedor.

```java
// Ejemplo de uso de FlowPane
FlowPane flowPane = new FlowPane();
```

4. **GridPane**: 
   - *Uso*: Organiza elementos en una matriz de filas y columnas.

```java
// Ejemplo de uso de GridPane
GridPane gridPane = new GridPane();
```

5. **StackPane**: 
   - *Uso*: Organiza elementos en capas, uno encima del otro.

```java
// Ejemplo de uso de StackPane
StackPane stackPane = new StackPane();
```

6. **TilePane**: 
   - *Uso*: Distribuye los elementos de manera uniforme en una matriz.

```java
// Ejemplo de uso de TilePane
TilePane tilePane = new TilePane();
```

7. **AnchorPane**: 
   - *Uso*: Permite anclar elementos a los márgenes del contenedor.

```java
// Ejemplo de uso de AnchorPane
AnchorPane anchorPane = new AnchorPane();
```

#### 🛠️ Trabajando con Contenedores

Los contenedores en JavaFX trabajan como una especie de árbol de nodos. Puedes añadir o eliminar nodos, y el contenedor se encargará de organizarlos automáticamente. Esto incluye redimensionar y recolocar los nodos según las reglas del contenedor.

```java
// Añadiendo un nodo a un contenedor
Pane root = new Pane();
Button myButton = new Button("Click Me");
root.getChildren().add(myButton);
```

___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #OpenJFX #javafxgraphics #Contenedores #Layouts #PaneClasses #Pane #BorderPane #FlowPane #GridPane #StackPane #TilePane #AnchorPane #CicloDeVida #Transformaciones #Canvas #Entrada #Dibujo #Imágenes #Efectos #Animaciones #CSS
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%