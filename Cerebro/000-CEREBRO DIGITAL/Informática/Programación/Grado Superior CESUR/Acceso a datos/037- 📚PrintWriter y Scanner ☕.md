---
ID: 37
nombre: PrintWriter y Scanner
tags:
  - pagacceso_a_datos
---
___

![](https://www.youtube.com/watch?v=ajcnc2O4f_A&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=176&ab_channel=Aulaenlanube)

___
### 📌 PrintWriter: Características y Métodos

- **Subclase de Writer**: `PrintWriter` es una subclase de la clase abstracta `Writer`.
- **Versatilidad**: Ofrece métodos para imprimir representaciones de varios tipos de datos como enteros, longs, floats, etc.
- **Métodos Útiles**:
  - `print(String s)`: Escribe una cadena sin un salto de línea.
  - `println(String s)`: Escribe una cadena con un salto de línea.
  - `close()`: Cierra el flujo de escritura y libera los recursos.

```java
PrintWriter pw = new PrintWriter(new FileWriter("file.txt"));
pw.print("Hello ");
pw.println("World");
pw.close();
```

---

### 📌 Scanner: Características y Métodos

- **Lectura de Ficheros**: Se puede utilizar para leer datos de un fichero.
- **Métodos Útiles**:
  - `hasNext()`: Devuelve `true` si hay más tokens.
  - `nextInt()`: Devuelve el siguiente token como un entero.
  - `nextLine()`: Devuelve toda la línea desde el punto de lectura actual.

```java
Scanner sc = new Scanner(new File("file.txt"));
while(sc.hasNext()) {
    System.out.println(sc.nextLine());
}
sc.close();
```

---

### 🛠 Ejemplo Práctico: Uso Combinado de PrintWriter y Scanner

1. **Escritura en el Fichero**: Utilizamos un bucle `for` para escribir números del 1 al 1000 en un fichero.
2. **Lectura del Fichero**: Utilizamos un bucle `while` para leer los números del fichero e imprimirlos en la consola.

```java
// Escritura en el fichero
PrintWriter pw = new PrintWriter("file.txt");
for(int i = 1; i <= 1000; i++) {
    pw.print(i + " ");
}
pw.close();

// Lectura del fichero
Scanner sc = new Scanner(new File("file.txt"));
while(sc.hasNext()) {
    if(sc.hasNextInt()) {
        System.out.println("Valor leído: " + sc.nextInt());
    } else {
        sc.next();
    }
}
sc.close();
```



___
%%
tags: #java  #pagacceso_a_datos  #Java #Programación #Curso #FicherosDeTexto #PrintWriter #Scanner #Métodos #EjemploPráctico #Escritura #Lectura 
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%