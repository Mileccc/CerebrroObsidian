---
"ID:": 12
nombre: GIT en Visual Studio Code
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
En este texto, exploramos cómo utilizar Git y GitHub en Visual Studio Code (VSCode). Se abordan desde la inicialización de un repositorio hasta la gestión de ramas y merges.

### 📁 Inicialización de Repositorio

1. Crear una carpeta en Windows llamada `proyecto git 2`.
2. Abrir VSCode y arrastrar la carpeta.
3. Abrir la terminal (`Ctrl+N`) en VSCode.
4. Ejecutar `git init` para inicializar el repositorio vacío.

| Comando    | Descripción                            |
|------------|----------------------------------------|
| `git init` | Inicializa un repositorio Git vacío.   |

### 📝 Creación y Modificación de Archivos

1. Crear `file1.txt` y escribir "curso de git y github".
2. Guardar el archivo. Notarás que el color cambia a verde en la barra lateral, lo que indica un nuevo cambio.

### 🎛️ Uso de Source Control

![[Pasted image 20231027192323.png]]

1. Ir a la sección de Source Control (ícono de control de versiones).
2. Verás que `file1.txt` aparece como un archivo modificado.

| Comando        | Descripción                                       |
|----------------|---------------------------------------------------|
| `git status`   | Muestra el estado actual del repositorio.          |

#### 🔄 Stage y Unstage

1. Para agregar cambios al Stage, utilizar el signo más (+) al lado del archivo en Source Control.
2. Para quitar del Stage, utilizar el signo menos (-).

![[Pasted image 20231027192424.png]]

![[Pasted image 20231027192505.png]]

| Signo | Acción                                |
|-------|---------------------------------------|
| `+`   | Agregar cambios al stage.             |
| `-`   | Quitar cambios del stage.             |

#### ✏️ Commit

1. Ingresar un mensaje de commit en la barra superior de Source Control.
2. Presionar el ícono de `commit`.

![[Pasted image 20231027192545.png]]

| Comando       | Descripción                    |
|---------------|--------------------------------|
| `git commit`  | Crea un nuevo commit.          |

### 🌿 Creación de Ramas (Branching)

1. Ir al nombre de la rama actual en la barra inferior (por defecto "master").
2. Hacer clic y crear una nueva rama llamada `rama nueva`.

![[Pasted image 20231027192701.png]]

| Comando            | Descripción                         |
|--------------------|-------------------------------------|
| `git checkout -b`  | Crea y cambia a una nueva rama.     |

### 📜 Merge de Ramas

1. Cambiar a la rama `master`.
2. Ir a los tres puntos en Source Control y seleccionar `Merge Branch`.
3. Elegir la rama `rama nueva` para realizar el merge.

![[Pasted image 20231027192801.png]]

| Comando       | Descripción                            |
|---------------|----------------------------------------|
| `git merge`   | Combina los cambios entre dos ramas.   |


### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=n9DqBRf9J4Kxpza-&amp;start=3825" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

___
%%
tags:  #paggitygithub  #Git #GitHub #VisualStudioCode #InicializaciónDeRepositorio #gitInit #CreaciónYModificaciónDeArchivos #UsoDeSourceControl #gitStatus #StageYUnstage #Commit #gitCommit #CreaciónDeRamas #gitCheckout-b #MergeDeRamas #gitMerge
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


