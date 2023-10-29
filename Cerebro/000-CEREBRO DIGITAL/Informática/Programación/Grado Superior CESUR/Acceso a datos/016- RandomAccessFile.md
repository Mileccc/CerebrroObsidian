---
"ID:": 16
-nombre: Explicación Java RandomAccessFile
tags:
  - pagacceso_a_datos
---
___

![](https://www.youtube.com/watch?v=ZusJ9y_bEe8&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=180&ab_channel=Aulaenlanube)

### 📌 Introducción al Acceso Aleatorio en Java

La clase `RandomAccessFile` en Java permite un acceso aleatorio a los datos de un archivo. Este tipo de acceso es más eficiente que el acceso secuencial, que requiere leer los datos desde el inicio hasta el final del archivo.

#### 📂 Tipos de Acceso a la Información

- **Acceso Secuencial**: 
  - Más lento.
  - Requiere leer y escribir datos en orden.
  - Utiliza clases como `FileInputStream` y `FileOutputStream` para ficheros binarios y `FileReader` y `FileWriter` para ficheros de texto.

- **Acceso Aleatorio**: 
  - Más rápido.
  - Permite acceder directamente a un dato específico.
  - Utiliza la clase `RandomAccessFile`.

### 🛠️ Funcionamiento y Ejemplo de Código

Para acceder a los datos de forma aleatoria, se utilizan registros de tamaño conocido. Podemos movernos de un registro a otro para leer o modificar datos.

```java
package aulaenlanube.tema8.ejemplos.ficheros;

import java.io.IOException;
import java.io.RandomAccessFile;

public class EjemploAccesoAleatorio {
    public static void main(String[] args) {

        try {

            RandomAccessFile raf = new RandomAccessFile("random.dat", "rw");

            for (int i = 0; i < 10; i++) {
                raf.writeInt(i);
            }

            raf.seek(19); // Mueve el puntero a la posición 20 (5 enteros * 4 bytes)

            //1-4:   (num=0) 00000000 00000000 00000000 00000000
            //5-8:   (num=1) 00000000 00000000 00000000 00000001
            //9-12:  (num=2) 00000000 00000000 00000000 00000010
            //13-16: (num=3) 00000000 00000000 00000000 00000011
            //17-20: (num=4) 00000000 00000000 00000000 00000100
            //21-24: (num=5) 00000000 00000000 00000000 00000101
            //25-28: (num=6) 00000000 00000000 00000000 00000110
            //29-32: (num=7) 00000000 00000000 00000000 00000111
            //33-36: (num=8) 00000000 00000000 00000000 00001000
            //37-40: (num=9) 00000000 00000000 00000000 00001001
            
            int sexto = raf.readInt(); //19: 00000100 00000000 00000000 00000000
            System.out.println("El entero es: " + sexto);

            raf.close();

        } catch (IOException e) {
            System.out.println("ERROR");
        }
    }
}
```

#### 📍 Notas sobre el Ejemplo

- `seek()` mueve el puntero del archivo.
- `writeInt()` y `readInt()` se utilizan para escribir y leer enteros, respectivamente.
- Cada entero ocupa 4 bytes.

### 🚨 Consideraciones y Problemas Potenciales

- Si intentas leer un byte que no es múltiplo del tamaño del registro, los datos no se leerán correctamente.
- Debes conocer la estructura exacta del archivo para acceder a los datos de forma precisa.

### 💡 Consejos y Recomendaciones

- Aunque `RandomAccessFile` es eficiente, no es adecuado para ficheros de texto que utilizan codificaciones de caracteres de múltiples bytes, como UTF-8.
- Para ficheros de texto, es mejor utilizar clases como `BufferedReader` o `BufferedWriter`.
___
%%
tags: #pagacceso_a_datos  #randomAccessFile  #Java #RandomAccessFile #AccesoAleatorio #AccesoSecuencial #FileInputStream #FileOutputStream #FileReader #FileWriter #seek #writeInt #readInt #CodificaciónUTF8 #BufferedReader #BufferedWriter #IOException #EjemploCódigo #Consideraciones #Consejos #Recomendaciones
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%