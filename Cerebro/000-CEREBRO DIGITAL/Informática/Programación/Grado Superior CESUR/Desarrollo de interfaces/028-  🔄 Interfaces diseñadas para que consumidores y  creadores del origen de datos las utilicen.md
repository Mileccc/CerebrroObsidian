---
ID: 28
nombre: " Interfaces diseñadas para que consumidores y \rcreadores del origen de datos las utilicen"
tags:
  - pagdesarrollo_de_interfaces
---
___
### 🎛️ La Conexión entre Controles y Datos

En el paradigma de desarrollo de interfaces de usuario con JavaFX, los controles son elementos clave que permiten la interacción con el usuario. Estos controles pueden estar vinculados a un modelo de datos o a un origen de datos específico, lo que facilita la presentación y manipulación de la información.

#### 📊 TableView: El Control Estrella en JavaFX

![[Pasted image 20231017193246.png|1200]]

Uno de los controles más versátiles y ampliamente utilizados en JavaFX es el `TableView`. Este control es especialmente útil para presentar datos en forma de tabla. En JavaFX, se le conoce como `javafx.scene.control.TableView<S>`, donde `S` es un tipo genérico que representa el tipo de objetos que la tabla contendrá.

##### 📝 Ejemplo de Uso de TableView

Para ilustrar cómo funciona `TableView`, consideremos el siguiente fragmento de código:

```java
TableView<Person> table = new TableView<>();
table.setItems(teamMembers);
```

Aquí, el componente `TableView` se asocia directamente con una clase llamada `Person`. Esta clase `Person` contendrá campos, propiedades y métodos que representan la información que se mostrará en la tabla.

###### 📋 Carga de Datos en TableView

Para cargar datos en `TableView`, se utiliza una lista observable. Por ejemplo:

```java
ObservableList<Person> teamMembers = FXCollections.observableArrayList(members);
```

### 🛠️ Personalización de TableView

Una de las ventajas de usar `TableView` en JavaFX es la capacidad de personalizar su apariencia y comportamiento. Esto incluye definir características como las cabeceras de las columnas.

#### 📑 Ejemplo de Personalización de Columnas

Para definir las cabeceras de las columnas y otros aspectos, se pueden utilizar métodos específicos del API de `TableView`. Aquí hay un ejemplo:

```java
TableColumn<Person, String> firstNameCol = new TableColumn<>("First Name");
firstNameCol.setCellValueFactory(new PropertyValueFactory<>(members.get(0).firstNameProperty().getName()));
TableColumn<Person, String> lastNameCol = new TableColumn<>("Last Name");
lastNameCol.setCellValueFactory(new PropertyValueFactory<>(members.get(0).lastNameProperty().getName()));
table.getColumns().setAll(firstNameCol, lastNameCol);
```

Este fragmento de código muestra cómo se pueden definir las columnas `First Name` y `Last Name` y cómo se pueden asociar con las propiedades correspondientes de la clase `Person`.

___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #Controles #TableView #ModeloDeDatos #OrigenDeDatos #Personalización #ObservableList #API #Columnas #CargaDeDatos #Conexión #InteracciónUsuario #ClasePerson
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%