---
ID: 35
nombre: Bindings y propiedades
tags:
  - pagdesarrollo_de_interfaces
---
___
## 🌟 Introducción a JavaFX: Bindings y Propiedades 

![](https://www.youtube.com/watch?v=ESLDAQ-CC4M&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=215&ab_channel=Aulaenlanube)

### 📚 Concepto de Propiedad en JavaFX

1. **Importancia**: Las propiedades son fundamentales para crear interfaces de usuario que sean reactivas y fáciles de mantener.
2. **Tipos de Propiedades**: Antes de adentrarnos en el mundo de los `bindings`, es esencial entender los distintos tipos de propiedades que se pueden crear en JavaFX.

### 🔄 Bindings en JavaFX

1. **Qué es un Binding**: El concepto de `binding` se desarrolla a partir de las propiedades, permitiendo establecer relaciones entre ellas.
2. **Tipos de Binding**: 
   - **Unidireccional**: La actualización de una propiedad se refleja en otra, pero no viceversa.
   - **Bidireccional**: Las actualizaciones se reflejan en ambas propiedades.
   - **De expresiones**: Permite aplicar operaciones complejas antes de actualizar una propiedad.
   
3. **Clases Especializadas**: Existen clases especializadas para almacenar resultados derivados de una o más propiedades.

### 🛠 Ejemplos de Uso

1. **Barra de Progreso**: Primeramente, se mostrará cómo crear una barra de progreso utilizando propiedades y `bindings`.
   
```java
ProgressBar progressBar = new ProgressBar();
DoubleProperty progressProperty = new SimpleDoubleProperty();
progressBar.progressProperty().bind(progressProperty);
```

2. **Conversor de Monedas**: Como segundo ejemplo, se abordará la creación de un conversor de monedas.

```java
DoubleProperty dollars = new SimpleDoubleProperty();
DoubleProperty euros = new SimpleDoubleProperty();
euros.bind(dollars.multiply(0.85));
```

Al organizar la información en esta forma, es más fácil captar la esencia y aplicabilidad de las propiedades y `bindings` en JavaFX. Además, al enumerar los tipos y ejemplos específicos, se añade claridad al contenido.
___
## 🌟 Profundizando en Propiedades

### 📚 Qué son las Propiedades en JavaFX

1. **Definición**: Una propiedad en JavaFX es un contenedor especializado que puede alojar distintos tipos de valores, como enteros, cadenas o incluso objetos.
2. **Finalidad**: La utilidad primordial de las propiedades es permitir que variables y elementos de la interfaz de usuario estén sincronizados, facilitando la creación de interfaces reactivas.

### 🛡 Características de las Propiedades

1. **Encapsulamiento**: Las propiedades toman un valor y lo encapsulan para que sea seguro y fácil de manipular.
2. **Observabilidad**: Permiten ser observadas, lo que significa que se pueden recibir notificaciones cuando el valor de una propiedad cambia.

### 🧪 Tipos de Propiedades y Ejemplos

Aquí se muestran ejemplos de declaración de propiedades según su tipo:

1. **String Properties**
   ```java
   StringProperty s1 = new SimpleStringProperty("Hola");
   StringProperty s2 = new SimpleStringProperty("Mundo");
   ```
   
2. **Integer Property**
   ```java
   IntegerProperty x = new SimpleIntegerProperty(5);
   ```
   
3. **Double Property**
   ```java
   DoubleProperty euros = new SimpleDoubleProperty(1.123);
   ```
   
4. **Boolean Property**
   ```java
   BooleanProperty condicion = new SimpleBooleanProperty(true);
   ```
   
5. **Object Properties**
   - Aunque se pueden usar propiedades para contener cualquier objeto a través de `ObjectBinding`, los tipos primitivos son generalmente suficientes para entender el concepto.

### 🔄 Sincronización con Bindings

1. **Qué es el Binding**: Es una funcionalidad que permite sincronizar dos o más propiedades entre sí.
   
2. **Ejemplo de Binding entre Strings**
   ```java
   s1.bind(s2);
   ```
   En este caso, estamos vinculando el valor de `s1` al valor de `s2`, haciéndolos estar sincronizados.

___
## 🌟Tipos de Binding
___
### 🎯 Binding Unidireccional

1. **Definición**: En un binding unidireccional, una propiedad está vinculada a otra de tal manera que si la primera cambia, la segunda también lo hace. Sin embargo, la segunda propiedad no tiene la capacidad de cambiar la primera.
   
2. **Comportamiento**
    - Si la propiedad fuente cambia, la propiedad vinculada también cambia.
    - Si se intenta cambiar la propiedad vinculada, se producirá una excepción.

3. **Ejemplo de Binding Unidireccional con Strings**

    ```java
    StringProperty s1 = new SimpleStringProperty("Hola");
    StringProperty s2 = new SimpleStringProperty("Mundo");

    s2.bind(s1);

    // Cambiar el valor de s1 afecta a s2
    s1.set("Adiós");
    System.out.println(s2.get()); // Salida: Adiós
    s2.set("Fin"); // Daría Error, no se puede cambiar s2 directamente
    ```

    En este ejemplo, la propiedad `s2` queda vinculada a `s1`. Por lo tanto, si `s1` cambia, `s2` también lo hará. Si se intenta cambiar `s2` directamente, se generará una excepción.

4. **Comportamiento Inicial**

    Si se realizan el binding pero no se modifica la propiedad fuente (`s1` en el ejemplo), la propiedad vinculada (`s2`) tomará el valor inicial de la propiedad fuente. En otras palabras, si no cambiamos `s1`, el valor de `s2` sería "Hola", ya que `s1` tiene inicialmente ese valor.

#### 🔒 Nota sobre Limitaciones

- No se puede modificar directamente el valor de una propiedad que ha sido vinculada de forma unidireccional. Cualquier intento de hacerlo resultará en una excepción.

___
### 🔄 Binding Bidireccional

#### 1️⃣ Definición
En un binding bidireccional, ambas propiedades están vinculadas de tal manera que si cualquiera de ellas cambia, la otra también lo hace. A diferencia del binding unidireccional, ambas propiedades pueden afectarse mutuamente.

#### 2️⃣ Método Utilizado
Para establecer un binding bidireccional, usamos el método `bindBidirectional()` en lugar del método `bind()` usado en el binding unidireccional.

#### 3️⃣ Comportamiento en Detalle

- **Actualización Automática**: Al establecer el binding, los valores de ambas propiedades se sincronizan automáticamente.
  
- **Valor Prevalente**: Al realizar el binding bidireccional, el valor de la segunda propiedad prevalece y se copia en la primera.

#### 4️⃣ Ejemplo de Binding Bidireccional con Strings

```java
StringProperty s1 = new SimpleStringProperty("Hola");
StringProperty s2 = new SimpleStringProperty("Mundo");

s1.bindBidirectional(s2);

// Modificar s2 afecta a s1
s2.set("Adiós");
System.out.println(s1.get());  // Salida: Adiós

// Modificar s1 afecta a s2
s1.set("Fin");
System.out.println(s2.get());  // Salida: Fin
```

En este ejemplo, ambas propiedades `s1` y `s2` se vinculan bidireccionalmente. Cuando cambiamos el valor de una, la otra también se actualiza.

#### 5️⃣ Observaciones Específicas

- Al establecer el binding bidireccional, el valor inicial de la segunda propiedad (`s2` en el ejemplo) se copia en la primera (`s1`), sincronizando así sus valores iniciales.
  
- Posteriormente, cualquier cambio en una de las propiedades se reflejará en la otra, permitiendo una verdadera interacción bidireccional.

#### 🚫 Nota sobre Desvinculación

- Al igual que con el binding unidireccional, también podemos desvincular las propiedades en el binding bidireccional si es necesario, lo que detiene la sincronización entre ellas.

___

### 🎭 Binding de Expresiones

#### 1️⃣ Introducción y Definición

En JavaFX, además de los bindings unidireccionales y bidireccionales, tenemos un tercer tipo llamado *binding de expresiones*. Este tipo de binding es particularmente poderoso porque permite realizar operaciones más complejas entre propiedades y vincular resultados de estas operaciones a otras propiedades.

#### 2️⃣ Operaciones Básicas entre Propiedades

Una de las características más llamativas es la capacidad de efectuar operaciones aritméticas (como suma, resta, etc.) entre diferentes propiedades.

##### 📝 Ejemplo Básico de Suma de Propiedades

```java
IntegerProperty a = new SimpleIntegerProperty(5);
IntegerProperty b = new SimpleIntegerProperty(10);
IntegerProperty sum = new SimpleIntegerProperty();

sum.bind(a.add(b));

System.out.println(sum.get());  // Salida: 15
```

En este ejemplo, la propiedad `sum` se vincula al resultado de sumar las propiedades `a` y `b`. Inicialmente, `a` tiene un valor de 5 y `b` un valor de 10, por lo que `sum` tendrá un valor de 15.

#### 3️⃣ Actualización Automática

- Al modificar el valor de cualquiera de las propiedades `a` o `b`, el valor de `sum` se recalculará automáticamente.

```java
a.setValue(20);
System.out.println(sum.get());  // Salida: 30
```

En este caso, al cambiar el valor de `a` a 20, `sum` se actualiza automáticamente a 30 (20 + 10).

#### 4️⃣ Restricciones de Modificación Directa

- Una propiedad que está enlazada a una expresión no se puede modificar directamente. Intentar hacerlo generará un error.

```java
// Esto generará un error
sum.setValue(100);
```

La propiedad `sum` está vinculada a la suma de `a` y `b`, por lo que su valor solo puede cambiarse indirectamente al modificar `a` o `b`.

#### 5️⃣ Operaciones Avanzadas y Condiciones

- Además de operaciones aritméticas simples, también es posible incorporar condiciones y funciones más complejas en el binding de expresiones. Esto se verá en ejemplos más avanzados.

___
## 🌟 Especializaciones en la Clase Binding en JavaFX

### 📌 Tipos de Especializaciones en Binding

JavaFX permite utilizar especializaciones en la clase Binding para trabajar con distintos tipos de datos. Veamos algunos ejemplos de cómo hacerlo con tipos de datos específicos.

#### 🔢 NumberBinding: Trabajando con Números Enteros

La clase `NumberBinding` es una clase abstracta que se usa para representar valores numéricos. Esta clase puede depender de uno o más observables. En JavaFX, estos observables son, de hecho, propiedades que están en constante observación.

##### Ejemplo con Números Enteros
```java
IntegerProperty a = new SimpleIntegerProperty(5);
IntegerProperty b = new SimpleIntegerProperty(10);
NumberBinding suma = a.add(b);
System.out.println(suma.getValue()); // 15
a.setValue(20);
System.out.println(suma.getValue()); // 30
```

Ahora, si hacemos un `System.out.println(suma.getValue());`, nos devolverá `15` porque `suma` está vinculado a las propiedades `a` y `b`.

#### 🎯 DoubleBinding: Trabajando con Números Flotantes

`DoubleBinding` es una especialización de `NumberBinding` diseñada para trabajar con números en coma flotante.

##### Ejemplo con Números Flotantes
```java
DoubleProperty x = new SimpleDoubleProperty(2.5);
DoubleProperty y = new SimpleDoubleProperty(4.5);
DoubleBinding resultado = x.multiply(y);
System.out.println(resultado.getValue()); // 11.25
```
Si ejecutamos `System.out.println(resultado.getValue());`, obtendremos `11.25` como resultado.

#### 📜 StringBinding: Cadena de Texto

`StringBinding` se utiliza para crear cadenas de texto a partir de uno o más observables.

##### Ejemplo con Cadenas de Texto
```java
StringProperty nombre = new SimpleStringProperty("Juan");
StringProperty apellido = new SimpleStringProperty("Pérez");
StringBinding nombreCompleto = (StringBinding)Bindings.concat(nombre, " ", apellido);
System.out.println(nombreCompleto.getValue()); // Juan Pérez
nombre.set("Ana");
System.out.println(nombreCompleto.getValue()); // Ana Pérez
```
Al ejecutar `System.out.println(nombreCompleto.getValue());`, obtendremos `Juan Pérez`.

#### ✔️ BooleanBinding: Condiciones Booleanas

`BooleanBinding` está diseñado para manejar propiedades de tipo booleano.

##### Ejemplo con Booleanos
```java
BooleanProperty condicionA = new SimpleBooleanProperty(true);
BooleanProperty condicionB = new SimpleBooleanProperty(false);
BooleanBinding ambasVerdaderas = condicionA.and(condicionB);
System.out.println(ambasVerdaderas.getValue()); // false
condicionB.set(true);
System.out.println(ambasVerdaderas.getValue()); // true

BooleanBinding cualquieraVerdadera = condicionA.or(condicionB);
BooleanBinding noA = condicionA.not();

System.out.println(cualquieraVerdadera.getValue()); // true
System.out.println(noA.getValue()); // false
```
Si ejecutamos `System.out.println(ambasVerdaderas.getValue());`, nos devolverá `false`.

___
### 🛠️Métodos Estáticos de la Clase `Binding`

---

#### 1. Métodos Numéricos

La clase `Binding` proporciona diferentes métodos estáticos que permiten realizar operaciones matemáticas sobre observables numéricos.

* **Add**: Suma dos observables de tipo numérico.
* **Subtract**: Resta dos observables de tipo numérico.
* **Multiply**: Multiplica dos observables de tipo numérico.
* **Divide**: Divide dos observables de tipo numérico.

##### Ejemplo con Add

Para realizar una suma, no necesitas hacer `a.add(b)`. Puedes utilizar el método estático `add` de la clase `Binding`.

```java
IntegerProperty a = new SimpleIntegerProperty(5);
IntegerProperty b = new SimpleIntegerProperty(2);
NumberBinding suma = Bindings.add(a, b);
System.out.println("Suma: " + suma.getValue()); // Salida: Suma: 7
```

---

#### 2. Condicionales

La clase `Binding` también proporciona métodos para realizar enlaces condicionales.

* **When**: Inicia un enlace condicional y toma un booleano como parámetro.
* **Then**: Define el resultado si la condición es `true`.
* **Otherwise**: Define el resultado si la condición es `false`.

##### Ejemplo con When

Aquí hay un ejemplo de cómo se puede utilizar el método `when` para crear un enlace condicional.

```java
BooleanProperty condicion = new SimpleBooleanProperty(true);
StringProperty resultado = new SimpleStringProperty("");
resultado.bind(Bindings.when(condicion).then("Verdadero").otherwise("Falso"));
System.out.println("Resultado: " + resultado.getValue()); // Salida: Resultado: Verdadero
```

---

#### 3. Ejemplos

Ahora, vamos a mezclar varios de los métodos que hemos aprendido.

##### Ejemplo con Add y When

Podemos combinar métodos numéricos y condicionales para crear enlaces más complejos.

```java
NumberBinding suma = Bindings.add(a, b);
BooleanBinding isSumaMayorACinco = Bindings.greaterThan(suma, 5);
StringProperty resultado = new SimpleStringProperty("");
resultado.bind(Bindings.when(isSumaMayorACinco).then("Mayor que 5").otherwise("Menor o igual a 5"));
```

En este ejemplo, `resultado` será "Mayor que 5" si la suma de `a` y `b` es mayor que 5; de lo contrario, será "Menor o igual a 5".

---
## 🛠 Especializaciones en Clase Binding: Ejercicio Avanzado en JavaFX 

El contenido se centra en un ejercicio más complejo que combina múltiples métodos y propiedades de la clase `Binding` en JavaFX. El objetivo es ayudarte a entender cómo interactúan estas propiedades y métodos en un escenario real.
### 🎯 Creación de Propiedades

```java
// Creación de propiedades enteras num1 y num2 con valores 10 y 20 respectivamente
IntegerProperty num1 = new SimpleIntegerProperty(10);
IntegerProperty num2 = new SimpleIntegerProperty(20);

// Creación de una propiedad entera valorCondicion con valor 50
IntegerProperty valorCondicion = new SimpleIntegerProperty(50);
```

### 🧮 Operaciones Matemáticas con Bindings

```java
// Creación de un NumberBinding llamado multiplicacion que almacena el resultado de multiplicar num1 y num2
NumberBinding multiplicacion = num1.multiply(num2);
```

En este momento, `multiplicacion` tendrá un valor inicial de 200 (10 * 20).

### 🌟 Uso del Método When

```java
// Creación de otro NumberBinding llamado resultado
NumberBinding resultado = Bindings.when(multiplicacion.greaterThan(100))
                                  .then(multiplicacion.add(valorCondicion))
                                  .otherwise(multiplicacion);
```

`resultado` se inicializa con 250, ya que `multiplicacion` es mayor que 100. 

### 🖨 Salidas de Ejemplo

```java
// Se imprime el valor inicial de resultado que es (10*20)=200; 200>100 -> 200+50=250
System.out.println("Resultado inicial: " + resultado.getValue());
```

### 🔄 Cambios en Propiedades y Efectos en Bindings

1. Cambio en `num1` a 5:
   - `multiplicacion` se actualiza a 100 (5 * 20)
   - `resultado` se actualiza a 100 porque ya no cumple con la condición `greaterThan(100)`.

   ```java
   // Cambio de num1 a 5
   num1.setValue(5);
   ```

2. Cambio en `num2` a 25:
   - `multiplicacion` se actualiza a 125 (5 * 25)
   - `resultado` se actualiza a 175 (125 + 50)

   ```java
   // Cambio de num2 a 25
   num2.setValue(25);
   ```

3. Cambio en `valorCondicion` a 100:
   - `multiplicacion` se mantiene en 125
   - `resultado` se actualiza a 225 (125 + 100)

   ```java
   // Cambio de valorCondicion a 100
   valorCondicion.setValue(100);
   ```

___

## Ejemplo Avanzada Barra de Progreso

```java
package com.aula.progreso;

import javafx.application.Application;
import javafx.application.Platform;
import javafx.beans.property.DoubleProperty;
import javafx.beans.property.SimpleDoubleProperty;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.Label;
import javafx.scene.control.ProgressBar;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

/**
 * JavaFX App
 */
public class App extends Application {

    public void start(Stage ventanaPrincipal) throws Exception {

        VBox root = new VBox(20);
        root.setAlignment(Pos.CENTER);

        ProgressBar progressBar = new ProgressBar(0);
        Label label = new Label("Procesando...");

        DoubleProperty progressValue = new SimpleDoubleProperty(0);

        // Vinculamos la propiedad del progreso al contador
        progressBar.progressProperty().bind(progressValue);

        root.getChildren().addAll(progressBar, label);

        Scene scene = new Scene(root, 400, 300);

        ventanaPrincipal.setTitle("Barra de Progreso con Thread");
        ventanaPrincipal.setScene(scene);
        ventanaPrincipal.show();

        // Aumentar el contador con un hilo (simulando una tarea en segundo plano)
        new Thread(() -> {
            for (int i = 0; i <= 100; i++) {

                final int FINAL_I = i;
                
                Platform.runLater(() -> {
                    progressValue.set(FINAL_I / 100.0);

                    if (FINAL_I == 100) {
                        label.setText("Completado!!");
                        progressBar.setStyle("-fx-accent: green");
                    }
                });

                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }).start();
    }

    public static void main(String[] args) {
        launch();
    }

}
```

## Ejemplo Avanzado Conversor de Monedas

```java
package com.aula.conversor;

import javafx.application.Application;
import javafx.beans.binding.Bindings;
import javafx.beans.binding.DoubleBinding;
import javafx.beans.property.DoubleProperty;
import javafx.beans.property.SimpleDoubleProperty;
import javafx.geometry.Insets;
import javafx.scene.Scene;
import javafx.scene.control.Label;
import javafx.scene.control.TextField;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

/**
 * JavaFX App
 */
public class App extends Application {

    @Override
    public void start(Stage ventanaPrincipal) {

        VBox vbox = new VBox(10);
        vbox.setPadding(new Insets(20));

        TextField campoEuros = new TextField();
        Label etiquetaDolares = new Label();

        DoubleProperty euros = new SimpleDoubleProperty();
        DoubleProperty tasaCambio = new SimpleDoubleProperty(1.08);

        euros.bind(Bindings.createDoubleBinding(() -> {
            try {
                return Double.parseDouble(campoEuros.getText());
            } catch (NumberFormatException e) {
                return 0.0;
            }
        }, campoEuros.textProperty()));

        DoubleBinding dolares = euros.multiply(tasaCambio);
        etiquetaDolares.textProperty().bind(Bindings.format("En dólares: %.2f", dolares));
        vbox.getChildren().addAll(new Label("Euros:"), campoEuros, etiquetaDolares);

        Scene root = new Scene(vbox, 300, 200);
        ventanaPrincipal.setScene(root);
        ventanaPrincipal.setTitle("Conversor de monedas");
        ventanaPrincipal.show();
    }

    public static void main(String[] args) {
        launch();
    }

}
```


___
%%
tags: #pagdesarrollo_de_interfaces #JavaFX #Binding #Especializaciones #NumberBinding #StringBinding #MétodosEstáticos #EjercicioAvanzado #CreaciónDePropiedades #OperacionesMatemáticas #EfectosEnBindings #Algoritmos #Programación #EstructurasDeDatos #ComplejidadComputacional #BarraDeProgreso #ConversorDeMonedas
%%