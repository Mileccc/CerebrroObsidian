---
ID: 8
nombre: Ejemplos de lectura y escritura de Flujos de datos
tags:
  - pagacceso_a_datos
---
___
##### Ejemplos de lectura y escritura de Flujos de datos

***Lectura y escritura típica de flujo de bytes  ***

```java
import java.io.*;

public class EjemploFlujoBytes {
    public static void main(String[] args) {
        String archivoEntrada = "entrada.bin";
        String archivoSalida = "salida.bin";

        try (FileInputStream inputStream = new FileInputStream(archivoEntrada);
             FileOutputStream outputStream = new FileOutputStream(archivoSalida)) {

            int byteLeido;
            while ((byteLeido = inputStream.read()) != -1) {
                // Procesa el byte leído
                outputStream.write(byteLeido);
            }

            System.out.println("Lectura y escritura de bytes completadas.");
        } catch (FileNotFoundException e) {
            System.err.println("El archivo de entrada no se encontró: " + e.getMessage());
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```


***Lectura y escritura típica de flujo de caracteres***
```java
import java.io.*;

public class EjemploFlujoCaracteres {
    public static void main(String[] args) {
        String archivoEntrada = "entrada.txt";
        String archivoSalida = "salida.txt";

        try (BufferedReader lector = new BufferedReader(new FileReader(archivoEntrada));
             BufferedWriter escritor = new BufferedWriter(new FileWriter(archivoSalida))) {

            String linea;
            while ((linea = lector.readLine()) != null) {
                escritor.write(linea);
                escritor.newLine();
            }

            System.out.println("Lectura y escritura completadas.");
        } catch (FileNotFoundException e) {
            System.err.println("El archivo de entrada no se encontró: " + e.getMessage());
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```







___
%%
tags: #código #programación #pagacceso_a_datos  #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%