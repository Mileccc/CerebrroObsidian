---
ID: 35
nombre: La Clase File en Detalle
tags:
  - pagacceso_a_datos
---
___
#### Clase File
![](https://www.youtube.com/watch?v=2GjrBo2SRP8&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=173&ab_channel=Aulaenlanube)

#### Ejemplos de usos de los métodos de la Clase File
![](https://www.youtube.com/watch?v=0tN_yrTwLPY&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=174&ab_channel=Aulaenlanube)
___

### 📖 Introducción

La clase `File` en Java es una herramienta esencial para manipular archivos y directorios en el sistema operativo. Este tutorial abarca desde la creación de instancias de la clase `File` hasta las operaciones más comunes que puedes realizar con ella.

### 🗂 Creación de Instancias de la Clase `File`

Para trabajar con archivos y directorios, primero debes crear una instancia de la clase `File`. Aquí hay dos formas de hacerlo:

1. Utilizando una ruta completa con el nombre del archivo incluido.
   ```java
   File archivo1 = new File("ruta/alt/archivo.txt");
   ```
2. Utilizando un constructor que recibe dos parámetros: la ruta y el nombre del archivo.
   ```java
   File archivo2 = new File("ruta/alt", "archivo.txt");
   ```

### 🛠 Operaciones Básicas con Archivos y Directorios

#### Leer y Escribir Datos

- La clase `File` no se utiliza para leer o escribir datos en el archivo. Para eso, se utilizan otras clases que necesitan una instancia de `File`.
  
#### Métodos Útiles

- `createNewFile()`: Crea un nuevo archivo vacío.
- `delete()`: Borra un archivo o directorio.
- `exists()`: Verifica si el archivo o directorio existe.
- `getName()`: Obtiene el nombre del archivo o directorio.
- `length()`: Obtiene el tamaño del archivo.

### 📁 Trabajando con Directorios

- Puedes crear instancias de `File` que representen tanto archivos como directorios.
- Para borrar un directorio, este debe estar vacío.

#### Métodos para Directorios

- `listFiles()`: Obtiene un array de instancias de la clase `File` con los archivos en un directorio.
- `isDirectory()`: Verifica si la instancia representa un directorio.

### 🛤 Rutas Absolutas y Relativas

- Ruta Absoluta: Especifica la ubicación exacta en el sistema de archivos.
  ```java
  File carpetaRaiz = new File("C:/users");
  ```
- Ruta Relativa: Especifica la ubicación en relación con un punto de partida.
  ```java
  File carpetaRelativa = new File("../users");
  ```

### 🔄 Flujos y Canales

- `java.io` utiliza flujos unidireccionales.
- `java.nio` utiliza canales bidireccionales.

### 🚫 Operaciones Bloqueantes vs No Bloqueantes

- `java.io` tiene operaciones bloqueantes.
- `java.nio` permite operaciones no bloqueantes.

### 📑 Conclusión

Entender la clase `File` en Java es crucial para la manipulación de archivos y directorios. Este tutorial abarca desde la creación de instancias hasta las operaciones más comunes que puedes realizar, ofreciendo un conocimiento integral para trabajar eficientemente con archivos y directorios en Java.

___
%%
tags: #java  #pagacceso_a_datos  #Java #File #ClaseFile #Instancias #OperacionesBasicas #Leer #Escribir #Metodos #Directorios #RutasAbsolutas #RutasRelativas #Flujos #Canales #OperacionesBloqueantes #OperacionesNoBloqueantes #Conclusión
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%