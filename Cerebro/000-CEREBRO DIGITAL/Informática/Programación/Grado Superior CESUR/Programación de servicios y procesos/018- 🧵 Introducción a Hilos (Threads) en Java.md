---
ID: 18
nombre: Introducción a Hilos (Threads) en Java
tags:
  - pagprogramación_de_servicios_y_procesos
"Vínculos:":
---
___
![](https://www.youtube.com/watch?v=fiLrTdSKVcE&list=PLyvsggKtwbLXEZjb8HrNTbWesTKIfpNak&index=23&ab_channel=LaGeekipediaDeErnesto)
### 📚 Concepto de Hilos

Un hilo, también conocido como *thread*, es un flujo de control dentro de un programa que permite la ejecución simultánea de múltiples procesos. En otras palabras, con la ayuda de hilos, se pueden ejecutar dos o más procesos al mismo tiempo sin tener que esperar a que uno termine para iniciar el siguiente.

#### 🔄 Ejemplo sin Hilos

Si no utilizamos hilos, debemos esperar a que finalice el primer proceso para pasar al siguiente. Supongamos que tenemos dos bucles `for`. El primer `for` se ejecutará completamente antes de pasar al segundo `for`.

```java
for(int i = 0; i <= 5; i++) {
    System.out.println("Proceso 1");
}
for(int j = 0; j <= 5; j++) {
    System.out.println("Proceso 2");
}
```

### 🛠 Creación de Proyecto en NetBeans

1. Abrir NetBeans y cerrar el proyecto anterior.
2. Crear un nuevo proyecto llamado `Hilos`.
3. Crear un paquete llamado `clases`.
4. Dentro del paquete, crear una clase principal que contenga el método `main`.

### 📝 Implementación de Hilos en Java

En Java, hay dos maneras de implementar hilos:

#### 🌱 Herencia (`extends Thread`)

1. Crear una clase llamada `Proceso1`.
2. Heredar de la clase `Thread` usando `extends Thread`.
3. Sobreescribir el método `run()`.

```java
public class Proceso1 extends Thread {
    @Override
    public void run() {
        for(int i = 0; i <= 5; i++) {
            System.out.println("Proceso 1");
        }
    }
}
```

#### 🎣 Interfaz (`implements Runnable`)

1. Crear una clase llamada `Proceso2`.
2. Implementar la interfaz `Runnable` usando `implements Runnable`.
3. Sobrescribir el método `run()`.

```java
public class Proceso2 implements Runnable {
    @Override
    public void run() {
        for(int i = 0; i <= 5; i++) {
            System.out.println("Proceso 2");
        }
    }
}
```

### 🚀 Ejecución de Hilos

Para ejecutar los hilos, se deben seguir los siguientes pasos:

1. Crear instancias de las clases que implementan los hilos.
2. Utilizar el método `start()` para iniciar cada hilo.

```java
Proceso1 hilo1 = new Proceso1();
Thread hilo2 = new Thread(new Proceso2());

hilo1.start();
hilo2.start();
```

### 📌 Notas Adicionales

- No es necesario crear una clase por cada hilo. Se pueden crear múltiples instancias de una misma clase para ejecutar el mismo proceso varias veces de manera simultánea.
- La ejecución de los hilos depende de la velocidad del procesador, por lo que el orden en que se ejecutan puede variar.

### 🎬 Conclusión

Los hilos son una herramienta poderosa en Java para la ejecución simultánea de procesos. Pueden ser implementados mediante herencia o interfaces, y su ejecución se controla mediante el método `start()`.

___
%%
tags:  #pagprogramación_de_servicios_y_procesos  #Java #Hilos #Threads #Concepto #Ejemplo #NetBeans #Proyecto #Implementación #Herencia #Interfaz #Runnable #Ejecución #NotasAdicionales #Conclusión
Vínculos:  [[000-Menú Programación de servicios y procesos 📃|Menú Programación de servicios y procesos 📃]]
%%