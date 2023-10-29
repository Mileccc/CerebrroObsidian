---
ID: 40
nombre: Ejercicio Lineas y Figuras
tags:
  - pagdesarrollo_de_interfaces
---
___
Este proyecto utiliza la biblioteca JavaFX para crear una pequeña aplicación de escritorio que muestra varias figuras geométricas y líneas. Aquí se analizará cada componente y su funcionalidad.

---

### Índice

1. [[#Estructura General]]
2. [[#Clase Principal o main App.java]]
3. [[#Controlador controlador.Java]]
4. [[#Vista vista.fxml]]
5. [[#Estilos style.css]]

---

### Estructura General

Antes de entrar en los detalles del código, es importante entender que estamos utilizando **JavaFX**, que es una biblioteca para crear interfaces gráficas de usuario en aplicaciones Java.

El proyecto está organizado en un patrón MVC (Modelo-Vista-Controlador), que separa la lógica de negocio, la interfaz de usuario y el control de la aplicación.

```plaintext
com.casopractico1
|-- App.java
|-- controlador.java
|-- vista.fxml
|-- style.css
```


---

## Clase Principal o main: App.java

`App.java` es el punto de entrada para la aplicación JavaFX. Este archivo es crucial para inicializar y mostrar la interfaz de usuario. 

---

### Herencia de la clase `Application`

```java
public class App extends Application {
    // ...
}
```

- `public class App extends Application`: Aquí, la clase `App` hereda de la clase `Application` de JavaFX. Esta herencia es crucial porque permite acceder al ciclo de vida de una aplicación JavaFX.

---

### El método `start()`

```java
@Override
public void start(Stage primaryStage) throws Exception {
    // ...
}
```

- `@Override public void start(Stage primaryStage)`: El método `start()` es el punto de entrada de todas las aplicaciones JavaFX. Se sobrescribe del método abstracto en la clase `Application`.
- `Stage primaryStage`: Este es el escenario (ventana) principal que el usuario verá.

---

### Creación de la escena

```java
Parent root = FXMLLoader.load(getClass().getResource("vista.fxml"));
Scene scene = new Scene(root, 600, 500);
```

- `Parent root = FXMLLoader.load(...)`: Esta línea carga el diseño de la UI desde el archivo `vista.fxml`.
- `Scene scene = new Scene(root, 600, 500)`: Crea una nueva escena y establece su tamaño a 600x500 píxeles.

---

### Añadiendo estilos

```java
scene.getStylesheets().add(getClass().getResource("/css/style.css").toExternalForm());
```

- `scene.getStylesheets().add(...)`: Añade la hoja de estilo CSS para decorar los componentes de la UI.

---

### Configurando y mostrando el `Stage`

```java
primaryStage.setTitle("Ejercicio de Manejo de Figuras");
primaryStage.setScene(scene);
primaryStage.show();
```

- `primaryStage.setTitle(...)`: Establece el título de la ventana.
- `primaryStage.setScene(scene)`: Asigna la escena creada al escenario principal.
- `primaryStage.show()`: Muestra el escenario. Es el último paso para que la aplicación sea visible.

---

### Método `main()`

```java
public static void main(String[] args) {
    launch(args);
}
```

- `public static void main(String[] args)`: El método `main()` es el punto de entrada de la aplicación Java en general.
- `launch(args)`: Este método está presente en la clase `Application` y se utiliza para lanzar la aplicación JavaFX.



---

## Controlador: controlador.Java

Este archivo desempeña un papel crítico en la manipulación de la lógica detrás de la interfaz de usuario de la aplicación JavaFX. A continuación, se analiza cada parte del código de forma detallada.

---


### Declaración de la Clase

```java
public class controlador {
    // Código
}
```

- `public class controlador`: Aquí se define la clase pública `controlador`, que contendrá toda la lógica para manipular los elementos de la interfaz gráfica.

---

### Declaraciones de Variables y Elementos FXML

```java
@FXML
private Group grupoLineas;
@FXML
private Group grupoGeometricas;
@FXML
private Line line1;
@FXML
private Line line2;
@FXML
private Line line3;
// ... (y así sucesivamente para otros elementos)
```

- `@FXML private Group grupoLineas;`: Esta línea declara una variable `grupoLineas` del tipo `Group`. La anotación `@FXML` indica que esta variable está vinculada a un elemento en el archivo `vista.fxml`. Similarmente, las otras variables con anotaciones `@FXML` también están vinculadas a elementos en `vista.fxml`.

---

### El Método `initialize()`

```java
@FXML
public void initialize() {
    // Código
}
```

- `@FXML public void initialize()`: Este método se llama automáticamente después de que todos los elementos de la interfaz gráfica se han cargado. Aquí es donde se pueden inicializar valores o realizar tareas que deben ejecutarse antes de que el usuario interactúe con la aplicación.

#### Inicialización de Listas

```java
List<String> listaColores = new ArrayList<>(Arrays.asList("RED","BLUE","GREEN","PINK","PURPLE","BROWN","BLACK","YELLOW","CYAN","LIME"));
List<Double> listaGrosores = new ArrayList<>(Arrays.asList(0.0,1.0,2.0,3.0,4.0,5.0,6.0,7.0,8.0,9.0));
```

- `List<String> listaColores` y `List<Double> listaGrosores`: Estas listas se inicializan con varios valores para colores y grosores, respectivamente. Estos valores se usarán más tarde para configurar las propiedades de las líneas generadas.

#### Bucle For para Generar Líneas
Podríamos generar todas las lineas directamente en el archivo de ``vistas.fxml`` pero decidí usar esta parte para mostrar la generación de lineas automáticas con la necesidad de solo cambiar el valor de la variable numLineas.

```java
Integer numLineas = 5;
for (int i = 1; i <= numLineas; i++) {
    Line newLine = new Line();
    newLine.setStartX(line1.getStartX());
    newLine.setStartY(line1.getStartY() + i * 10);
    newLine.setEndX(line1.getEndX());
    newLine.setEndY(line1.getEndY() + i * 10);
    int colorIndex = i % listaColores.size();
    int grosorIndex = i % listaGrosores.size();
    newLine.setStroke(Color.valueOf(listaColores.get(colorIndex)));
    newLine.setStrokeWidth(listaGrosores.get(grosorIndex));
    grupoLineas.getChildren().add(newLine);
}
```

- `for (int i = 1; i <= 5; i++)`: Un bucle que se ejecuta 5 veces para generar 5 líneas.
- `Line newLine = new Line()`: Crea una nueva instancia de la clase `Line` para cada iteración del bucle.
- `newLine.setStartX(line1.getStartX());`, `newLine.setStartY(line1.getStartY() + i * 10)`, etc.: Estas funciones configuran las coordenadas de inicio y fin de la línea. Se usa la línea existente `line1` como referencia.
- `int colorIndex = i % listaColores.size();` y `int grosorIndex = i % listaGrosores.size();`: Calcula los índices para los colores y grosores utilizando el operador de módulo.
- `newLine.setStroke(Color.valueOf(listaColores.get(colorIndex)));` y `newLine.setStrokeWidth(listaGrosores.get(grosorIndex));`: Establece el color y el grosor de la línea.
- `grupoLineas.getChildren().add(newLine);`: Esta línea añade la nueva instancia de `Line` al grupo de líneas `grupoLineas`, que es un nodo en la interfaz gráfica. Esencialmente, esto hace que la nueva línea sea visible en la interfaz de usuario.

---

Este método `initialize()` es fundamental para el funcionamiento de la aplicación. No sólo inicializa las listas de colores y grosores que se utilizarán más tarde, sino que también crea dinámicamente nuevas líneas basadas en la línea de referencia `line1`, aplicándoles colores y grosores de las listas previamente inicializadas.


## Vista: vista.fxml

El archivo `vista.fxml` es un archivo XML que define la interfaz gráfica de usuario (GUI) para la aplicación JavaFX. A continuación, se realiza un análisis paso a paso de cada sección de este archivo.

---

### Estructura General

```xml
<?xml version="1.0" encoding="UTF-8"?>
```

- **`<?xml version="1.0" encoding="UTF-8"?>`**: Esta línea declara que el archivo es un documento XML y especifica la versión y la codificación utilizadas.

```xml
<BorderPane xmlns="http://javafx.com/javafx" xmlns:fx="http://javafx.com/fxml"
   fx:controller="com.casopractico1.controlador">
   <!-- Contenido -->
</BorderPane>
```

- **`<BorderPane xmlns="http://javafx.com/javafx" xmlns:fx="http://javafx.com/fxml" fx:controller="com.casopractico1.controlador">`**: Aquí se declara el elemento raíz `BorderPane`, que es un tipo de panel que permite un diseño flexible. También se define el espacio de nombres y el controlador asociado.

---

### Elementos de Diseño

Dentro del `BorderPane`, hay varios grupos y formas que componen la interfaz gráfica.

#### Grupo de Líneas

```xml
<top>
  <Group fx:id="grupoLineas">
     <Line fx:id="line1" styleClass="linea1" startX="1" startY="50" endX="150" endY="150" />
     <!-- ... -->
  </Group>
</top>
```

- **`<top>`**: Este elemento define la región superior del `BorderPane`.
- **`<Group fx:id="grupoLineas">`**: Declara un grupo para contener líneas. Este grupo está vinculado al controlador mediante la anotación `fx:id`.
- **`<Line fx:id="line1" styleClass="linea1" startX="1" startY="50" endX="150" endY="150" />`**: Define una línea con un ID y una clase de estilo, además de las coordenadas de inicio y fin.

#### Grupo Geométrico

```xml
<bottom>
  <Group fx:id="grupoGeometricas">
     <Polygon fx:id="penta1" styleClass="poligono1"
        points="100.0,50.0, 130.0,90.0, 120.0,130.0, 80.0,130.0, 70.0,90.0 " scaleX="2.0" scaleY="1.5" />
     <!-- ... -->
  </Group>
</bottom>
```

- **`<bottom>`**: Este elemento define la región inferior del `BorderPane`.
- **`<Group fx:id="grupoGeometricas">`**: Similar al grupo de líneas, este grupo contendrá las formas geométricas.
- **`<Polygon fx:id="penta1" styleClass="poligono1" points="..." scaleX="2.0" scaleY="1.5">`**: Define un polígono con un ID, una clase de estilo y varios puntos que forman la figura.

#### Transformaciones

Las transformaciones como `scaleX`, `scaleY`, `translateX`, y `rotate` son muy útiles para modificar elementos gráficos en JavaFX sin alterar sus propiedades básicas. Por ejemplo, puedes rotar un rectángulo sin tener que recalcular todas sus coordenadas. Esto hace que las transformaciones sean herramientas poderosas para el diseño gráfico dinámico.

```java
<Polygon ... scaleX="2.0" scaleY="1.5" />
<Circle ... translateX="300" />
<Rectangle ... rotate="45" />
```

#### Estilos

La propiedad `styleClass` en cada elemento (como `styleClass="linea1"`) permite vincular la forma con las definiciones de estilo en el archivo `style.css`.

---


## Estilos: style.css

### Introducción

El archivo `style.css` es utilizado para definir los estilos aplicados a los elementos gráficos de nuestra aplicación JavaFX. Cada selector CSS define un conjunto de reglas de estilo que se aplican a los elementos con la `styleClass` correspondiente en el archivo FXML.

---

### Estilos para las Líneas

```css
/* Definir el estilo para las líneas */
.linea1 {
    -fx-stroke: blue;
    -fx-stroke-width: 5;
}
.linea2 {
    -fx-stroke: red;
    -fx-stroke-width: 3;
}
.linea3 {
    -fx-stroke: pink;
    -fx-stroke-width: 2;
}
```

- **`.linea1`, `.linea2`, `.linea3`**: Estos son selectores de clase CSS que corresponden a las `styleClass` definidas para las líneas en el archivo `vista.fxml`.

- **`-fx-stroke`**: Define el color de la línea.

- **`-fx-stroke-width`**: Define el grosor de la línea.

En resumen, tenemos tres tipos de líneas con colores y grosores específicos: azul con un grosor de 5, rojo con un grosor de 3 y rosa con un grosor de 2.

### Estilos para las Figuras Geométricas

```css
/* Definir el estilo para los polígonos */
.poligono1 {
    -fx-fill: purple;
}

/* Definir el estilo para los círculos */
.circulo1 {
    -fx-fill: yellow;
}

/* Definir el estilo para los rectángulos */
.cuadrado1 {
    -fx-fill: orange;
}
```

- En esta sección, definimos los estilos para tres tipos de figuras geométricas: un polígono (pentágono), un círculo y un rectángulo (cuadrado). Cada figura geométrica tiene su propio selector de clase `.poligono1`, `.circulo1`, y `.cuadrado1`, que se corresponden con las `styleClass` definidas para estas figuras en el archivo `vista.fxml`.

- **`-fx-fill`**: Esta es la propiedad de estilo común entre estas figuras geométricas. Se utiliza para definir el color de relleno de cada figura.


Con esta sección, hemos definido estilos específicos para cada figura geométrica, lo cual facilita el mantenimiento y la comprensión del código.

## Resultado de ejecución

![[Pasted image 20231021172157.png]]

___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #MVC #AplicaciónDeEscritorio #UI #Herencia #FXML #CSS #Escena #Stage #Inicialización #GeneraciónDinámica #Líneas #FigurasGeométricas #PatronesDeDiseño #Transformaciones #XML
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%