---
ID: 24
nombre: Ubicación, Tamaño y Alineamiento
tags:
  - pagdesarrollo_de_interfaces
---
___
### 📐 Fundamentos de Propiedades en Controles

En JavaFX, la apariencia y el comportamiento de los controles, especialmente de los *Leaf Nodes*, se rigen por un conjunto de propiedades clave. Estas propiedades se heredan principalmente de dos clases superiores: `javafx.scene.layout.Region` y `javafx.scene.control.Control`.

#### 📏 Dimensiones de los Controles

- **Height**: Define la altura del control.
- **minHeight**: Establece la altura mínima que puede tener el control.
- **Width**: Indica la anchura del control.
- **minWidth**: Fija la anchura mínima del control.

#### 🌐 Espaciado y Alineamiento

- **Padding**: Este es el espacio que se deja entre el contenedor padre y el nodo hijo.

#### 🛠️ Acceso a Propiedades

Para acceder o modificar estas propiedades, se utilizan métodos específicos como `getHeight`, `getWidth`, `setHeight`, etc.

```java
// Ejemplo de cómo establecer la altura y la anchura de un control
Control myControl = new Control();
myControl.setHeight(100);
myControl.setWidth(200);
```

### 📍 Ubicación de los Controles

La ubicación de un control dentro de su contenedor padre es un aspecto crucial. Este posicionamiento se maneja de manera diferente según el tipo de contenedor en el que se encuentra el control.

### 🎨 Propiedades en Formas Geométricas

Las formas geométricas del paquete `javafx.scene.shape` también tienen propiedades similares. Sin embargo, algunas de estas propiedades pueden derivarse de otras características intrínsecas de la forma.

#### 📝 Ejemplo con Forma Geométrica

```java
// Ejemplo de cómo establecer propiedades en una forma geométrica
import javafx.scene.shape.Circle;

Circle circle = new Circle();
circle.setCenterX(100.0f);
circle.setCenterY(100.0f);
circle.setRadius(50.0f);
```

Este ejemplo muestra cómo establecer el centro y el radio de un círculo, lo que a su vez determina su tamaño y ubicación.


___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #Controles #LeafNodes #Propiedades #Dimensiones #Height #minHeight #Width #minWidth #Espaciado #Alineamiento #Padding #AccesoAPropiedades #UbicaciónDeControles #FormasGeométricas #EjemplosDeCódigo
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%