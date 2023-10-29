---
ID: 15
nombre: Ejemplo Lectura-Escritura con Acceso Aleatorio
tags:
  - pagacceso_a_datos
---
___
### EJEMPLO PRÁCTICO 
En la empresa en la que estamos desarrollando el editor de texto, tienen la necesidad de almacenar el número de productos que entran por almacén a través de un dispositivo que permite ejecutar Java. 

El _usuario_ introducirá un número entero por teclado y lo añadirá al _final de un fichero binario_ ``recepcion.dat`` que contiene las cantidades. 

Necesitamos generar los métodos y programas necesarios para realizar la gestión. En este caso la aplicación será muy sencilla e incluida totalmente en un único paquete que se encargará de realizar todo el proceso:

```java
import java.io.EOFException;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.RandomAccessFile;
import java.util.Scanner;

public class EntradaMercancia {
  static Scanner scanner = new Scanner(System.in);
  static RandomAccessFile fichero = null;

  public static void main(String[] args) {
    int numero;
    try {
      //fichero para el almacenaje de las mercancías
      fichero = new RandomAccessFile("/mercancia.dat", "rw");
      mostrarFichero(); //muestra el contenido original del fichero

      System.out.print("Introduce las unidades recibidas: ");
      numero = scanner.nextInt();
      fichero.seek(fichero.length()); //nos colocamos al final del fichero
      fichero.writeInt(numero); //se escribe el entero
      mostrarFichero();//muestra el contenido del fichero después de añadir el número

    } catch (FileNotFoundException ex) {
      System.out.println(ex.getMessage());
    } catch (IOException ex) {
      System.out.println(ex.getMessage());
    } finally {
      try {
        if (fichero != null) {
          fichero.close();
        }
      } catch (IOException e) {
        System.out.println(e.getMessage());
      }
    }
  }

  public static void mostrarFichero() {
    int n;
    try {
      fichero.seek(0); //principio del fichero
      while (true) {
        n = fichero.readInt(); //leemos un entero
        System.out.println(n); //lo mostramos
      }
    } catch (EOFException e) {
      System.out.println("Fin de fichero");
    } catch (IOException ex) {
      System.out.println(ex.getMessage());
    }
  }
}

```


___
%%
tags: #pagacceso_a_datos  #Java #RandomAccessFile #FileHandling #EOFException #FileNotFoundException #IOException #Scanner #tryCatch #finally #mostrarFichero #mainMethod #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%