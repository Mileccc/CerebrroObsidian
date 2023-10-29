---
ID: 38
nombre: Uso de CSS
tags:
  - pagdesarrollo_de_interfaces
---
___
## 🎨 Introducción a la Utilización de CSS en JavaFX

![](https://www.youtube.com/watch?v=8Rv4SHZ-9xM&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=217&ab_channel=Aulaenlanube)

### 🎮 ¿Qué es CSS y por qué usarlo en JavaFX?

CSS, o *Cascading Style Sheets*, es un lenguaje de hojas de estilo utilizado para describir la presentación de un documento escrito en HTML o XML. En el contexto de JavaFX, CSS nos permite estilizar y mejorar la apariencia visual de la interfaz de usuario de nuestras aplicaciones.

### 🛠 Principales Selectores CSS en JavaFX

En CSS, los selectores son patrones que determinan qué elementos del documento serán seleccionados para aplicar estilos. Los dos principales selectores que vamos a tratar son:

1. ***Selector de tipo:*** Se aplica a todos los componentes de un tipo específico.
   ```css
   Button {
     /* Propiedades */
   }
   ```
2. ***Selector de ID:*** Se aplica al componente que tiene un ID específico.
   ```css
   #myButton {
     /* Propiedades */
   }
   ```

### 🎨 Propiedades CSS Comunes

Algunas de las propiedades CSS que comúnmente se utilizan en JavaFX para modificar el diseño de componentes son:

- `color`: Define el color del texto
- `font-size`: Establece el tamaño del texto
- `border`: Modifica los bordes del componente

```css
Button {
  color: red;
  font-size: 16px;
  border: 1px solid black;
}
```

### 🌐 Asociar un Fichero CSS a una Escena de JavaFX

Para aplicar los estilos de un fichero CSS externo a una escena en JavaFX, podemos hacer lo siguiente:

```java
Scene scene = new Scene(root, 400, 400);
scene.getStylesheets().add("myStyles.css");
```

### 📌 Estilos en Línea en JavaFX

Si no deseamos utilizar un fichero CSS externo, también podemos aplicar estilos en línea directamente en el código Java:

```java
Button button = new Button("Click Me");
button.setStyle("-fx-background-color: blue;");
```

### 📚 Ejemplo de Uso de CSS en una Aplicación con Interfaz Diseñada en FXML

En el siguiente ejemplo, mostramos cómo combinar el uso de CSS con una interfaz diseñada utilizando FXML.

```java
FXMLLoader loader = new FXMLLoader(getClass().getResource("myLayout.fxml"));
Parent root = loader.load();
Scene scene = new Scene(root);
scene.getStylesheets().add("myStyles.css");
```

En este caso, tanto la interfaz como los estilos se definen externamente, y luego se cargan en el código Java para ser utilizados.

___
## 🎨 Profundizando en el Uso de CSS en JavaFX

### 📚 Detalles sobre CSS en JavaFX

#### 📍 Asociando un Archivo CSS a una Escena o Componente 

Para asociar una hoja de estilo a una escena en JavaFX, puedes usar el método `getStylesheets().add()`. Es vital colocar el archivo CSS en la carpeta `resources` del proyecto. Aquí hay un ejemplo:

```java
Scene scene = new Scene(root);
scene.getStylesheets().add(getClass().getResource("archivo.css").toExternalForm());
```

#### 🌟 Selectores CSS en JavaFX

En JavaFX, se utilizan selectores similares a los que se emplean en CSS para páginas web. Los más comunes son:

1. ***Selector de clase (.nombreClase):*** Aplica el estilo a todos los componentes que pertenecen a una clase específica.
   ```css
   .boton-personalizado {
     -fx-background-color: #3498db;
     -fx-text-fill: white;
   }
   ```
2. ***Selector de ID (#IDnombre):*** Aplica el estilo solo al componente con el ID especificado.
   ```css
   #texto-destacado {
     -fx-font-size: 20px;
     -fx-font-weight: bold;
   }
   ```
   
#### 🤖 Aplicando Clases e IDs en Java

Para aplicar una clase o un ID a un componente en JavaFX, puedes hacerlo de la siguiente manera:

- **Aplicar Clase:**
  ```java
  Button boton = new Button("Haz clic en mí");
  boton.getStyleClass().add("boton-personalizado");
  ```
  
- **Aplicar ID:**
  ```java
  Text texto = new Text("Texto destacado");
  texto.setId("texto-destacado");
  ```

#### 📜 Propiedades de Estilo

Las propiedades CSS que se aplican a los componentes en JavaFX suelen tener el prefijo `-fx-`. Por ejemplo:

```css
-fx-background-color: red;
-fx-font-size: 20px;
```

### 📝 Notas Finales

En resumen, aunque JavaFX utiliza una sintaxis de CSS que es muy similar a la usada en diseño web, hay algunas diferencias clave, como el prefijo `-fx-` en las propiedades de estilo. Con estos fundamentos, se pueden personalizar componentes de forma efectiva y eficiente en aplicaciones JavaFX.

___
## 🌈 JavaFX y CSS: Entendiendo los Estilos por Defecto

### 📝 Introducción
En la programación con JavaFX, una de las potentes características es el uso de hojas de estilo en cascada (CSS) para personalizar la apariencia de los componentes de la interfaz de usuario. Aquí se explorará cómo aplicar estilos por defecto a componentes específicos como `Label`, `Button` y `Text`.

### 🎨 Estilos por Defecto para Componentes Específicos

#### 🏷️ Labels
Para definir un estilo por defecto para todos los componentes de tipo `Label`, simplemente incluimos el selector del `Label` en nuestra hoja de estilo CSS.

```css
Label {
  -fx-text-fill: #2c3e50; 
  -fx-font-size: 14px;
}
```
Con este CSS, cualquier `Label` creado en una escena asociada a esta hoja de estilo tendrá un tamaño de letra de 14 píxeles y el color especificado.

#### 🖲️ Botones
De manera similar, para los botones, podemos definir un conjunto de propiedades que todos los botones heredarán.

```css
Button {
  -fx-background-color: #3498db; 
  -fx-text-fill: white;
  -fx-border-radius: 5px;
  -fx-background-radius: 5px; 
  -fx-padding: 5px 15px;
}
```
Si creamos botones en la misma escena, heredarán estas características automáticamente.

### 🌐 Clases Adicionales y Prioridad
Es posible añadir clases adicionales a componentes individuales para alterar su estilo. Por ejemplo, se podría tener una clase llamada `etiqueta-especial` que cambia el color del texto a rojo.

```css
.etiqueta-especial {
  -fx-text-fill: red;
}
```
Utilizando el método `getStyleClass().add`, podemos añadir esta clase adicional a un `Label`. Este tendrá prioridad sobre el estilo por defecto.

```java
label.getStyleClass().add("etiqueta-especial");
```

### 🔄 Combinación y Anulación de Estilos
Aunque los componentes tendrán un estilo por defecto, también se pueden modificar manualmente. Si definimos la misma propiedad en ambas clases, la clase añadida tendrá prioridad. Por ejemplo, si el `Label` tiene un color por defecto y se le añade la clase `etiqueta-especial`, el color cambiará a rojo pero mantendrá el tamaño original de 14 píxeles.

___
## 🎨 Estilos en Línea en CSS 

### 🛠️ Método `setStyle`

El método `setStyle` permite aplicar estilos en línea directamente a un componente en JavaFX. Estos estilos tienen la máxima prioridad, anulando cualquier estilo proveniente de una hoja de estilo CSS externa.

```java
b1.setStyle("-fx-background-color: red; -fx-text-fill: white;");
```

### ⚖️ Prioridad de los Estilos

1. **Estilo en Línea**: Si usas `setStyle`, ese estilo tendrá la máxima prioridad.
2. **Clases CSS Externas**: Menor prioridad si se ha aplicado un estilo en línea al mismo componente.

### 📝 Ejemplo Práctico 

Imaginemos un archivo CSS externo que aplica estilos a botones:

```css
.button {
  -fx-background-color: green;
  -fx-text-fill: white;
  -fx-border-radius: 5px;
  -fx-background-radius: 5px;
  -fx-padding: 10px 20px;
}

.button-special {
  text-fill: red;
}
```

#### 🖲️ Creación de Botones

Creamos 4 botones: B1, B2, B3, y B4 con los textos "Pulsa 1", "Pulsa 2", "Pulsa 3" y "Pulsa 4" respectivamente.

```java
Button b1 = new Button("Pulsa 1");
Button b2 = new Button("Pulsa 2");
Button b3 = new Button("Pulsa 3");
Button b4 = new Button("Pulsa 4");
```

#### 🎯 Aplicación de Estilos

- **Botón B1**: Usando `setStyle`, cambiamos su color de fondo a rojo y el color del texto a blanco.
  
```java
b1.setStyle("-fx-background-color: red; -fx-text-fill: white;");
```

- **Botón B2**: Añadimos la clase `button-special`, lo cual cambia su texto a rojo pero mantiene el resto de estilos.

```java
b2.getStyleClass().add("button-special");
```

- **Botón B3**: Utilizamos `setStyle` para establecer el color de fondo a azul, y luego añadimos la clase `button-special` para cambiar el color del texto a rojo.

```java
b3.setStyle("-fx-background-color: blue;");
b3.getStyleClass().add("button-special");
```

- **Botón B4**: No modificamos este botón, por lo que tendrá los estilos definidos en la hoja de estilo externa.

### ⚠️ Consideraciones

Aunque el uso de `setStyle` para definir estilos en línea es posible, no es recomendable, especialmente en aplicaciones grandes con múltiples componentes. Esto puede dificultar el mantenimiento y dar lugar a errores difíciles de detectar.

Es más efectivo y mantenible definir estilos en archivos CSS externos, lo cual también facilita la reutilización de código.

___
%%
tags: #pagdesarrollo_de_interfaces #CSS #JavaFX #SelectoresCSS #PropiedadesCSS #FicheroCSS #EstilosEnLínea #FXML #DetallesCSS #ClasesIDsJava #PrefijoFx #EstilosPorDefecto #PrioridadEstilos #MétodoSetStyle #Consideraciones
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%