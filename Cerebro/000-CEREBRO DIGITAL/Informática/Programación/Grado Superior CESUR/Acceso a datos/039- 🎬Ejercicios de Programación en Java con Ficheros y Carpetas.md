---
ID: 39
nombre: Ejercicios de Programación en Java con Ficheros y Carpetas
tags:
  - pagacceso_a_datos
---
___
![](https://www.youtube.com/watch?v=JUQcm0pxbHc&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=178&ab_channel=Aulaenlanube)

---

## 📝 1. Listado de Archivos por Extensión en Java : Primer Ejercicio 🛠️

### 📂 Descripción del Problema

El ejercicio consiste en crear un método en Java que reciba una ruta de carpeta y liste todos los archivos con extensión `.txt`. Además, se pide crear una sobrecarga del método para que pueda recibir tanto la ruta como la extensión de los archivos a listar.

### 📜 Código Principal

El programa comienza con un método `main` donde se definen dos variables: `ruta` y `extensión`.

```java
public static void main(String[] args) {
    String ruta = ".";
    String extension = "txt";
    listarPorExtension(ruta, extension);
}
```

#### 🛠️ Método `listarPorExtension`

Este método toma dos parámetros: la `ruta` de la carpeta y la `extensión` de los archivos a listar.

```java
public static void listarPorExtension(String ruta, String extension) {
    // Código del método
}
```

### 📋 Pasos del Método

1. **Crear una instancia de la clase `File` para la carpeta**

    ```java
    File carpeta = new File(ruta);
    ```

2. **Verificar si la ruta es una carpeta válida**

    ```java
    if (!carpeta.isDirectory()) {
        System.out.println("La ruta proporcionada no es una carpeta válida.");
        return;
    }
    ```

3. **Listar archivos con la extensión dada**

    Utilizamos el método `listFiles` con una expresión lambda para filtrar los archivos.

    ```java
    File[] archivos = carpeta.listFiles((dir, name) -> name.toLowerCase().endsWith("." + extension.toLowerCase()));
    ```

4. **Mostrar los archivos encontrados**

    ```java
    if (archivos != null) {
        for (File f : archivos) {
            System.out.println("Archivo encontrado: " + f.getName());
        }
    } else {
        System.out.println("No se encontraron archivos con la extensión " + extension);
    }
    ```

### 🔄 Sobrecarga del Método

Se puede crear una sobrecarga del método para recibir solo la `ruta` y listar archivos con extensión `.txt` por defecto.

### 🏁 Resultados

Al ejecutar el programa, se listarán todos los archivos en la carpeta actual con la extensión `.txt`.

```java
import java.io.File;

public class ListarArchivosPorExtension {
    public static void main(String[] args) {
        String ruta = ".";
        String extension = "txt";
        listarPorExtension(ruta, extension);
    }

    public static void listarPorExtension(String ruta, String extension) {
        // Crear una instancia de la clase File para la carpeta
        File carpeta = new File(ruta);

        // Verificar si la ruta es una carpeta válida
        if (!carpeta.isDirectory()) {
            System.out.println("La ruta proporcionada no es una carpeta válida.");
            return;
        }

        // Listar archivos con la extensión dada
        File[] archivos = carpeta.listFiles((dir, name) -> name.toLowerCase().endsWith("." + extension.toLowerCase()));

        // Mostrar los archivos encontrados
        if (archivos != null) {
            for (File f : archivos) {
                System.out.println("Archivo encontrado: " + f.getName());
            }
        } else {
            System.out.println("No se encontraron archivos con la extensión " + extension);
        }
    }
}
```


---



---

## 📝 2. Creación de Archivos en Java: Segundo Ejercicio 🛠️

### 🎯 Objetivo del Ejercicio

Crear un método que genere archivos con nombres secuenciales (`nombre1.txt`, `nombre2.txt`, etc.) en una carpeta especificada por el usuario. El número de archivos a crear y la frase a escribir en cada uno de ellos también se recibirán como parámetros.

### 📋 Especificaciones

1. **Parámetros del Método**: 
    - Ruta de la carpeta donde se crearán los archivos.
    - Número `n` que indica la cantidad de archivos a crear.

2. **Contenido del Archivo**: 
    - Cada archivo debe contener la frase: "Este es el fichero nombreX.txt", donde `X` es el número del archivo.

### 📜 Código Principal: `main`

```java
public static void main(String[] args) {
    String ruta = ".";
    int n = 5;
    crearArchivos(ruta, n);
}
```

### 🛠️ Método `crearArchivos`

```java
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
import java.io.File;

public static void crearArchivos(String ruta, int n) {
    File directorio = new File(ruta);
    if (!directorio.isDirectory()) {
        System.out.println("La ruta no es válida.");
        return;
    }

    for (int i = 1; i <= n; i++) {
        String nombreArchivo = ruta + "/nombre" + i + ".txt";
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(nombreArchivo))) {
            writer.write("Este es el fichero nombre" + i + ".txt");
        } catch (IOException e) {
            System.out.println("Error al crear el archivo.");
        }
    }
}
```

### 📊 Flujo del Programa

1. **Validación de la Ruta**: Se verifica si la ruta proporcionada es un directorio válido.
    - Si no es válida, se muestra un mensaje y se sale del método.
  
2. **Creación de Archivos**: Se itera desde `1` hasta `n`, creando un archivo en cada iteración.
    - Se genera el nombre del archivo.
    - Se crea el archivo y se escribe la frase correspondiente.

3. **Manejo de Excepciones**: Se captura cualquier excepción de tipo `IOException` y se muestra un mensaje de error.

### 🔄 Ejecución y Resultados

```java
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
import java.io.File;

public class CrearArchivos {
    public static void main(String[] args) {
        String ruta = ".";
        int n = 5;
        crearArchivos(ruta, n);
    }

    public static void crearArchivos(String ruta, int n) {
        File directorio = new File(ruta);
        if (!directorio.isDirectory()) {
            System.out.println("La ruta no es válida.");
            return;
        }

        for (int i = 1; i <= n; i++) {
            String nombreArchivo = ruta + "/nombre" + i + ".txt";
            try (BufferedWriter writer = new BufferedWriter(new FileWriter(nombreArchivo))) {
                writer.write("Este es el fichero nombre" + i + ".txt");
            } catch (IOException e) {
                System.out.println("Error al crear el archivo.");
            }
        }
    }
}
```

- Al ejecutar el programa, se crean 5 archivos en la carpeta actual con los nombres `nombre1.txt`, `nombre2.txt`, etc.
- Cada archivo contiene la frase "Este es el fichero nombreX.txt".

### 🛠️ Mejoras y Consideraciones

- Se valida si la ruta es un directorio antes de entrar al bucle `for`.
- Se utiliza un `BufferedWriter` para hacer la escritura más eficiente.

Con este enfoque, el código y el ejercicio quedan bien estructurados y fáciles de entender.

---

## 📚 3. Contar Ocurrencias de Palabras en un Archivo de Texto: Tercer Ejercicio

### 📝 Objetivo del Ejercicio

Crear un método que permita buscar y contar la cantidad de veces que una palabra específica aparece en un archivo de texto. Se debe utilizar un buffer para la lectura del archivo.

### 🛠️ Preparación

1. **Método Invocado**: `cantidadDePalabras`
2. **Parámetros**: 
    - Nombre del archivo: `archivo.txt`
    - Palabra a buscar: `programación`

### 📃 Código Principal

```java
public static void main(String[] args) {
    cantidadDePalabras("archivo.txt", "programación");
}
```

### 📑 Método `cantidadDePalabras`

#### Variables

- `contador`: Almacena el número de veces que la palabra aparece en el archivo.

#### Bloque Try-Catch

- **Try**: 
    1. Inicializa un `BufferedReader` envuelto alrededor de un `FileReader`.
    2. Utiliza un `Scanner` para más flexibilidad en la lectura del archivo.
- **Catch**: 
    - Captura excepciones de tipo `IOException` y muestra un mensaje de error.

#### Proceso de Lectura y Conteo

1. **Bucle Externo**: Recorre cada línea del archivo.
    - Utiliza `hasNextLine` para verificar si hay más líneas por leer.
2. **Bucle Interno**: Recorre cada palabra de la línea actual.
    - Utiliza `split` para dividir la línea en palabras.
    - Compara cada palabra con la palabra objetivo usando `equals`.

#### Cierre de Recursos

- Cierra el `Scanner` al finalizar la lectura.

### 📊 Resultados

- El método muestra el número de veces que la palabra objetivo aparece en el archivo.

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.Scanner;

public class Ejercicio3FicherosTexto {

    public static void main(String[] args) {

        cantidadPalabras("archivo.txt", "88");
    }

    // Crea un método que debe crear n archivos, nombre(1).txt, nombre(2).txt,....
    // nombre(n).txt en la carpeta que se solicita al usuario. Dentro de cada
    // archivo deberá escribirse la frase “Este es el fichero nombre(n).txt”.
    // Utiliza un búfer para la lectura
    public static void cantidadPalabras(String nombreArchivo, String palabraBuscada) {
        int contador = 0;
        try {
            BufferedReader br = new BufferedReader(new FileReader(nombreArchivo));
            Scanner scn = new Scanner(br);
            while (scn.hasNextLine()) {
                String[] palabrasLinea = scn.nextLine().split("\\s+");
                for (String palabraActual : palabrasLinea) {
                    if (palabraActual.equals(palabraBuscada)) {
                        contador++;
                    }
                }
            }
            scn.close();
        } catch (IOException e) {
            System.out.println("Ocurrió un error al leer el archivo " + nombreArchivo);
        }
        System.out.println("La palabra '" + palabraBuscada + "' aparece " + contador + " veces en el archivo.");
    }
}
```


#### Ejemplos de Uso

- Con la palabra `programación`, muestra que aparece 2 veces.
- Con la palabra `aa`, muestra que aparece 4 veces.
- Con el número `88`, muestra que aparece 1 vez.

### 📌 Notas

- La palabra debe coincidir exactamente, incluyendo acentos y mayúsculas, para ser contada.

### 🔄 Resumen

Este método es útil tanto para buscar palabras como números en un archivo de texto, y muestra de manera eficiente el número de veces que la palabra o número objetivo aparece en el archivo.


___

---
## 📚 4.  Eliminar Palabras en un Archivo de Texto: Ejercicio Cuatro

### 📝 Objetivo del Ejercicio

Crear un método que elimine todas las ocurrencias de una palabra específica en un archivo de texto. El archivo original no debe ser modificado; en su lugar, se generará un nuevo archivo con las palabras eliminadas.

### 🛠️ Preparación

1. **Método Invocado**: `eliminarPalabras`
2. **Parámetros**: 
    - Nombre del archivo: `archivo.txt`
    - Palabra a eliminar: `Sd`

### 📃 Código Principal

```java
public static void main(String[] args) {
    eliminarPalabras("archivo.txt", "SD");
}
```

### 📑 Método `eliminarPalabras`

#### Bloques Try-Catch

- **Try**: 
    - Contiene el código principal para la eliminación de palabras.
- **Catch**: 
    - Captura excepciones y muestra mensajes de error específicos.

#### Validación del Archivo

- Verifica si el archivo existe y si es un archivo válido.
- Si no, lanza una excepción.

#### Inicialización de Recursos

- `BufferedReader`: Para leer el archivo original.
- `BufferedWriter`: Para escribir en el nuevo archivo.

#### Proceso de Lectura y Escritura

1. **Nombre del Nuevo Archivo**: 
    - Utiliza `replace` para cambiar `.txt` por `_2.txt`.
2. **Bucle de Lectura y Escritura**: 
    - Utiliza un `Scanner` para leer el archivo original.
    - Utiliza `BufferedWriter` para escribir en el nuevo archivo.

#### Detalles del Proceso

- Utiliza `replaceAll` para eliminar todas las ocurrencias de la palabra.
- Opción de usar `\b` para eliminar solo palabras completas.

#### Cierre de Recursos

- Cierra tanto el `Scanner` como el `BufferedWriter`.

### 📊 Resultados

- Genera un nuevo archivo con las palabras eliminadas.

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

public class Ejercicio4FicherosTexto {

    public static void main(String[] args) {

        eliminarPalabras("archivo.txt", "Sd");
    }

    // Crea un método que permita eliminar todas las ocurrencias de una palabra dada
    // en un fichero de texto. Este código producirá automáticamente un nuevo
    // fichero con la siguiente nomenclatura: Si el fichero de entrada se llama
    // fichero.txt, el fichero generado se llamará fichero_2.txt.
    public static void eliminarPalabras(String nombreFichero, String palabra) {

        try {
            File fichero = new File(nombreFichero);
            if (!fichero.exists() || !fichero.isFile()) {
                throw new FileNotFoundException();
            }

            // lector del fichero origen
            BufferedReader br = new BufferedReader(new FileReader(nombreFichero));
            Scanner scn = new Scanner(br);

            // escritor del fichero destino
            String nombreFicheroNuevo = nombreFichero.replace(".txt", "_2.txt");
            BufferedWriter bw = new BufferedWriter(new FileWriter(nombreFicheroNuevo));

            String linea;
            while (scn.hasNextLine()) {
                linea = scn.nextLine().replaceAll(palabra, "");
                bw.write(linea+"\n");
            }
            scn.close();
            bw.close();

        } catch (FileNotFoundException e) {
            System.out.println("El archivo " + nombreFichero + " no existe o no es un archivo válido");
        } catch (IOException e) {
            System.out.println("Ocurrió un error al procesar el archivo");
        }
    }
}
```

#### Ejemplos de Uso

- Con `\b`: Elimina solo las palabras completas que coinciden.
- Sin `\b`: Elimina todas las ocurrencias, incluso si son parte de otra palabra.

### 📌 Notas

- La coincidencia debe ser exacta, incluyendo mayúsculas y minúsculas.

### 🔄 Resumen

Este método ofrece flexibilidad en la eliminación de palabras, permitiendo opciones para eliminar solo palabras completas o todas las ocurrencias. Genera un nuevo archivo sin modificar el original, y maneja errores de manera efectiva.

---

## 🛡️5.  Encriptar y Desencriptar con Código César: Ejercicio Cinco

### 🎯 Objetivo del Ejercicio

Desarrollar dos métodos: uno para encriptar y otro para desencriptar el contenido de un archivo de texto utilizando el Código César.

#### 📜 Código César

- Desplaza cada letra en el alfabeto una cantidad determinada de veces.
- Ejemplo: Con un desplazamiento de 2, la `a` se convierte en `c`.

### 🛠️ Preparación

1. **Constantes Estáticas**: 
    - `DESPLAZAMIENTO`: 3
    - `NOMBRE_DE_FICHERO`: Nombre del archivo a encriptar/desencriptar.

### 📃 Código Principal

```java
public static void main(String[] args) {
    encriptarArchivo("fichero.txt");
    desencriptarArchivo("fichero_encriptado.txt");
}
```

### 📑 Métodos `encriptarArchivo` y `desencriptarArchivo`

#### Método Común: `procesarArchivo`

- Acepta un booleano para determinar si se debe encriptar o desencriptar.
- Reutilizable para ambos métodos.

#### Bloques Try-Catch

- Manejo de excepciones similar al ejercicio anterior.

### 📋 Proceso de Encriptación/Desencriptación

1. **Validación del Archivo**: Verifica si el archivo existe y es válido.
2. **Inicialización de Recursos**: 
    - `BufferedReader` para lectura.
    - `BufferedWriter` para escritura.
3. **Bucle de Procesamiento**: 
    - Lee cada carácter y lo encripta o desencripta según el caso.

```java
while ((datos = lector.read()) != -1) {
    char c = (char) datos;
    if (estaEncriptado) {
        escritor.write(c - DESPLAZAMIENTO); // desencriptamos
    } else {
        escritor.write(c + DESPLAZAMIENTO); // encriptamos
    }
}
```

4. **Cierre de Recursos**: Cierra `BufferedReader` y `BufferedWriter`.

### 📊 Resultados

- Genera un archivo encriptado y otro desencriptado.
- Los archivos original y desencriptado deben ser idénticos.

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

public class Ejercicio5FicherosTexto {

    private static final int DESPLAZAMIENTO = 3;
    private static final String NOMBRE_FICHERO = "fichero.txt";

    public static void main(String[] args) {

        encriptarArchivo(NOMBRE_FICHERO, "fichero_encriptado.txt");
        desencriptarArchivo("fichero_encriptado.txt", "fichero_desencriptado.txt");
    }

    // método que desencripta datos en el archivo con código césar = DESPLAZAMIENTO
    public static void desencriptarArchivo(String rutaEntrada, String rutaSalida) {
        procesarArchivo(rutaEntrada, rutaSalida, true);
    }

    // método que encripta datos en el archivo con código césar = DESPLAZAMIENTO
    public static void encriptarArchivo(String rutaEntrada, String rutaSalida) {
        procesarArchivo(rutaEntrada, rutaSalida, false);
    }

    // método que encripta/desencripta en base al booleano
    public static void procesarArchivo(String rutaEntrada, String rutaSalida, boolean estaEncriptado) {
        try {
            File archivoEntrada = new File(rutaEntrada);
            if (!archivoEntrada.exists() || !archivoEntrada.isFile()) {
                throw new FileNotFoundException();
            }

            File archivoSalida = new File(rutaSalida);
            BufferedReader lector = new BufferedReader(new FileReader(archivoEntrada));
            BufferedWriter escritor = new BufferedWriter(new FileWriter(archivoSalida));

            int datos;
            while ((datos = lector.read()) != -1) {
                char c = (char) datos;
                if (estaEncriptado)
                    escritor.write(c - DESPLAZAMIENTO); // desencriptamos
                else
                    escritor.write(c + DESPLAZAMIENTO); // encriptamos
            }
            lector.close();
            escritor.close();

        } catch (FileNotFoundException e) {
            System.out.println("ERROR: el fichero no existe o no es un archivo válido");
        } catch (IOException e) {
            System.out.println("Ocurrió un error al procesar el archivo");
        }
    }

}
```

#### Ejemplo de Uso

- `fichero.txt` se encripta en `fichero_encriptado.txt`.
- `fichero_encriptado.txt` se desencripta en `fichero_desencriptado.txt`.

### 📌 Notas

- Los caracteres especiales se convierten en caracteres no legibles en el archivo encriptado.
- El método muestra mensajes de error específicos para diferentes tipos de excepciones.

### 🔄 Resumen

Este ejercicio demuestra cómo encriptar y desencriptar un archivo de texto utilizando el Código César. Utiliza un método común para realizar ambas operaciones, lo que hace que el código sea más eficiente y fácil de mantener.

___
%%
tags: #java  #pagacceso_a_datos  #Java #Archivos #Extensión #Método #Sobrecarga #CódigoPrincipal #PasosDelMétodo #Resultados #ObjetivoDelEjercicio #Especificaciones #FlujoDelPrograma #MejorasYConsideraciones #ContarOcurrencias #Preparación #Variables #BloqueTryCatch #ProcesoDeLecturaYConteo #EjemplosDeUso #EliminarPalabras #ValidaciónDelArchivo #InicializaciónDeRecursos #ProcesoDeLecturaYEscritura #EncriptarYDesencriptar #CódigoCésar #ProcesoDeEncriptación #Desencriptación #Notas #Resumen
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%