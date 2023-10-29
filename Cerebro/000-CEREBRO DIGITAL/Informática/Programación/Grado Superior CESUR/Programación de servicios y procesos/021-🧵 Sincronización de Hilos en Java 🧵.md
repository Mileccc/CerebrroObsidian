---
ID: 21
nombre: Sincronización de Hilos en Java
tags:
  - pagprogramación_de_servicios_y_procesos
"Vínculos:":
---
___
![](https://www.youtube.com/watch?v=5x_Nxdz_ZOs&list=PLyvsggKtwbLXEZjb8HrNTbWesTKIfpNak&index=25&ab_channel=LaGeekipediaDeErnesto)

### 🌟 Introducción
La sincronización es esencial para controlar el tiempo y la forma en que múltiples hilos se ejecutan simultáneamente. Esto evita que un hilo interfiera con otro durante la ejecución de tareas y también permite establecer un orden de ejecución específico.

### 🛠️ Configuración del Proyecto
Para ilustrar este concepto, vamos a crear un proyecto llamado "Sincronización de Hilos". Dentro de este proyecto, se incluirá un paquete llamado `hilo`, que contendrá cinco clases:

1. `ClasePrincipal`: Contiene el método `main`.
2. `Hilo1`: Primer hilo de ejecución.
3. `Hilo2`: Segundo hilo de ejecución.
4. `Hilo3`: Tercer hilo de ejecución.
5. `Hilo4`: Cuarto hilo de ejecución.

```java
// Ejemplo de la ClasePrincipal
public class ClasePrincipal {
    public static void main(String[] args) {
        // Código para manejar hilos
    }
}
```

### 🚀 Creación de Hilos
Cada una de las clases `Hilo1`, `Hilo2`, `Hilo3`, y `Hilo4` heredará de la clase `Thread` y sobrescribirá el método `run`.

```java
// Ejemplo de Hilo1
public class Hilo1 extends Thread {
    @Override
    public void run() {
        // Código del hilo
    }
}
```

### 🔄 Estructura de Control
Cada hilo imprimirá una letra específica (`g`, `e`, `e`, `k`) 11 veces. Utilizaremos un bucle `for` para lograr esto.

```java
// Ejemplo de bucle en Hilo1
for (int i = 0; i <= 10; i++) {
    System.out.print("g");
}
```

### ⏳ Sincronización de Hilos
Para sincronizar los hilos, utilizaremos el método `sleep` que pausa la ejecución del hilo durante un tiempo específico. Este método debe estar dentro de un bloque `try-catch` para manejar la excepción `InterruptedException`.

```java
// Ejemplo de sincronización en Hilo1
try {
    Thread.sleep(1000);
} catch (InterruptedException e) {
    System.out.println("Error en el hilo 1");
}
```

### 🎯 Ejecución y Resultados
Una vez que los hilos están sincronizados, se ejecutan en el orden especificado, imprimiendo la palabra "geek" de forma horizontal. Para separar cada impresión, el último hilo (`Hilo4`) añadirá un salto de línea.

```java
// Añadir salto de línea en Hilo4
System.out.println();
```


### Código completo de ejemplo

```java
// ClasePrincipal con el método main
public class ClasePrincipal {
    public static void main(String[] args) {
        // Crear instancias de los hilos
        Hilo1 hilo1 = new Hilo1();
        Hilo2 hilo2 = new Hilo2();
        Hilo3 hilo3 = new Hilo3();
        Hilo4 hilo4 = new Hilo4();

        // Iniciar los hilos
        hilo1.start();
        hilo2.start();
        hilo3.start();
        hilo4.start();
    }
}

// Hilo1 hereda de Thread y sobrescribe el método run
class Hilo1 extends Thread {
    @Override
    public void run() {
        for (int i = 0; i <= 10; i++) {
            System.out.print("g");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                System.out.println("Error en el hilo 1");
            }
        }
    }
}

// Hilo2 hereda de Thread y sobrescribe el método run
class Hilo2 extends Thread {
    @Override
    public void run() {
        for (int i = 0; i <= 10; i++) {
            System.out.print("e");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                System.out.println("Error en el hilo 2");
            }
        }
    }
}

// Hilo3 hereda de Thread y sobrescribe el método run
class Hilo3 extends Thread {
    @Override
    public void run() {
        for (int i = 0; i <= 10; i++) {
            System.out.print("e");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                System.out.println("Error en el hilo 3");
            }
        }
    }
}

// Hilo4 hereda de Thread y sobrescribe el método run
class Hilo4 extends Thread {
    @Override
    public void run() {
        for (int i = 0; i <= 10; i++) {
            System.out.print("k");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                System.out.println("Error en el hilo 4");
            }
            System.out.println();  // Añadir salto de línea
        }
    }
}

```

___
%%
tags:  #pagprogramación_de_servicios_y_procesos  #Java #SincronizaciónDeHilos #ConfiguraciónDelProyecto #CreaciónDeHilos #EstructuraDeControl #MétodoRun #MétodoSleep #InterruptedException #EjecuciónYResultados #RecursosAdicionales #ClasePrincipal #Hilo1 #Hilo2 #Hilo3 #Hilo4 #BucleFor #TryCatch #CursoRaptor #CódigoFuente
Vínculos:  [[000-Menú Programación de servicios y procesos 📃|Menú Programación de servicios y procesos 📃]]
%%