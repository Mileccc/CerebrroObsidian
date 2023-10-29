---
ID: 21
nombre: Ejemplo Lectura-Escritura Fichero de Objetos
tags:
  - pagacceso_a_datos
---
___
Ejemplo de una Factura

```java
// Importar las clases necesarias
import java.io.*;
import java.math.BigDecimal;
import java.util.Calendar;

public class FlujoDeObjetos {
    // Definir constantes para el archivo y los datos
    static final String archDatos = "Factura.txt";
    static final BigDecimal[] precios = { new BigDecimal("18.00"), new BigDecimal("160.00"), new BigDecimal("25.00"),
            new BigDecimal("14.00"), new BigDecimal("2.50") };
    static final int[] cants = { 4, 2, 1, 5, 50 };
    static final String[] items = { "Marcadorazul", "Papel A4 500 hojas", "Borrador", "CDROM RW",
            "Sobres A4 transparentes" };

    public static void main(String[] args) throws IOException, ClassNotFoundException {
        // Inicializar el flujo de salida de objetos
        ObjectOutputStream out = null;
        try {
            out = new ObjectOutputStream(new BufferedOutputStream(new FileOutputStream(archDatos)));
            // Escribir la fecha actual en el archivo
            out.writeObject(Calendar.getInstance());
            // Iterar a través de los arreglos de precios, cantidades e items
            for (int i = 0; i < precios.length; i++) {
                out.writeObject(precios[i]);
                out.writeInt(cants[i]);
                out.writeUTF(items[i]);
            }
        } finally {
            // Cerrar el flujo de salida
            out.close();
        }

        // Inicializar el flujo de entrada de objetos
        ObjectInputStream in = null;
        try {
            in = new ObjectInputStream(new BufferedInputStream(new FileInputStream(archDatos)));
            Calendar fecha = null;
            BigDecimal precio;
            int cant;
            String item;
            BigDecimal total = new BigDecimal("0");
            // Leer la fecha del archivo
            fecha = (Calendar) in.readObject();
            System.out.format("El %Ta, %<tB, %<te, %<Ty, se compro: %n", fecha);

            // Leer y procesar los datos hasta llegar al final del archivo
            try {
                while (true) {
                    precio = (BigDecimal) in.readObject();
                    cant = in.readInt();
                    item = in.readUTF();
                    System.out.format("%4d %25s a $%6.2f c/u $%8.2f%n", cant, item, precio,
                            precio.multiply(new BigDecimal(cant)));
                    total = total.add(precio.multiply(new BigDecimal(cant)));
                }
            } catch (EOFException e) {
                // Al llegar al final del archivo, mostrar el total
                System.out.format("\t\t\t\t\t TOTAL $%8.2f%n", total);
            } finally {
                // Cerrar el flujo de entrada
                in.close();
            }
        }
    }
}

```


### Ejemplo 2
En la empresa en la que estamos desarrollando diversas aplicaciones que mejoren la digitalización de las diferentes tareas se pretende mejorar el almacenamiento del número de productos que entran por el almacén a través de un dispositivo añadiéndole el nombre del artículo. 

El dispositivo tiene capacidad de conexión Wifi y, posteriormente, enviará serializada la lista al servidor central. 

El proceso sería el siguiente: 

- Se usa una clase Lista definida como serializable, esto permitirá guardar y recuperar la lista completa de un archivo, mediante una simple llamada a una función.

```java
// Importa el paquete necesario para la serialización
import java.io.Serializable;

// Definición de la clase ListaProductos que implementa la interfaz Serializable
public class ListaProductos implements Serializable {
    // Atributos de la clase
    private int[] cantidadProductos;
    private String[] listaProductos;
    private int numMax, contadorProducto;

    // Constructor de la clase
    public ListaProductos(int productosAlmacenar) {
        // Inicialización de los atributos
        this.cantidadProductos = new int[productosAlmacenar];
        this.listaProductos = new String[productosAlmacenar];
        numMax = productosAlmacenar;
        contadorProducto = 1;
    }

    // Método para añadir un nuevo producto
    public int nuevoProducto(String producto, int cantidad) {
        // Verifica si hay espacio para añadir el producto
        if (contadorProducto < numMax) {
            // Almacena el producto y la cantidad en los respectivos arrays
            this.cantidadProductos[contadorProducto - 1] = cantidad;
            this.listaProductos[contadorProducto - 1] = producto;
            // Incrementa el contador de productos
            contadorProducto++;
            return cantidad;
        } else {
            // Retorna -1 si no hay espacio para más productos
            return -1;
        }
    }
}

```

- Cualquier programa podría hacer uso de esta clase:

```java
// Importar las clases necesarias
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.util.Scanner;

// Definición de la clase Main
public class Main {
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        // Creación de una instancia de ListaProductos con espacio para 5 productos
        ListaProductos lista = new ListaProductos(5);
        Scanner scanner = new Scanner(System.in);
        int numero;
        String producto;

        // Obtener información del usuario
        System.out.print("Introduce las unidades recibidas(-1 para finalizar): ");
        numero = scanner.nextInt();
        scanner.nextLine(); // Consume la línea extra

        // Ciclo para recibir productos y cantidades
        while (numero >= 0) {
            System.out.print("Introduce el nombre del producto: ");
            producto = scanner.nextLine();
            lista.nuevoProducto(producto, numero);
            System.out.print("Introduce las unidades recibidas(-1 para finalizar): ");
            numero = scanner.nextInt();
            scanner.nextLine(); // Consume la línea extra
        }

        // Serialización de la lista de productos
        ObjectOutputStream salida = new ObjectOutputStream(new FileOutputStream("media.obj"));
        salida.writeObject("guardar este string y un objeto\n");
        salida.writeObject(lista);
        salida.close();

        // Deserialización de la lista de productos
        ObjectInputStream entrada = new ObjectInputStream(new FileInputStream("media.obj"));
        String str = (String) entrada.readObject();
        ListaProductos obj1 = (ListaProductos) entrada.readObject();
        entrada.close();
    }
}

```






___
%%
tags: #pagacceso_a_datos  #Factura #Java #Serializable #FlujoDeObjetos #ObjectOutputStream #ObjectInputStream #Digitalización #Almacén #ListaProductos #Serialización #Deserialización #BufferedOutputStream #BufferedInputStream #FileOutputStream #FileInputStream #BigDecimal #Calendar #EOFException #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%