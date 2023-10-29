---
ID: 40
nombre: 
tags:
  - pagacceso_a_datos
---
___
![](https://www.youtube.com/watch?v=ov2EoNfxIdA&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=179&ab_channel=Aulaenlanube)
## 📚 Trabajar con Ficheros Binarios en Java

### 📝 Introducción
En este primer vídeo, nos enfocamos en cómo trabajar con ficheros binarios en Java. Abordaremos cómo escribir y extraer datos asociados a tipos primitivos de Java, como `String` e `int`. En futuros vídeos, exploraremos cómo escribir datos de objetos en ficheros binarios y el proceso de serialización.

### 🎯 Objetivos
- Escribir datos asociados a tipos primitivos en ficheros binarios.
- Extraer datos escritos en ficheros binarios.
- Introducción a la serialización (a cubrir más adelante).

### 💾 Almacenamiento en Ficheros Binarios
El almacenamiento en ficheros binarios implica guardar datos directamente en formato binario, es decir, como secuencias de bits (ceros y unos). Estos bits se agrupan en bloques de 8 para formar bytes.

#### 📊 Tipos de Datos y Bytes Necesarios
- `int`: 4 bytes
- `double`: 8 bytes
- `byte`: 1 byte (rango de -128 a 127)
- 
![[Pasted image 20231015152134.png]]

#### 🤔 Consideraciones
- Elegir el tipo de variable adecuado para evitar desperdicio de espacio.
- Los dispositivos de almacenamiento actuales tienen gran capacidad, pero es mejor ser eficiente.

### 🚀 Eficiencia del Almacenamiento Binario
El almacenamiento binario es más eficiente en términos de espacio y tiempo de procesamiento porque:
- No requiere conversión adicional.
- El hardware solo entiende código binario.

#### ⚠️ Desventajas
- Los ficheros binarios no son legibles directamente por humanos.
- Pueden ser incompatibles con otros lenguajes de programación o sistemas operativos.

### 📦 Serialización en Java
La serialización es el proceso de convertir un objeto en un flujo de bits para almacenarlo en un archivo. En Java, se utilizan las clases `ObjectOutputStream` y `ObjectInputStream` para este propósito.

```java
// Ejemplo de serialización en Java
ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("archivo.bin"));
oos.writeObject(objeto);
```

#### 📌 Nota
Para que un objeto sea serializable, la clase debe implementar la interfaz `Serializable`.
___
___
## 📚 Escritura y Lectura de Tipos Primitivos en Java

### 📝 Introducción
En esta sección, nos adentraremos en el proceso de escritura y lectura de tipos primitivos en Java, como `boolean`, `int`, `float`, y `String`. Utilizaremos las clases `DataInputStream` y `DataOutputStream` del paquete `java.io`.

### 🛠 Herramientas y Clases Utilizadas

#### 📦 Clases para Manejo de Ficheros
- `File`: Para especificar el origen o destino de los datos.
- `FileInputStream`: Para lectura de ficheros.
- `FileOutputStream`: Para escritura de ficheros.

#### 📦 Clases para Datos Primitivos
- `DataInputStream`: Para lectura de tipos primitivos.
- `DataOutputStream`: Para escritura de tipos primitivos.

#### 🗂 Opciones de Constructores
- Aceptan una instancia de `File`.
- Aceptan una `String` con el nombre del fichero.

```java
// Ejemplo de creación de DataInputStream y DataOutputStream
FileInputStream fis = new FileInputStream("input.bin");
DataInputStream dis = new DataInputStream(fis);

FileOutputStream fos = new FileOutputStream("output.bin");
DataOutputStream dos = new DataOutputStream(fos);
```

### 📖 Proceso de Escritura y Lectura

#### 📝 Escritura de Datos

1. **Crear un `File`**: Especificar el destino de los datos.
2. **Envolver con `FileOutputStream`**: Para escribir en el fichero.
3. **Envolver con `DataOutputStream`**: Para escribir tipos primitivos.

##### 🛠 Métodos de Escritura
- `writeInt()`: Para escribir enteros.
- `writeDouble()`: Para escribir doubles.

```java
// Ejemplo de escritura de datos primitivos
dos.writeInt(42);
dos.writeDouble(3.14);
```

#### 📝 Lectura de Datos

1. **Crear un `File`**: Especificar el origen de los datos.
2. **Envolver con `FileInputStream`**: Para leer del fichero.
3. **Envolver con `DataInputStream`**: Para leer tipos primitivos.

##### 🛠 Métodos de Lectura
- `readInt()`: Para leer enteros.
- `readDouble()`: Para leer doubles.

```java
// Ejemplo de lectura de datos primitivos
int num = dis.readInt();
double pi = dis.readDouble();
```

### 📌 Notas Adicionales
- Los constructores de `FileInputStream` y `FileOutputStream` también aceptan una `String` como parámetro, eliminando la necesidad de crear una instancia de `File`.

___
___
## 📚 Lectura en Archivos Binarios en Java

### 📝 Introducción
En esta sección, exploraremos un ejemplo de lectura en archivos binarios en Java. Abordaremos cómo leer tipos primitivos y la importancia de conocer la estructura interna del archivo para una lectura efectiva.

### 🎯 Objetivos
- Entender cómo leer tipos primitivos como `int`, `float`, `char`, etc.
- Comprender la importancia de conocer la estructura interna del archivo binario.

### 📖 Importancia de la Estructura Interna

#### 🤔 ¿Por qué es crucial?
Para leer un archivo binario de manera efectiva, es esencial conocer su estructura interna. Es decir, necesitamos saber qué tipo de datos se ha escrito primero y en qué orden.

#### 📊 Ejemplo
Si un archivo binario contiene un `int` seguido de un `double`, debemos leer primero 4 bytes para el `int` y luego 8 bytes para el `double`.

### 🛠 Herramientas y Métodos de Lectura

#### 📦 Clases y Métodos
- `FileInputStream`: Para leer datos del archivo.
- `read()`: Método que lee un byte y lo devuelve como entero. Devuelve -1 si no hay más datos para leer.

```java
// Ejemplo de lectura byte a byte
FileInputStream fis = new FileInputStream("archivo.bin");
int num;
while ((num = fis.read()) != -1) {
    System.out.print(num + " ");
}
```

#### 📌 Nota
Si solo queremos leer byte a byte, no es necesario usar `DataInputStream`.

### 🚀 Ejemplo Práctico

#### 📝 Código de Ejemplo
En este ejemplo, leemos un archivo llamado `ejemplo.dat` y mostramos los valores enteros de cada byte.

```java
// Leer datos desde el archivo binario
try{
	// Ejemplo de lectura de archivo binario
	FileInputStream fis = new FileInputStream("ejemplo.dat");
	int num;
	System.out.println("Datos leídos desde el archivo binario:");
	while ((num = fis.read()) != -1) {
	    System.out.print(num + " ");
	}
}catch (IOException e) {
	System.err.println("Error al leer");
}
```

#### 📊 Resultado
El archivo `ejemplo.dat` ocupa 18 bytes, y cada byte se muestra como un valor entero.

### 📌 Desafíos y Consideraciones

#### ⚠️ Limitaciones
- Sin conocer la estructura interna del archivo, no podemos interpretar los datos de manera significativa.

#### 📋 Tareas Pendientes
- Interpretar y procesar los datos leídos para entender su significado.

___
___
## 📚 Trabajando con `DataOutputStream` en Java

### 📝 Introducción
En esta sección, exploraremos los métodos clave de la clase `DataOutputStream` en Java. También abordaremos cómo estos métodos interactúan con diferentes tipos de datos primitivos.

### 🎯 Objetivos
- Comprender los métodos de la clase `DataOutputStream`.
- Entender cómo escribir diferentes tipos de datos primitivos en archivos binarios.

### 🛠 Métodos de `DataOutputStream`

#### 📦 Constructor y Métodos Básicos
- `DataOutputStream`: Constructor que envuelve un `OutputStream`.
- `writeInt(int i)`: Escribe un entero utilizando 4 bytes.
- `writeLong(long l)`: Utiliza 8 bytes para escribir un `long`.

```java
// Ejemplo de uso del constructor y métodos básicos
DataOutputStream dos = new DataOutputStream(new FileOutputStream("archivo.bin"));
dos.writeInt(42);
dos.writeLong(123456789L);
```

#### 📝 Método para Strings: `writeUTF`
- Escribe una cadena en representación UTF-8.
- Primero escribe la longitud de la cadena utilizando 2 bytes.

```java
// Ejemplo de uso de writeUTF
dos.writeUTF("Hola mundo");
```

#### 📊 Nota sobre `writeUTF`
- Los caracteres de la cadena pueden ocupar 1, 2 o 3 bytes, dependiendo del tipo de carácter.
- Diseñado para minimizar el espacio de memoria requerido.

### 📖 Métodos para Números Reales

#### 📈 Float y Double
- `writeFloat(float f)`: Utiliza 4 bytes para escribir un `float`.
- `writeDouble(double d)`: Utiliza 8 bytes para escribir un `double`.

```java
// Ejemplo de uso de writeFloat y writeDouble
dos.writeFloat(3.14f);
dos.writeDouble(2.71828);
```

### 🔄 Métodos Correspondientes en `DataInputStream`

- Los métodos para leer datos son similares pero con el prefijo `read` en lugar de `write`.
  - Ejemplo: `readInt()`, `readUTF()`, etc.

### 🚀 Ejemplo Adicional: `writeUTF`

#### 📝 Código de Ejemplo
Este método se utiliza para escribir una cadena en el archivo binario. La longitud de la cadena se almacena primero utilizando 2 bytes.

```java
// Ejemplo de uso de writeUTF
dos.writeUTF("Hola, este es un ejemplo");
```

#### 📌 Nota
- La longitud de la cadena determina la cantidad de bytes que ocupará.

### 📌 Consideraciones y Excepciones

#### ⚠️ Excepciones
- `DataOutputStream` y `DataInputStream` pueden lanzar una excepción de tipo `FileNotFoundException`.

___
___
## 📚 Trabajando con Archivos Binarios en Java: Ejemplo Práctico

### 📝 Introducción
En esta última sección, vamos a explorar un ejemplo práctico que demuestra cómo escribir y leer diferentes tipos de variables primitivas en un archivo binario usando Java.

### 🎯 Objetivos
- Crear un archivo binario y escribir datos en él.
- Leer los datos del archivo binario.
- Utilizar un buffer para mejorar la eficiencia de la escritura.

### 🛠 Herramientas y Métodos

#### 📦 Creación de Variables
1. Crear cuatro variables de diferentes tipos: `boolean`, `String`, `int`, `double`.

#### 📝 Escritura en Archivo Binario
1. Crear un `FileOutputStream`.
   ```java
   new FileOutputStream("ejemplo.dat");
   ```
2. Envolverlo en un `DataOutputStream`.
   ```java
   new DataOutputStream(FileOutputStream);
   ```
3. Utilizar los métodos `writeBoolean`, `writeUTF`, `writeInt`, `writeDouble` para escribir las variables.
4. Cerrar el `DataOutputStream`.

#### 📖 Lectura desde Archivo Binario
1. Crear un `FileInputStream`.
   ```java
   new FileInputStream("ejemplo.dat");
   ```
2. Envolverlo en un `DataInputStream`.
   ```java
   new DataInputStream(FileInputStream);
   ```
3. Utilizar los métodos `readBoolean`, `readUTF`, `readInt`, `readDouble` para leer las variables.
   - Importante: Leer en el mismo orden en que se escribieron.
4. Mostrar los datos leídos en la consola.

#### 🚀 Uso de Buffer
- Envolver el `FileOutputStream` en un `BufferedOutputStream` para almacenar datos temporalmente en memoria antes de escribirlos en el disco.

### 🎓 Ejemplo Extendido
- Se muestra cómo los datos se almacenan en el archivo binario.
- Se explica la representación en bytes de cada tipo de variable.
```java 
import java.io.*;

public class Main {
    public static void main(String[] args) {
        // Creación de Variables
        boolean aprobado = true;
        String nombre = "PNG";
        int convocatoria = 1;
        double nota = 7.8;

        // Escritura en Archivo Binario
        try {
            FileOutputStream fos = new FileOutputStream("ejemplo.dat");
            DataOutputStream dos = new DataOutputStream(fos);

            dos.writeBoolean(aprobado);
            dos.writeUTF(nombre);
            dos.writeInt(convocatoria);
            dos.writeDouble(nota);

            dos.close();
        } catch (IOException e) {
            e.printStackTrace();
        }

        // Lectura desde Archivo Binario
        try {
            FileInputStream fis = new FileInputStream("ejemplo.dat");
            DataInputStream dis = new DataInputStream(fis);

            boolean aprobadoLeido = dis.readBoolean();
            String nombreLeido = dis.readUTF();
            int convocatoriaLeida = dis.readInt();
            double notaLeida = dis.readDouble();

            System.out.println("Valor leído de aprobado: " + aprobadoLeido);
            System.out.println("Valor leído de nombre: " + nombreLeido);
            System.out.println("Valor leído de convocatoria: " + convocatoriaLeida);
            System.out.println("Valor leído de nota: " + notaLeida);

            dis.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```
  
### 📊 Datos en Binario
- `boolean`: 1 byte (1 para true, 0 para false)
- `String`: 2 bytes para la longitud + 1-3 bytes por carácter
- `int`: 4 bytes
- `double`: 8 bytes

### 📈 Eficiencia con Buffer
- Es más eficiente escribir 100 KB de una vez que hacer 100 escrituras de 1 byte cada una.

___
___
## 📚 Trabajando con Strings y Almacenamiento en Ficheros Binarios en Java

### 📝 Ejemplo de Codificación de Caracteres en Strings

Para entender cómo se almacenan las `Strings` en un fichero binario, he creado tres `Strings` diferentes: `datos1`, `datos2` y `datos3`. Cada una de estas `Strings` tiene una primera letra 'a' seguida de un carácter con un valor Unicode específico:

- `datos1`: Valor Unicode de 56 (ocupa 1 byte)
- `datos2`: Valor Unicode de 159 (ocupa 2 bytes)
- `datos3`: Valor Unicode de 1000 (ocupa 3 bytes)

#### 📊 Espacio en Memoria

Si ejecutamos el código, podemos observar que el archivo `datos.dat` ocupa 15 bytes. Aquí está el desglose:

- `datos1`: 4 bytes (2 para longitud + 2 para caracteres)
- `datos2`: 5 bytes (2 para longitud + 3 para caracteres)
- `datos3`: 6 bytes (2 para longitud + 4 para caracteres)

### 🛠️ Experimentos con el Tamaño del Archivo

Si eliminamos `datos2` y `datos3`, el archivo ocupará 4 bytes. Si dejamos solo `datos2`, ocupará 5 bytes, y si dejamos solo `datos3`, ocupará 6 bytes.

### 🎛️ Limitaciones de Byte y Enteros

Es importante tener en cuenta que el valor de un byte siempre debe estar entre 0 y 255, ya que un byte está formado por 8 bits. Esto genera 256 combinaciones posibles. Por ejemplo, si asignamos un valor entero de un millón a una variable, los datos en binario mostrarán que ningún valor de byte supera 255.

#### 📜 Ejemplo de Código

```java
package aulaenlanube.tema8.ejemplos.ficheros;

import java.io.DataOutputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class EjemploWriteUTF {

    public static void main(String[] args) {

        String fichero = "datos.dat";

        String datos1 = "a\u0056";
        System.out.println(datos1);

        String datos2 = "a\u0159";
        System.out.println(datos2);
        
        String datos3 = "a\u1000";
        System.out.println(datos3);

        try {
            DataOutputStream out = new DataOutputStream(new FileOutputStream(fichero));
            out.writeUTF(datos1);
            out.writeUTF(datos2);
            out.writeUTF(datos3);
            out.close();

        } catch (IOException e) {
            System.out.println("ERROR");
        }

    }
}

```

___
%%
tags: #java  #pagacceso_a_datos  #Java #FicherosBinarios #Introducción #Objetivos #Almacenamiento #TiposDeDatos #Bytes #Consideraciones #Eficiencia #Desventajas #Serialización #ObjectOutputStream #ObjectInputStream #Serializable #Escritura #Lectura #TiposPrimitivos #DataInputStream #DataOutputStream #File #FileInputStream #FileOutputStream #Constructores #MétodosDeEscritura #MétodosDeLectura #NotasAdicionales #EstructuraInterna #Herramientas #MétodosDeLectura #Limitaciones #TareasPendientes #DataOutputStream #Métodos #Constructor #MétodosBásicos #writeInt #writeLong #writeUTF #NúmerosReales #Float #Double #Excepciones #FileNotFoundException #EjemploPráctico #Buffer #EficienciaConBuffer #Strings #Almacenamiento #CodificaciónDeCaracteres #EspacioEnMemoria #Experimentos #TamañoDelArchivo #LimitacionesDeByte #Enteros #Código #EjemploWriteUTF
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%