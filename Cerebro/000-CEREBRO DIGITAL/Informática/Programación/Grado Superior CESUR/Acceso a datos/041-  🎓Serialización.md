---
ID: 41
nombre: Serialización
tags:
  - pagacceso_a_datos
---
___

![](https://www.youtube.com/watch?v=p2zgGu4nOCc&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=181&ab_channel=Aulaenlanube)

### 📚 Introducción a la Serialización

La serialización en Java es un mecanismo que permite almacenar el estado de un objeto en una secuencia de bytes. Este proceso es especialmente útil para guardar instancias de objetos en archivos o bases de datos.

* **Estado del Objeto**: Los valores de las variables asociadas a una instancia específica.
  * *Ejemplo*: Una instancia de la clase `Persona` con atributos `nombre` y `edad` tendría su estado definido por estos valores.

### 🔄 Proceso de Serialización y Deserialización

* **Serialización**: Convertir el estado del objeto en una secuencia de bytes.
* **Deserialización**: Convertir la secuencia de bytes de nuevo en una instancia del objeto.

#### 🛠️ Requisitos para la Serialización

1. La clase debe implementar la interfaz `Serializable`.
2. No se requiere ningún método adicional; la interfaz actúa como un marcador.

```java
public class Ejemplo implements Serializable {
    // Código de la clase
}
```

#### ⚠️ Consideraciones de Seguridad

* La serialización puede ser insegura si los datos no provienen de fuentes confiables.
* Alternativas más seguras incluyen el uso de JSON (JavaScript Object Notation).

### 📝 Ejemplo de Serialización

Para ilustrar el proceso de serialización, se crea una instancia de la clase `Grupo`, que contiene una colección de instancias de la clase `Alumno`.

```java
public class EjemploSerializacion {
    public static void main(String[] args) {
        Grupo dam = new Grupo("1DAM");
        dam.agregarAlumno(new Alumno("Pep", "1111A", 15));
        dam.agregarAlumno(new Alumno("Tom", "2222A", 17));
        // Código para serializar el objeto 'dam'
    }
}
```

#### 📄 Pasos para Serializar un Objeto

1. Crear una instancia de `FileOutputStream`.
2. Envolver `FileOutputStream` en un objeto `ObjectOutputStream`.
3. Utilizar el método `writeObject()` para escribir la instancia del objeto.

```java
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectOutputStream;

public class EjemploSerializacion {

    public static void main(String[] args) {

        Grupo dam = new Grupo("1DAM");
        dam.agregarAlumno(new Alumno("Pep", "1111A", 15));
        dam.agregarAlumno(new Alumno("Tom", "2222A", 17));

        try (FileOutputStream fos = new FileOutputStream("archivo.dat")) {
            ObjectOutputStream out = new ObjectOutputStream(fos);
            out.writeObject(dam);
            out.writeInt(23);
            out.writeObject(new Alumno("Jon", "3333A", 20));
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

### 🔄 Ejemplo de Deserialización

Para deserializar, se sigue un proceso similar pero en orden inverso.

#### 📄 Pasos para Deserializar un Objeto

1. Crear una instancia de `FileInputStream`.
2. Envolver `FileInputStream` en un objeto `ObjectInputStream`.
3. Utilizar el método `readObject()` y realizar un *casting* al tipo de objeto.

```java
import java.io.FileInputStream;
import java.io.IOException;
import java.io.ObjectInputStream;

public class EjemploDeserializacion {

    public static void main(String[] args) {

        try {

            FileInputStream fis = new FileInputStream("archivo.dat");
            ObjectInputStream in = new ObjectInputStream(fis);

            System.out.println((Grupo)in.readObject());
            System.out.println("El entero es: "+(int)in.readInt());
            System.out.println((Alumno)in.readObject());

            in.close();

        } catch (ClassNotFoundException | IOException e) {
            e.printStackTrace();
        } 
    }
}
```

### 📚 Métodos de la Clase `ObjectStream`

* `writeObject()`: Escribe una instancia de un objeto en el flujo de datos.
* `readObject()`: Lee una instancia de un objeto del flujo de datos.

### Clases Grupo y Alumnos 
### Alumnos
```java
import java.io.Serializable;

public class Alumno implements Serializable {

    private String nombre;
    private String nia;
    private int edad;

    public Alumno(String nombre, String nia, int edad) {
        this.nombre = nombre;
        this.nia = nia;
        this.edad = edad;
    }

    public String getNombre() {
        return nombre;
    }

    public String getNia() {
        return nia;
    }

    public int getEdad() {
        return edad;
    }

    @Override
    public String toString() {
        return "Alumno [nombre=" + nombre + ", nia=" + nia + ", edad=" + edad + "]";
    }   
}
```

#### Grupo
```java
import java.io.Serializable;
import java.util.ArrayList;

public class Grupo implements Serializable {

    private String nombre;
    private ArrayList<Alumno> alumnos;

    public Grupo(String nombre) {
        this.nombre = nombre;
        alumnos = new ArrayList<>();
    }

    public String getNombre() {
        return nombre;
    }

    public ArrayList<Alumno> getAlumnos() {
        return alumnos;
    }

    public void agregarAlumno(Alumno a) {
        alumnos.add(a);
    }

    public void mostrarAlumnos() {
        for (Alumno a : alumnos) {
            System.out.println(a);
        }
    }

    @Override
    public String toString() {
        String s = "El nombre del Grupo es: " + getNombre() + "\n";
        for (Alumno alumno : alumnos) {
            s += alumno.toString() + "\n";
        }
        return s;
    }
}
```


### 📌 Conclusión

La serialización y deserialización son procesos fundamentales en Java para el almacenamiento y recuperación de objetos. Sin embargo, se deben tener en cuenta las consideraciones de seguridad y posiblemente utilizar alternativas más seguras como JSON.

___
%%
tags: #java  #pagacceso_a_datos  #Serialización #Java #EstadoDelObjeto #ProcesoDeSerialización #ProcesoDeDeserialización #RequisitosParaSerialización #InterfazSerializable #ConsideracionesDeSeguridad #JSON #EjemploDeSerialización #FileOutputStream #ObjectOutputStream #writeObject #EjemploDeDeserialización #FileInputStream #ObjectInputStream #readObject #MétodosObjectStream #Conclusión
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%