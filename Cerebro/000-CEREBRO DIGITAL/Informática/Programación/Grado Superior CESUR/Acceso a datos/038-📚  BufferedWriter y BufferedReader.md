---
ID: 38
nombre: BufferedWriter y BufferedReader
tags:
  - pagacceso_a_datos
---
___
![](https://www.youtube.com/watch?v=LeLR8C8FsUE&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=177&ab_channel=Aulaenlanube)

---

### 📚 Conceptos Clave

#### 📝 BufferedWriter
- **Función**: Utilizado para escribir texto en ficheros de manera eficiente.
- **Uso de Buffer**: Almacena datos en un buffer para minimizar las operaciones de escritura en disco.
- **Ejemplo de Código**:
  ```java
  BufferedWriter bw = new BufferedWriter(new FileWriter("file.txt"));
  bw.write("Hello World");
  bw.close();
  ```

#### 📝 BufferedReader
- **Función**: Utilizado para leer texto de ficheros de manera eficiente.
- **Uso de Buffer**: Almacena datos en un buffer para minimizar las operaciones de lectura en disco.
- **Ejemplo de Código**:
  ```java
  BufferedReader br = new BufferedReader(new FileReader("file.txt"));
  String line = br.readLine();
  br.close();
  ```

---

### 🛠 Ejemplos Prácticos

#### 📌 Ejercicio 1: Uso de BufferedWriter
- **Objetivo**: Crear un archivo y escribir líneas numeradas en él.
- **Código de Ejemplo**:
  ```java
  public static void crearLineas(String nombreFichero, int numLineas) {
    BufferedWriter bw = new BufferedWriter(new FileWriter(nombreFichero));
    for(int i = 1; i <= numLineas; i++) {
      bw.write("Esta es la línea " + i);
      bw.newLine();
    }
    bw.close();
  }
  ```

#### 📌 Ejercicio 2: Uso de BufferedReader
- **Objetivo**: Leer un archivo y contar el número de palabras en él.
- **Código de Ejemplo**:
  ```java
  public static void contarPalabras(String nombreArchivo) {
    BufferedReader br = new BufferedReader(new FileReader(nombreArchivo));
    String line;
    int palabras = 0;
    while((line = br.readLine()) != null) {
      palabras += line.split(" ").length;
    }
    br.close();
    System.out.println("Total palabras: " + palabras);
  }
  ```

---

### 📋 Resumen de Métodos

| Método | Clase | Descripción |
|--------|-------|-------------|
| `readLine()` | BufferedReader | Lee una línea completa del archivo. |
| `write(String s)` | BufferedWriter | Escribe una cadena en el archivo. |
| `newLine()` | BufferedWriter | Inserta un salto de línea. |
| `close()` | Ambas | Cierra el flujo de lectura/escritura. |

---

### 📌 Notas Adicionales
- Se puede utilizar la clase `Scanner` en combinación con `BufferedReader` para más versatilidad.
- El método `flush()` se utiliza para vaciar el buffer y escribir todo lo almacenado en el fichero.


___
%%
tags: #java  #pagacceso_a_datos  #Java #BufferedWriter #BufferedReader #DAM #DAW #Programación #FicherosDeTexto #Eficiencia #Lectura #Escritura #EjemplosPrácticos #Métodos #Scanner #Flush
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%