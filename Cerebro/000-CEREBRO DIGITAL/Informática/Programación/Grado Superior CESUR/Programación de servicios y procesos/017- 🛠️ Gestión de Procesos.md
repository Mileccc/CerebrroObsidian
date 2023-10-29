---
ID: 17
nombre: Gestión de Procesos
tags:
  - pagprogramación_de_servicios_y_procesos
"Vínculos:":
---
___
[![](https://mermaid.ink/img/pako:eNqNVE1rFDEY_ishp11Ylp3d6X7MrW6L7mGx0OJB9hIzb9vUmWRMMtIPCh68SEtVVhBapApeRIpIL-J1f5D9CSaZzsx-tTqnSfK8X8_zJEeYihBwgGPGw5gkI46QFEJXKjeXF5___HqLHoLSbHLNUQhoQwoKSigEHG0ypSEmCj1OQBLNXgpVrdpwhG4uP7xGfREnggPXoExolONLeIa16LMLW2gNVELoLgmFLI_GJ2gjIpxtM2oPppvIa43P0YaIJlfaQBQ6QEOgJkDFQjl0Hk3tEHliVIaUW0XgXXHV6s3l6U_UZzRymCcsJNMdVSplMsPf-SvUl5AlmIZVS5TrhIQSEKBdtidm4j--t7SsR8xoc28Wg_36CQ0M1ZLQDGh4l3dWdPpssSRjyAiV8kWC8m-TcSoFJ2jxaFVNrrLDmV7OfpicnKZSAqeMGEluc7DDrMiydgprFaHGOPO4zJGPQEoSM4MgboC57It9OstlvKzqyXU8o3oxJ9xS15fzxrBafrcdPouc481AIkopM_ZeSu36Po1S5ZINU51aBh5E4kUKwq3FfMj4jRHP2G1J-_nMZcGZtk7fuXtGpGaFQQZ8W8j4dt756zAj9r22KARRsDP5zf9lkwEPIQEesiXC2a8vhFVhmarjL2hr8o1yd3__R88cYK-qsUvILDMkWgTOC7GsrampUGJemCFwRfYA13AMhkYWmsfxyAaOsN6FGEY4ML8hkc9HeMSPDY6kWmwecIoDLVOo4TQJiYY1RnaMTXGwTSJV7K6HTAtZbIJbDrMn2L3ENZwQ_lSIOM9mljg4wvs48Lt1r9v2O5122_Naza5Xwwc48JrteqflN7y273X9lU6jdVzDhy5Bo95rNXtes-d3Vno9r-F3jv8CktoBmg?type=png)](https://mermaid.live/edit#pako:eNqNVE1rFDEY_ishp11Ylp3d6X7MrW6L7mGx0OJB9hIzb9vUmWRMMtIPCh68SEtVVhBapApeRIpIL-J1f5D9CSaZzsx-tTqnSfK8X8_zJEeYihBwgGPGw5gkI46QFEJXKjeXF5___HqLHoLSbHLNUQhoQwoKSigEHG0ypSEmCj1OQBLNXgpVrdpwhG4uP7xGfREnggPXoExolONLeIa16LMLW2gNVELoLgmFLI_GJ2gjIpxtM2oPppvIa43P0YaIJlfaQBQ6QEOgJkDFQjl0Hk3tEHliVIaUW0XgXXHV6s3l6U_UZzRymCcsJNMdVSplMsPf-SvUl5AlmIZVS5TrhIQSEKBdtidm4j--t7SsR8xoc28Wg_36CQ0M1ZLQDGh4l3dWdPpssSRjyAiV8kWC8m-TcSoFJ2jxaFVNrrLDmV7OfpicnKZSAqeMGEluc7DDrMiydgprFaHGOPO4zJGPQEoSM4MgboC57It9OstlvKzqyXU8o3oxJ9xS15fzxrBafrcdPouc481AIkopM_ZeSu36Po1S5ZINU51aBh5E4kUKwq3FfMj4jRHP2G1J-_nMZcGZtk7fuXtGpGaFQQZ8W8j4dt756zAj9r22KARRsDP5zf9lkwEPIQEesiXC2a8vhFVhmarjL2hr8o1yd3__R88cYK-qsUvILDMkWgTOC7GsrampUGJemCFwRfYA13AMhkYWmsfxyAaOsN6FGEY4ML8hkc9HeMSPDY6kWmwecIoDLVOo4TQJiYY1RnaMTXGwTSJV7K6HTAtZbIJbDrMn2L3ENZwQ_lSIOM9mljg4wvs48Lt1r9v2O5122_Naza5Xwwc48JrteqflN7y273X9lU6jdVzDhy5Bo95rNXtes-d3Vno9r-F3jv8CktoBmg)
### 🔄 Componentes del Sistema Operativo

#### 🎛️ Despachador
- Encargado de mover los procesos entre diferentes estados.
- Actualiza las colas de procesos y estados.

#### 📋 Planificador de Procesos
- Decide qué proceso se debe ejecutar, detener o pausar.

### 📚 Políticas y Mecanismos de Planificación

- ***Política***: Estrategia para determinar el próximo proceso a ejecutar.
- ***Mecanismo de Planificación***: Implementación de una política específica.
___
### 🌱 Ciclo de Vida de Procesos

#### 🚀 Creación de Procesos
- Proceso padre e hijo.
- Estructura de árbol entre procesos.

![[Pasted image 20231013203112.png]]

##### Ejemplo Uso de ProcessBuilder
```java
package creador;
import java.io.IOException;

public class Creador {
	public void ejecutar (String ruta) {
		ProcessBuilder pb;
		try{
			pb = new ProcessBuilder (ruta);
			pb.start();
		}catch (IOException e) {
			System.out.println("Error");
		}
		
	}

	public static void main (String[] args) {
		String ruta = "C:\\Program Files (x86)\\Adobe\\Acrobat Reader DC\\Reader\\AcroRd32.exe";
		Creador cr = new Creador();
		cr.ejecutar(ruta);
		System.out.println("Finalizado")
	}
}
```

#### 🗑️ Eliminación de Procesos
- Terminación por el propio proceso o por el proceso padre.
- Uso del servicio del sistema `Exit`.
___
### 🤝 Interacción entre Procesos

- ***Memoria Compartida***: Procesos manipulan la memoria compartida.
- ***Paso de Mensajes***: Sistema operativo proporciona enlace lógico.

#### 🔄 Tipos de Comunicación
- ***Síncrona***: Procesos se sincronizan para intercambiar datos.
- ***Asíncrona***: Uso de buffer temporal.

___
### 🎯 Concurrencia y Sincronización

#### 🔄 Procesos Concurrentes
- Ventajas y desafíos de la concurrencia.

#### 🛠️ Herramientas de Sincronización
- ***Operación Atómica***: No puede ser interrumpida.
- ***Sección Crítica***: Área donde se comparten recursos.
___
### 🚫 Problemas y Soluciones

#### 🔄 Exclusión Mutua y Bloqueo Mutuo
- Condiciones que pueden llevar a un bloqueo de recursos.

#### 📉 Inanición
- Falta de recursos que lleva a una debilidad en el proceso.

#### 🛠️ Soluciones
- Procedimientos para entrar y salir de la sección crítica.
- Uso del concepto de envejecimiento para asignar recursos.

```java
public void entrada_seccion_critica(){
	/*Codigo*/ 
} 

public void salida_seccion_critica(){
	/*Codigo*/ 
}
```

***Requisitos***:
• No puede haber más de un proceso o hilo simultáneamente en la zona de sección crítica. 
• No puede existir inanición, pues un proceso no puede esperar un tiempo indefinido para entrar. 
• No puede producirse un interbloqueo, ningún proceso fuera de la sección crítica puede impedir que otro proceso entre.


### 🌐 Compartición de Información y Mecanismos de Comunicación

#### 🔄 Tipos de Procesos según Comunicación
- ***Procesos Independientes***: No necesitan cooperación.
- ***Procesos Cooperantes***: Necesitan interactuar y comunicarse.

#### 📡 Técnicas de Sincronización
- ***Sincronismo Condicional***: Basado en condiciones.
- ***Exclusión Mutua***: Acceso exclusivo a recursos.
- ***Comunicación por Mensajes***: Intercambio de mensajes para sincronización.

Tomando un momento para evaluar, creo que esta estructura aclara y organiza la información de manera efectiva, facilitando la comprensión del tema de la gestión de procesos en sistemas operativos.

___
#### EJEMPLO PRÁCTICO
A Juan le plantean buscar una solución a la siguiente situación a través de un pequeño programa en Java. En una tienda se ha implementado un contador de entrada de aforo y un contador de salida.

Ambos contadores son independientes, siendo la condición de aforo máximo de 20 personas. ¿Cómo resolver que salga y entre una persona al mismo tiempo a la tienda?

En primer lugar, deberíamos implementar las funciones que implementaría la entrada y salida de personas:

```java
int numPersonas = 0; // Variable común

int agregarPersona() {
	numPersonas = nupersonas + 1;
}

int restarPersona() {
	numPersonas = nupersonas - 1;
}
```

Como se observa, al tener una variable común, denominada numPersonas, si ambas funciones se ejecutan por procesos diferentes y de forma simultánea, puede dar un error. Podemos usar dos funciones que garantizasen el uso atómico de la variable numPersonas:

```java
int numPersonas = 0; // Variable común
int np = 0; // Variable para garantizar exclusión mutua

int agregarPersona() {
	PedMutex(np);
	numPersonas = nupersonas + 1;
	LibMutex(np); 
}

int restarPersona() {
	PedMutex(np);
	numPersonas = nupersonas - 1;
	LibMutex(np); 
} 
```


___
%%
tags:  #pagprogramación_de_servicios_y_procesos  #GestiónDeProcesos #SistemasOperativos #ComponentesDelSistemaOperativo #Despachador #PlanificadorDeProcesos #PolíticasDePlanificación #MecanismosDePlanificación #CicloDeVidaDeProcesos #CreaciónDeProcesos #EliminaciónDeProcesos #InteracciónEntreProcesos #MemoriaCompartida #PasoDeMensajes #TiposDeComunicación #Síncrona #Asíncrona #Concurrencia #Sincronización #ProcesosConcurrentes #HerramientasDeSincronización #OperaciónAtómica #SecciónCrítica #ProblemasYSoluciones #ExclusiónMutua #BloqueoMutuo #Inanición #Soluciones #ComparticiónDeInformación #MecanismosDeComunicación #ProcesosIndependientes #ProcesosCooperantes #TécnicasDeSincronización #SincronismoCondicional #ComunicaciónPorMensajes
Vínculos:  [[000-Menú Programación de servicios y procesos 📃|Menú Programación de servicios y procesos 📃]]
%%