---
ID: 10
nombre: Thread Métodos más importantes
tags:
  - pagprogramación_de_servicios_y_procesos
"Vínculos:":
---
___
Los métodos más importantes de la clase `Thread` en Java son:

- `start()`: Inicia la ejecución del hilo. Este método invoca automáticamente el método `run()` del hilo.
  
- `run()`: Contiene el código que constituye la nueva tarea. Este método es llamado cuando se inicia un hilo con `start()`.

- `sleep(long millis)`: Hace que el hilo actual se detenga durante un número específico de milisegundos.

- `join()`: Espera a que el hilo sobre el que se invoca termine su ejecución.

- `yield()`: Hace que el hilo en ejecución vuelva al estado listo para permitir que otros hilos del mismo nivel de prioridad puedan ejecutarse.

- `interrupt()`: Interrumpe el hilo, lo cual afecta operaciones como `sleep()` y `join()`.

- `isInterrupted()`: Comprueba si el hilo ha sido interrumpido.

- `setPriority(int newPriority)`: Establece la prioridad del hilo.

- `getPriority()`: Devuelve la prioridad del hilo.

- `setName(String name)`: Cambia el nombre del hilo.

- `getName()`: Devuelve el nombre del hilo.

- `currentThread()`: Método estático que devuelve referencia al hilo actual en ejecución.

- `getId()`: Devuelve el ID del hilo.

- `stop()`: **Desaconsejado**. Detiene el hilo de forma inmediata, lo cual puede ser peligroso.

- `suspend()`: **Desaconsejado**. Pausa el hilo hasta que `resume()` sea llamado.

- `resume()`: **Desaconsejado**. Reanuda un hilo suspendido.

Estos métodos proveen las funcionalidades básicas necesarias para la programación multihilo en Java.

___
%%
tags:  #pagprogramación_de_servicios_y_procesos  #Java #Thread #Multithreading #Métodos #start #run #sleep #join #yield #interrupt #isInterrupted #setPriority #getPriority #setName #getName #currentThread #getId #stop #suspend #resume
Vínculos:  [[000-Menú Programación de servicios y procesos 📃|Menú Programación de servicios y procesos 📃]]
%%