---
ID: 42
nombre: Ficheros en Java NIO
tags:
  - pagacceso_a_datos
---
___
![](https://www.youtube.com/watch?v=s8Ea7478mmA&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=182&ab_channel=Aulaenlanube)

### 📝 Introducción

Java NIO (New I/O) ofrece clases adicionales para trabajar de manera más eficiente con ficheros. En este tutorial, abordaremos cómo manipular ficheros de texto y binarios utilizando las clases del paquete Java NIO.

---

### 📄 Trabajar con Ficheros de Texto

#### 🛠 Herramientas y Clases

- **Clase `Path`**: Representa la ruta del fichero.
- **Clase `Files`**: Ofrece métodos para leer y escribir en ficheros.

#### 📝 Ejemplo de Escritura

```java
List<String> lineas = Arrays.asList("linea1", "linea2");
Path path = Paths.get("file.txt");
Files.write(path, lineas, StandardCharsets.UTF_8);
```

#### 📝 Ejemplo de Lectura

```java
List<String> lineasLeidas = Files.readAllLines(path, StandardCharsets.UTF_8);
for(String linea : lineasLeidas) {
    System.out.println(linea);
}
```

### Código completo de ejemplo con Ficheros de Texto
```java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.util.Arrays;
import java.util.List;

public class EjemploTextoNio {
    public static void main(String[] args) {
        
        try {

            List<String> lineasEscritas = Arrays.asList("Hola", "Mundo", "Desde", "Java", "NIO");
            Path fichero = Paths.get("archivoNIO.txt");

            // Escribe las líneas en el archivo
            Files.write(fichero, lineasEscritas, StandardCharsets.UTF_8); // El tercer argumento es el tipo de codificación

            // Lee todas las líneas del archivo
            List<String> lineasLeidas  = Files.readAllLines(fichero, StandardCharsets.UTF_8); 
            
            for (String s : lineasLeidas) {
                System.out.println(s);
            }

        } catch (IOException e) {
            System.out.println("Ocurrió un error: " + e.getMessage());
        }
    }
}
```


---

### 📦 Trabajar con Ficheros Binarios

#### 🛠 Herramientas y Clases

- **Clase `FileChannel`**: Para leer y escribir en ficheros.
- **Clase `ByteBuffer`**: Buffer para almacenar datos.

#### 📝 Ejemplo de Escritura

```java
FileOutputStream fos = new FileOutputStream("integers.bin");
FileChannel canal = fos.getChannel();
ByteBuffer buffer = ByteBuffer.allocate(Integer.BYTES * 4);
for(int i = 0; i < 4; i++) {
    buffer.putInt(i);
}
buffer.flip();
canal.write(buffer);
```

#### 📝 Ejemplo de Lectura

```java
FileInputStream fis = new FileInputStream("integers.bin");
FileChannel canal = fis.getChannel();
ByteBuffer buffer = ByteBuffer.allocate(Integer.BYTES * 4);
canal.read(buffer);
buffer.flip();
while(buffer.hasRemaining()) {
    System.out.println(buffer.getInt());
}
```


### Código completo de Ejemplo con Ficheros Binarios
```java
import java.nio.ByteBuffer;
import java.nio.channels.FileChannel;
import java.io.*;

public class EjemploBinariosNio {
    public static void main(String[] args) {
        
        try {

            //ESCRITURA UTILIZANDO UN CANAL
            // Crea un nuevo archivo y obtén un canal para escribir en él
            FileOutputStream fos = new FileOutputStream("integers.bin");
            FileChannel canal = fos.getChannel();

            // Crea un buffer y pone algunos enteros en él
            ByteBuffer buffer = ByteBuffer.allocate(Integer.BYTES * 4);
            for (int i = 0; i < 4; i++) {
                buffer.putInt(i);
            }

            // Prepara el buffer para escribir
            buffer.flip();

            // Escribe el buffer en el archivo
            canal.write(buffer);
           
            fos.close();


            //LECTURA UTILIZANDO UN CANAL
            FileInputStream fis = new FileInputStream("integers.bin");
            canal = fis.getChannel();

            // Crea un buffer para almacenar los enteros
            buffer = ByteBuffer.allocate(Integer.BYTES * 4);

            // Lee del archivo en el buffer
            canal.read(buffer);
            // Prepara el buffer para la lectura
            buffer.position(1);

            //buffer
            // bytes 1-4(int=0):   00000000 00000000 00000000 00000000 
            // bytes 5-8(int=1):   00000000 00000000 00000000 00000001 
            // bytes 9-12(int=2):  00000000 00000000 00000000 00000010 
            // bytes 13-16(int=3): 00000000 00000000 00000000 00000011 

            //(0)   --> 00000000 00000000 00000000 00000000
            //(256) --> 00000000 00000000 00000001 00000000
            //(512) --> 00000000 00000000 00000010 00000000
            //error --> 00000000 00000000 00000011 --------

            // Lee los enteros del buffer
            while (buffer.hasRemaining()) {
                System.out.println(buffer.getInt());
            }
            fis.close();

        } catch (IOException e) {
            System.out.println("Ocurrió un error: " + e.getMessage());
        }
    }
}
```


---

### 🎯 Consejos y Trucos

- **Posición y Límite**: Se pueden establecer de forma manual, pero usar `flip()` es más práctico.
- **Try-With-Resources**: Para cerrar recursos automáticamente.

```java
try(FileOutputStream fos = new FileOutputStream("integers.bin")) {
    // código aquí
}
```



___
%%
tags: #java  #pagacceso_a_datos  #Java #NIO #FicherosDeTexto #FicherosBinarios #ClasePath #ClaseFiles #ClaseFileChannel #ClaseByteBuffer #EjemploDeEscritura #EjemploDeLectura #ConsejosYTrucos
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%