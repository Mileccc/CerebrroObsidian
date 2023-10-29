---
ID: 10
nombre: Ejemplo de código con ficheros
tags:
  - pagacceso_a_datos
---
___
##### Ejemplo de código con ficheros

```java
import java.io.File;

public class EjemploListarArchivos {
    public static void main(String[] args) {
        // Ruta del directorio en el que queremos trabajar
        String directorioPath = "/ruta/del/directorio";

        // Nombre del archivo que vamos a crear
        String nombreArchivo = "mi_archivo.txt";

        try {
            // Crear un nuevo archivo en el directorio especificado
            File archivo = new File(directorioPath, nombreArchivo);
            
            if (archivo.createNewFile()) {
                System.out.println("Archivo creado: " + archivo.getName());
            } else {
                System.out.println("El archivo ya existe.");
            }

            // Listar los archivos en el directorio
            File directorio = new File(directorioPath);
            File[] archivosEnDirectorio = directorio.listFiles();

            if (archivosEnDirectorio != null) {
                System.out.println("Archivos en el directorio:");
                for (File archivoEnDirectorio : archivosEnDirectorio) {
                    System.out.println(archivoEnDirectorio.getName());
                }
            } else {
                System.out.println("El directorio está vacío o no existe.");
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

```

Este código primero crea un archivo llamado "mi_archivo.txt" en el directorio especificado. Luego, utiliza `listFiles()` para obtener una lista de archivos en el directorio y muestra sus nombres en la consola mediante un ciclo `for`. Asegúrate de reemplazar `"/ruta/del/directorio"` con la ruta real de tu directorio de trabajo.











___
%%
tags: #código #programación #pagacceso_a_datos  #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%