---
ID: 23
nombre: Excepciones en Ficheros
tags:
  - pagacceso_a_datos
---
___
![[d 7X502QjN.svg]]

### 🎯 Tipos de Excepciones en Ficheros 🌟

Las excepciones en el manejo de ficheros se pueden clasificar principalmente en dos categorías:

1. **Excepciones al Abrir Archivos**: Se originan cuando hay problemas al intentar abrir un archivo.
    - ***Ejemplo de Excepción***: `FileNotFoundException`

2. **Excepciones al Leer o Escribir en Archivos**: Ocurren durante las operaciones de lectura o escritura en un archivo.
    - ***Ejemplo de Excepción***: `EOFException`

Ambas categorías de excepciones son subclases de la clase `IOException`.

### 🛠️ Cómo Manejar `FileNotFoundException` 📘

Existen dos enfoques para manejar esta excepción:

1. **Manejo Local de la Excepción**: Se maneja la excepción dentro de la misma función donde se crea el objeto de archivo.

    ```java
    public void leerArchivo() {
        try {
            FileReader fr = new FileReader(archivo);
        } catch (FileNotFoundException e) {
            // Código de manejo de excepción
        }
    }
    ```

2. **Propagación de la Excepción**: Se propaga la excepción para que sea manejada fuera de la función donde se crea el objeto de archivo.

    ```java
    public void leerArchivo() throws FileNotFoundException {
        FileReader fr = new FileReader(archivo);
    }
    ```
    - ***Manejo Externo***:
        ```java
        try {
            leerArchivo();
        } catch (FileNotFoundException e) {
            // Código de manejo de excepción
        }
        ```

### 🌠 EOFException: Excepción de Fin de Archivo 🌌

La excepción `EOFException` se produce cuando se alcanza el final del archivo durante una operación de lectura.

- ***Ejemplo de Uso***: Ocurre típicamente en métodos como `readInt()`.

### 🚀 Consideraciones Finales 🌟

- Siempre es recomendable manejar excepciones para garantizar la robustez de la aplicación.
- Las excepciones como `FileNotFoundException` y `EOFException` son específicas y deben ser manejadas de manera adecuada para evitar interrupciones en el flujo del programa.

___
%%
tags: #java  #pagacceso_a_datos  #Excepciones #Ficheros #Java #FileNotFoundException #EOFException #IOException #ManejoLocal #Propagación #ConsideracionesFinales
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%