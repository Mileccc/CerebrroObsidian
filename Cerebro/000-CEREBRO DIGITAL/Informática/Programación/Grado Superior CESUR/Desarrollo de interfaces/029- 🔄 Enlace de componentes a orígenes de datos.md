---
ID: 29
nombre: Enlace de componentes a orígenes de datos
tags:
  - pagdesarrollo_de_interfaces
---
___
### 🎛️ Fundamentos del Enlace de Datos

En el contexto de la arquitectura MVC (Modelo-Vista-Controlador), cualquier elemento de la interfaz de usuario que pueda mostrar o recoger información puede ser enlazado a un origen de datos a través de un controlador.

#### 📌 Ejemplo con Controles Básicos

Para ilustrar este concepto, consideremos dos controles muy básicos en JavaFX:

- `javafx.scene.control.Label`
- `javafx.scene.text.Text`

Ambos controles son capaces de mostrar texto en la interfaz de usuario. Veamos cómo se crea un nuevo control `Label`:

```java
Label labelData = new Label("data from DB");
```

Este control `labelData` se conectará a un controlador, que a su vez estará vinculado a un modelo. Este modelo puede obtener información de una celda de una base de datos y mostrarla en el control `Label`.

### 📊 Trabajando con TableView

#### 📝 Estructura de Datos

En el caso de `TableView`, los datos suelen almacenarse en una lista observable de un tipo específico, como `Person`. Por ejemplo:

```java
ObservableList<Person> teamMembers = FXCollections.observableArrayList(members);
```

#### 🛠️ Definición de la Clase `Person`

La clase `Person` podría definirse de la siguiente manera:

```java
public class Person {
    private StringProperty firstName;
    // Métodos para firstName
    private StringProperty lastName;
    // Métodos para lastName
    public Person(String firstName, String lastName) {
        setFirstName(firstName);
        setLastName(lastName);
    }
}
```

### 🌐 Diversidad de Orígenes de Datos

Los componentes en JavaFX pueden conectarse a una variedad de orígenes de datos:

- Datos en memoria
- Bases de datos relacionales (BBDD)
- Bases de datos en la nube

Cada uno de estos orígenes de datos puede ser accesible a través del controlador, permitiendo una gran flexibilidad en la forma en que se manejan y presentan los datos en la interfaz de usuario.

___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #MVC #EnlaceDeDatos #Controlador #InterfazDeUsuario #Label #Text #TableView #ObservableList #ClasePerson #OrigenDeDatos #DatosEnMemoria #BasesDeDatosRelacionales #BasesDeDatosEnLaNube 
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%