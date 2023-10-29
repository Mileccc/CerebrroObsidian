---
ID: 23
nombre: Propiedades Comunes en Componentes
tags:
  - pagdesarrollo_de_interfaces
---
___
### 📏 Propiedades de Tamaño, Ubicación y Alineamiento

Estas propiedades son fundamentales para determinar cómo se visualizará un componente en la interfaz. Son aplicables a una amplia gama de componentes, incluidos contenedores, branch nodes y leaf nodes. Sin embargo, su interpretación puede variar según el contexto en el que se encuentren.

#### Contexto de Aplicación

- **Contenedores**: En el caso de contenedores, estas propiedades determinan cómo se distribuirán los elementos hijos dentro del contenedor.
- **Branch Nodes y Leaf Nodes**: Para estos nodos, las propiedades definen su tamaño y posición relativa dentro del contenedor padre.

#### Ejemplo de Código en JavaFX

```java
// Establecer el tamaño y la posición de un botón
Button btn = new Button("Click Me");
btn.setLayoutX(50);
btn.setLayoutY(50);
btn.setPrefSize(100, 20);
```

### 🎨 Propiedades Relacionadas con el Color

Estas propiedades permiten personalizar la apariencia visual de los componentes. Al igual que las propiedades de tamaño y ubicación, son aplicables tanto a contenedores como a nodos finales.

#### Aspectos Personalizables

- **Fondo**: Color o imagen de fondo del componente.
- **Borde**: Color y estilo del borde.
- **Patrón**: Patrones de color o textura.

#### Ejemplo de Código en JavaFX

```java
// Establecer el color de fondo y el borde de un panel
Pane panel = new Pane();
panel.setStyle("-fx-background-color: #FFFFFF; -fx-border-color: #000000;");
```

### 🌳 Propiedades de Posición y Dependencia en el Árbol de Nodos

Estas propiedades son cruciales para entender la relación entre los diferentes nodos en la estructura arborescente de una escena.

#### Aspectos a Considerar

- **Padre**: Nodo al que pertenece el componente.
- **Hijos**: Nodos que están contenidos dentro del componente.

#### Ejemplo de Código en JavaFX

```java
// Añadir un nodo hijo a un contenedor padre
Pane root = new Pane();
Button btn = new Button("Click Me");
root.getChildren().add(btn);
```

### 🛠️ Propiedades Específicas de los Componentes

Además de las propiedades comunes, cada tipo de componente puede tener propiedades específicas que le son inherentes. Por ejemplo, un botón podría tener propiedades relacionadas con el evento de clic, mientras que un campo de texto podría tener propiedades relacionadas con la validación de entrada.

#### Ejemplo de Código en JavaFX

```java
// Establecer una acción al hacer clic en un botón
Button btn = new Button("Click Me");
btn.setOnAction(e -> System.out.println("Button clicked"));
```


___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #PropiedadesComunes #Tamaño #Ubicación #Alineamiento #Color #Posición #Dependencia #ÁrbolDeNodos #ComponentesEspecíficos #Contenedores #BranchNodes #LeafNodes #CódigoEjemplo
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%