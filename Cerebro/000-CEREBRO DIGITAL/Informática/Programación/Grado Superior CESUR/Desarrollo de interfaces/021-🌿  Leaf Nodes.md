---
ID: 21
nombre: Leaf Nodes
tags:
  - pagdesarrollo_de_interfaces
---
___

### 🎨 Introducción a Leaf Nodes en OpenJFX

Los Leaf Nodes son los componentes gráficos fundamentales que se pueden añadir a una aplicación OpenJFX para hacerla interactiva. Estos componentes se pueden dividir en dos categorías principales: formas _geométricas_ y _controles_ de usuario. Ambas categorías se describen mediante ficheros FXML y controladores para su carga.

#### 📐 Formas Geométricas en `javafx.scene.shape`

Este paquete es uno de los pilares básicos en OpenJFX para la creación de elementos gráficos. Las clases más comunes que encontramos aquí son:

1. **Line**
   - **Descripción**: Representa una línea en el espacio 2D.
   - **Propiedades**: Coordenadas x, y.
   ```java
   Line line = new Line(0, 0, 100, 100);
   ```

2. **Rectangle**
   - **Descripción**: Define un rectángulo.
   - **Propiedades**: Array de segmentos.
   ```java
   Rectangle rectangle = new Rectangle(50, 50, 100, 100);
   ```

3. **Circle**
   - **Descripción**: Crea un círculo 2D.
   - **Propiedades**: Radio, centro x, centro y.
   ```java
   Circle circle = new Circle(50, 50, 30);
   ```

4. **Ellipse**
   - **Descripción**: Crea una elipse 2D.
   - **Propiedades**: Radios horizontal y vertical, centro x, centro y.
   ```java
   Ellipse ellipse = new Ellipse(50, 50, 30, 40);
   ```

5. **Polygon**
   - **Descripción**: Crea un polígono.
   - **Propiedades**: Array de coordenadas x, y.
   ```java
   Polygon polygon = new Polygon(0, 0, 50, 30, 10, 60);
   ```

#### 🎛️ Controles de Usuario en `javafx.scene.control`

Este paquete es esencial para la interacción con el usuario. Algunos de los controles más comunes son:

1. **Button**
   - **Descripción**: Botón clickeable.
   ```java
   Button button = new Button("Click Me");
   ```

2. **CheckBox**
   - **Descripción**: Control con tres estados.
   ```java
   CheckBox checkBox = new CheckBox("Accept Terms");
   ```

3. **ColorPicker**
   - **Descripción**: Selector de color.
   ```java
   ColorPicker colorPicker = new ColorPicker();
   ```

4. **Label**
   - **Descripción**: Muestra texto no editable.
   ```java
   Label label = new Label("Hello, World");
   ```

5. **Menu, MenuBar, MenuItem**
   - **Descripción**: Controles para menús.
   ```java
   Menu menu = new Menu("File");
   MenuBar menuBar = new MenuBar();
   MenuItem menuItem = new MenuItem("Open");
   ```

6. **TextArea**
   - **Descripción**: Área de texto multicolumna y fila.
   ```java
   TextArea textArea = new TextArea();
   ```

### 🤔 Diferencias entre Formas Geométricas y Controles de Usuario

Las formas geométricas (`javafx.scene.shape`) son elementos gráficos básicos que se utilizan para dibujar y representar objetos en la escena. Por otro lado, los controles de usuario (`javafx.scene.control`) son elementos interactivos que permiten la interacción del usuario con la aplicación, como hacer clic en un botón o seleccionar una opción en un menú desplegable.

Ambos tipos de componentes son Leaf Nodes, pero mientras las formas geométricas son más estáticas y se utilizan para la representación gráfica, los controles de usuario son dinámicos y se utilizan para la interacción en tiempo real.

___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #LeafNodes #OpenJFX #FXML #Controladores #FormasGeométricas #javafxsceneshape #Line #Rectangle #Circle #Ellipse #Polygon #ControlesDeUsuario #javafxscenecontrol #Button #CheckBox #ColorPicker #Label #Menu #MenuBar #MenuItem #TextArea #InteracciónUsuario #ComponentesGráficos #ElementosInteractivos #ElementosEstáticos
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%