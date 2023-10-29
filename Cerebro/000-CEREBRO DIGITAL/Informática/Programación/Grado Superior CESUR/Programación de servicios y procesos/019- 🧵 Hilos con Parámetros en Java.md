---
ID: 19
nombre: Hilos con Parámetros en Java
tags:
  - pagprogramación_de_servicios_y_procesos
"Vínculos:":
---
___
![](https://www.youtube.com/watch?v=0b1wHDssExQ&list=PLyvsggKtwbLXEZjb8HrNTbWesTKIfpNak&index=23&ab_channel=LaGeekipediaDeErnesto)

### 🛠 Configuración del Proyecto en NetBeans
1. Crear un nuevo proyecto llamado `HilosConParametros`.
2. Eliminar el método `main` predeterminado.
3. Crear un paquete llamado `clases`.
4. Dentro del paquete, crear dos clases: `Proceso` y `ClasePrincipal`.

### 📝 Creación de la Clase `Proceso`
1. Abrir la clase `Proceso`.
2. Implementar la herencia con `Thread` usando `extends Thread`.
3. Sobreescribir el método `run()`.

```java
public class Proceso extends Thread {
    @Override
    public void run() {
        // Código aquí
    }
}
```

### 🔄 Implementación de Bucles en `Proceso`
1. Dentro del método `run()`, agregar un bucle `for`.
2. Utilizar una variable `i` para controlar el bucle.

```java
@Override
public void run() {
    for(int i = 0; i <= 5; i++) {
        System.out.println(i);
    }
}
```

### 📦 Pasar Parámetros a Hilos
1. Declarar una variable global `num` en la clase `Proceso`.
2. Crear un método `valorDeLaCondicion(int valor)` para recibir el valor del parámetro.
3. Dentro del método, asignar `valor` a `num`.

```java
int num;

public void valorDeLaCondicion(int valor) {
    this.num = valor;
}
```

### 🚀 Ejecución de Hilos en `ClasePrincipal`
1. Crear instancias de la clase `Proceso`.
2. Utilizar el método `valorDeLaCondicion()` para pasar parámetros a cada hilo.
3. Iniciar los hilos con el método `start()`.

```java
Proceso hilo1 = new Proceso();
hilo1.valorDeLaCondicion(5);
hilo1.start();

Proceso hilo2 = new Proceso();
hilo2.valorDeLaCondicion(10);
hilo2.start();
```

### 🎯 Identificación de Hilos
Para identificar qué hilo está ejecutando qué tarea, podemos utilizar el método `getName()` de la clase `Thread`.

```java
@Override
public void run() {
    for(int i = 0; i <= num; i++) {
        System.out.println(this.getName() + " " + i);
    }
}
```

### 📌 Notas Adicionales
- Los hilos se ejecutan de manera simultánea, lo que puede llevar a resultados impredecibles en el orden de ejecución.
- Es posible personalizar el nombre de cada hilo para facilitar su identificación.

### Código completo
#### Clase con método main (ClasePrincipal)

```java
public class ClasePrincipal {
    public static void main(String[] args) {
        Proceso hilo1 = new Proceso("Hilo 1");
        Proceso hilo2 = new Proceso("Hilo 2");
        Proceso hilo3 = new Proceso("Hilo 3");

        hilo1.valorDeLaCondicion(5);
        hilo2.valorDeLaCondicion(10);
        hilo3.valorDeLaCondicion(5);

        hilo1.start();
        hilo2.start();
        hilo3.start();
    }
}

```

#### Clase Proceso
```java
public class Proceso extends Thread {
    int num;

    public Proceso(String nombre) {
        super(nombre);
    }

    public void valorDeLaCondicion(int valor) {
        this.num = valor;
    }

    @Override
    public void run() {
        for(int i = 0; i <= num; i++) {
            System.out.println(this.getName() + " " + i);
        }
    }
}

```


___
%%
tags:  #pagprogramación_de_servicios_y_procesos  #Java #Hilos #Parametros #NetBeans #Proyecto #ClaseProceso #Herencia #Thread #MetodoRun #Bucles #VariableGlobal #MetodoValorDeLaCondicion #ClasePrincipal #EjecucionDeHilos #IdentificacionDeHilos #GetName #ResultadosImpredecibles #PersonalizarNombreHilo #Tutorial #ProgramacionIntermedia
Vínculos:  [[000-Menú Programación de servicios y procesos 📃|Menú Programación de servicios y procesos 📃]]
%%