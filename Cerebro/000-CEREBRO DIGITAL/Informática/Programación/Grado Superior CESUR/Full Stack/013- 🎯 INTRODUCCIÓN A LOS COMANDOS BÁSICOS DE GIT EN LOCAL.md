---
ID: 13
nombre: "INTRODUCCIÓN A LOS COMANDOS BÁSICOS DE GIT\rEN LOCAL"
tags:
  - pagfull_stack
---
___
### 📜 Origen de Git: Un Vistazo al Pasado
Git es más que un sistema de control de versiones; su historia es fascinante y está profundamente entrelazada con la evolución del software libre. Surge en el contexto del desarrollo del kernel de Linux, una obra liderada por Linus Torvalds. Durante su evolución, se hizo evidente la necesidad de un sistema de control de versiones robusto. Inicialmente, se optó por BitKeeper, un Sistema de Control de Versiones Distribuido (DVCS) gratuito en ese momento. Sin embargo, debido a circunstancias imprevistas relacionadas con la empresa desarrolladora, BitKeeper se convirtió en software propietario. Fue entonces cuando Linus Torvalds decidió crear Git, con el objetivo de solucionar las deficiencias de BitKeeper y añadir nuevas funcionalidades.

#### 🎯 Objetivos que Guiaron la Creación de Git

- ***Mayor Velocidad***: Uno de los puntos focales fue aumentar la velocidad de operaciones, permitiendo una colaboración más eficiente.
  
- ***Diseño y Uso Sencillos***: Git fue creado con una interfaz intuitiva para facilitar su manejo.
  
- ***Soporte para Ramas en Paralelo***: Git permite la creación de ramas de trabajo independientes que pueden fusionarse más tarde.
  
- ***Sistema Completamente Distribuido***: A diferencia de los sistemas centralizados, Git permite que cada desarrollador tenga una copia completa del historial del proyecto.
  
- ***Escalabilidad para Grandes Proyectos***: Git es lo suficientemente robusto como para manejar proyectos de gran envergadura con múltiples colaboradores.

### 💻 Comandos Básicos de Git en Local

Para trabajar con Git en tu ordenador local, es fundamental familiarizarse con un conjunto de comandos básicos que facilitarán tus interacciones con este sistema de control de versiones. Aquí te presento una lista resumida de los más esenciales:

#### 🌱 Inicialización y Clonado

- ``git init``: Inicializa un nuevo repositorio Git en tu directorio actual.
  
- ``git clone [url]``: Clona un repositorio existente a tu máquina local.

#### 📝 Gestión de Cambios

- ``git add [archivo]``: Agrega cambios al área de preparación (staging area).
  
- ``git commit -m "[mensaje]"``: Confirma los cambios agregados al área de preparación con un mensaje descriptivo.

#### 🔀 Ramas y Fusiones

- ``git branch [nombre-rama]``: Crea una nueva rama en el repositorio.
  
- ``git merge [nombre-rama]``: Fusiona los cambios de una rama en otra.

#### 🔄 Sincronización

- ``git pull [nombre-repositorio-remoto] [nombre-rama]``: Actualiza tu repositorio local con cambios del repositorio remoto.
  
- ``git push [nombre-repositorio-remoto] [nombre-rama]``: Envía tus cambios locales al repositorio remoto.

___
%%
tags: #pagfull_stack #Git #OrigenDeGit #LinusTorvalds #BitKeeper #ObjetivosDeGit #MayorVelocidad #DiseñoYUsoSencillos #SoporteParaRamas #SistemaDistribuido #Escalabilidad #ComandosBásicos #Inicialización #Clonado #GestiónDeCambios #RamasYFusiones #Sincronización
Vínculos:  [[000-Menú Full Stack 📃|Menú Full Stack 📃]]
%%