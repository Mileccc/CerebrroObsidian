---
ID: 22
nombre: Manipulación de Componentes en Interfaces JavaFX
tags:
  - pagdesarrollo_de_interfaces
---
___
### 🌳 Entendiendo la Estructura de la Escena en OpenJFX

Una aplicación en OpenJFX se compone de un escenario principal, representado por la clase `Stage`. Dentro de este escenario, se dibuja una `Scene`, que actúa como una estructura arborescente de datos. En esta estructura:

- Cada elemento, o nodo, puede tener un padre y cero, uno o varios hijos.
- Un nodo sin hijos se considera una "hoja" (`Leaf Node`).
- Un nodo con hijos se considera una "rama" (`Branch Node`).

#### 📚 Clases Principales

1. **Scene**
   - *Responsabilidad*: Define la escena que se dibujará en el escenario (`Stage`).
   - *Relación*: Siempre se dibuja dentro de un `Stage`.

2. **Node**
   - *Responsabilidad*: Actúa como el elemento base en la estructura arborescente de la escena.
   - *Tipos*: Puede ser una "hoja" si no tiene hijos o una "rama" si tiene hijos.
   - *Root Node*: El nodo sin padres se denomina "root".

#### 🌲 Tipos de Nodos

1. **Branch Nodes**
   - *Herencia*: Heredan de `javafx.scene.Parent`.
   - *Características*: Contienen hijos.

2. **Leaf Nodes**
   - *Ejemplos*: `Rectangle`, `Text`, `Line`.
   - *Características*: No pueden tener hijos.

### 🎨 Añadir y Eliminar Elementos en la Escena

Para manipular elementos en una escena, se utiliza una clase que actúa como un contenedor de nodos, como `Group`.

#### 📝 Ejemplo de Uso de la Clase `Group`

```java
@Override public void start(Stage stage) {
  Group root = new Group();
  Scene scene = new Scene(root, 200, 150);
  scene.setFill(Color.LIGHTGRAY);
  
  Circle circle = new Circle(60, 40, 30, Color.GREEN);
  Text text = new Text(10, 90, "JavaFX Scene");
  text.setFill(Color.DARKRED);
  Font font = new Font(20);
  text.setFont(font);
  
  root.getChildren().add(circle);
  root.getChildren().add(text);
  
  stage.setScene(scene);
  stage.show();
}
```

#### 🛠️ Métodos para Manipular Nodos en `Group`

- `getChildren()`: Devuelve un `ObservableList` de nodos (`javafx.scene.Node`).
- `add()`: Permite añadir un nuevo nodo al `ObservableList`.

Con estos métodos, se pueden añadir y eliminar elementos de la escena de manera dinámica, lo que permite una interacción más rica con el usuario.


___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #OpenJFX #Stage #Scene #Node #LeafNode #BranchNode #Group #ObservableList #ManipulaciónDeComponentes #EstructuraDeEscena #AñadirElementos #EliminarElementos #InteracciónUsuario
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%