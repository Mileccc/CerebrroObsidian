---
ID: 15
nombre: Estados y planificación de los procesos
tags:
  - pagprogramación_de_servicios_y_procesos
"Vínculos:":
---
___
![[d qH72fVTT.svg]]
### 🌱 Fases o Estados de un Proceso

Un proceso en computación es una instancia de un programa en ejecución. Desde su creación hasta su terminación, un proceso pasa por diferentes estados que definen su ciclo de vida. Estos estados son:

![[Pasted image 20231013200327.png]]

- 🆕 ***Nuevo***: El proceso ha sido creado recientemente y está listo para entrar en la fase de preparación.
- 🕒 ***Preparado***: El proceso tiene asignados todos los recursos que necesita y está en espera de ser ejecutado por la CPU.
- 🏃 ***Ejecución***: El proceso está utilizando el tiempo de CPU para ejecutar sus instrucciones.
- 🚫 ***Bloqueado***: El proceso se encuentra detenido debido a ciertas circunstancias, como la necesidad de un recurso que está siendo utilizado por otro proceso.
- ✅ ***Terminado***: El proceso ha completado todas sus instrucciones y ha finalizado su ejecución.

### 🔄 Transiciones entre Estados

Los cambios de estado en un proceso se conocen como transiciones. Estas son:

![[Pasted image 20231013200412.png]]

- 🅰️ ***Transición A***: De *Nuevo* a *Preparado* cuando se asignan los recursos necesarios.
- 🅱️ ***Transición B***: De *Preparado* a *Ejecución* cuando se asigna tiempo de CPU.
- 🅲️ ***Transición C***: De *Ejecución* a *Preparado* cuando se agota el tiempo asignado de CPU.
- 🅳️ ***Transición D***: De *Bloqueado* a *Preparado* cuando se asigna un recurso no disponible previamente.
- 🅴️ ***Transición E***: De *Ejecución* a *Bloqueado* cuando se necesita un recurso no disponible.
- 🅵️ ***Transición F***: De *Ejecución* a *Terminado* cuando se han completado todas las instrucciones.

### 🌟 Prioridades en la Planificación de Procesos

La asignación de prioridades es crucial para determinar qué proceso se ejecutará a continuación. Estas prioridades pueden ser asignadas tanto por el administrador del sistema como por el sistema operativo.

#### 📊 Algoritmos de Planificación

Los algoritmos de planificación son métodos que la CPU utiliza para decidir qué proceso se ejecutará a continuación, basándose en su tipo y prioridad. Los algoritmos más comunes son:

- 🔄 ***Round Robin***: Asigna tiempo de CPU a los procesos de manera rotativa. Cada proceso recibe un intervalo de tiempo de ejecución, conocido como *quantum*.
- 🥇 ***FIFO (First In First Out)***: El primer proceso en la cola es el primero en recibir tiempo de CPU y lo retiene hasta que completa todas sus instrucciones.
- ⏳ ***SJF (Shortest Job First)***: Selecciona el proceso con el menor tiempo de ejecución estimado para ser el próximo en ejecutarse.
- 🌐 ***Prioridad***: Elige el proceso con la mayor prioridad para ser el próximo en ejecutarse. Para evitar que algunos procesos nunca se ejecuten, se añade un mecanismo que incrementa la prioridad de los procesos que han estado esperando durante un tiempo prolongado.

Con esta estructura, se espera que el ciclo de vida de los procesos en computación, sus estados, transiciones y cómo se planifican para la ejecución sean más comprensibles.

![Planificación de procesos de la CPU - YouTube](https://www.youtube.com/watch?v=jxGnKR3JoOw)

___
%%
tags:  #pagprogramación_de_servicios_y_procesos  #CicloDeVida #PlanificaciónDeProcesos #Computación #Fases #EstadosDeProceso #Nuevo #Preparado #Ejecución #Bloqueado #Terminado #Transiciones #TransiciónA #TransiciónB #TransiciónC #TransiciónD #TransiciónE #TransiciónF #Prioridades #AlgoritmosDePlanificación #RoundRobin #FIFO #SJF #Prioridad
Vínculos:  [[000-Menú Programación de servicios y procesos 📃|Menú Programación de servicios y procesos 📃]]
%%