---
ID: 20
nombre: Estados de un Hilo en Java
tags:
  - pagprogramación_de_servicios_y_procesos
"Vínculos:":
---
___
![](https://www.youtube.com/watch?v=0Ez-QPXsKTo&list=PLyvsggKtwbLXEZjb8HrNTbWesTKIfpNak&index=24&ab_channel=LaGeekipediaDeErnesto)

### 🌱 Estado Nuevo (New)

- **Definición**: El hilo ha sido creado pero aún no se ha inicializado.
- **Método relevante**: Ninguno.
- **Excepción**: Se producirá un mensaje de error `IllegalThreadStateException` si se intenta ejecutar cualquier método de la clase `Thread` excepto el método `start`.
  
```java
Thread hilo1 = new Thread();
```

### 🏃‍♂️ Estado Ejecutable (Runnable)

- **Definición**: El hilo ha sido inicializado y está listo para ejecutarse.
- **Método relevante**: `start()`.
- **Ejemplo práctico**:

```java
hilo1.start();
```

### 🚧 Estado Bloqueado (Blocked)

- **Definición**: El hilo está en ejecución pero se encuentra detenido debido a alguna tarea o actividad.
- **Método relevante**: `sleep()`.
- **Excepción**: Debe estar encerrado en un bloque `try-catch` para manejar `InterruptedException`.
  
```java
try {
    Thread.sleep(1000);  // 1000 milisegundos = 1 segundo
} catch (InterruptedException e) {
    System.out.println("Error en el hilo");
}
```

### 💀 Estado Muerto (Dead)

- **Definición**: El hilo ha finalizado su ejecución.
- **Métodos relevantes**: 
  - Muerte natural: Finalización del método `run()`.
  - Muerte provocada: `stop()`.

```java
// Muerte natural
public void run() {
    // Código del hilo
}

// Muerte provocada
hilo1.stop();
```

### 🛠️ Implementación en Clases

- **Clase Principal**: Contiene el método `main` y crea instancias de la clase que maneja el hilo.
  
```java
public class ClasePrincipal {
    public static void main(String[] args) {
        // Código para manejar hilos
    }
}
```

- **Clase de Hilo**: Contiene la tarea a ejecutar en el hilo y hereda de la clase `Thread`.

```java
public class Hilo_Proceso extends Thread {
    public void run() {
        // Código del hilo
    }
}
```

### 📚 Documentación de Java

Para entender más sobre los métodos y clases disponibles en Java para el manejo de hilos, es altamente recomendable consultar la documentación oficial de Java.

### Código completo de ejemplo

```java 
public class Main {
    public static void main(String[] args) {
        // Estado Nuevo (New)
        ThreadExample threadExample = new ThreadExample();
        System.out.println("Estado Nuevo: " + threadExample.getState());

        // Estado Ejecutable (Runnable)
        threadExample.start();
        System.out.println("Estado Ejecutable: " + threadExample.getState());

        try {
            // Estado Bloqueado (Blocked)
            Thread.sleep(100); // Dar tiempo para que el hilo entre en estado bloqueado
            System.out.println("Estado Bloqueado: " + threadExample.getState());
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        try {
            // Esperar a que el hilo termine su ejecución
            threadExample.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // Estado Muerto (Dead)
        System.out.println("Estado Muerto: " + threadExample.getState());
    }
}

class ThreadExample extends Thread {
    @Override
    public void run() {
        // Simular una tarea que toma tiempo
        for (int i = 0; i < 5; i++) {
            try {
                Thread.sleep(500); // 500 milisegundos = 0.5 segundos
                System.out.println("Ejecutando tarea " + i);
            } catch (InterruptedException e) {
                System.out.println("Error en el hilo");
            }
        }
    }
}

```


___
%%
tags:  #pagprogramación_de_servicios_y_procesos  #Java #Hilo #EstadosDeHilo #Nuevo #Ejecutable #Bloqueado #Muerto #Implementación #ClasePrincipal #ClaseDeHilo #Documentación #Métodos #Excepciones
Vínculos:  [[000-Menú Programación de servicios y procesos 📃|Menú Programación de servicios y procesos 📃]]
%%