---
ID: 12
nombre: Ejemplo Código Hilo (Thread)
tags:
  - pagprogramación_de_servicios_y_procesos
"Vínculos:":
---
___

### Creador de la Clase Hilo
```java
// Se declara una clase Hilo que extiende de la clase Thread.
public class Hilo extends Thread{
	// Se definen dos variables privadas: nombre (de tipo String) y retardo (de tipo int).
	private String nombre;
	private int retardo;

	// Constructor de la clase que inicializa las variables nombre y retardo.
	public Hilo(String s, int d) {
		nombre = s;
		retardo = d;
	}

	// Método run() que será ejecutado cuando el hilo se inicie.
	public void run() {
		try {
			// El hilo duerme (se detiene) durante el tiempo definido en retardo.
			sleep(retardo);
		}catch(InterruptedException e) {
			// Manejo de la excepción InterruptedException.
		}
		// Se imprime el nombre del hilo y el retardo.
		System.out.println(nombre + "-> retardo:" + retardo);
	}
}

```


### Clase CreadorHilos 
Contiene el método main y es donde se instancian los hilos y se inician

```java
// Se declara una clase CreadorHilos con un método main para iniciar la aplicación.
public class CreadorHilos {

	public static void main(String[] args) {
		// Se declaran dos variables de tipo Hilo, h1 y h2.
		Hilo h1, h2;

		// Se instancian los objetos h1 y h2 con nombres y retardos aleatorios.
		h1 = new Hilo("hilo 1", (int)(Math.random() * 2000));
		h2 = new Hilo("hilo 2", (int)(Math.random() * 2000));

		// Se inician los hilos h1 y h2.
		h1.start();
		h2.start();
	}
}

```

### Consola
```java
hilo 1-> retardo:96
hilo 2-> retardo:1225
```

___
%%
tags:  #pagprogramación_de_servicios_y_procesos  #Java #Hilo #Thread #CreadorHilos #retardo #InterruptedException #métodoRun #Constructor #Obsidian #ResultadoConsola #VariablesPrivadas
Vínculos:  [[000-Menú Programación de servicios y procesos 📃|Menú Programación de servicios y procesos 📃]]
%%