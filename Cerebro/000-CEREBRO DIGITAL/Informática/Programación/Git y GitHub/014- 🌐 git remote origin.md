---
"ID:": 14
nombre: git remote origin
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 🛠️ Preparativos: Cuenta y Repositorio en GitHub

1. Crear o tener una cuenta en GitHub.
2. Ir a "_Repositories_" en GitHub y crear un nuevo repositorio. 

![[Pasted image 20231027201229.png]]

### 💻 Comandos Básicos en Terminal de Visual Studio Code

#### Tabla de Comandos

| Comando | Descripción |
| ------- | ----------- |
| `git init` | Inicializa un nuevo repositorio Git en tu proyecto local. |
| `git commit` | Realiza un commit con los cambios en tu repositorio local. |
| `git remote add origin [URL]` | Conecta tu repositorio local con un repositorio remoto en GitHub. El "origin" es un nombre corto para la URL del repositorio remoto. |
| `git push origin [branch]` | Sube los cambios de la rama especificada a GitHub. |
| `git pull` | Descarga los cambios desde el repositorio remoto a tu repositorio local. |
| `git clone [URL]` | Clona un repositorio remoto a tu sistema local. |

### 👩‍💻 Conexión del Repositorio Local con GitHub



1. Copiar la URL del nuevo repositorio en GitHub.
2. En Visual Studio Code, abrir la terminal.
3. Ejecutar `git remote add origin [URL]` para conectar el repositorio local con GitHub.

![[Pasted image 20231027201946.png]]

### 🔄 Push y Pull: Sincronización de Cambios

1. Para subir cambios: `git push origin [branch]`.
    - Aquí `[branch]` es el nombre de la rama que quieres subir a GitHub (por ejemplo, `master` o `main`).
2. Para descargar cambios: `git pull`.

### 🌿 Manejo de Ramas

1. Crear o cambiar a otra rama en Visual Studio Code.
2. Usar `git push` para subir una nueva rama al repositorio remoto.
3. Verificar que la nueva rama aparece en GitHub.

### 🕵️‍♀️ Revisión de Commits en GitHub

- En GitHub, puedes seleccionar una rama específica y luego revisar los commits realizados.
- Cada commit muestra los cambios en el código, permitiendo identificar fácilmente errores o modificaciones.

### 📁 Otras Operaciones

- En GitHub, se pueden realizar acciones como crear nuevos archivos, subir archivos de manera manual y más.
- También puedes ver las diferencias entre dos ramas, lo que es útil para entender las variaciones entre distintas versiones del proyecto.

### 🔄 Actualización de Proyecto en Visual Studio Code

- Utilizar `git pull` para actualizar tu proyecto local con los cambios hechos en el repositorio remoto.

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=_SHCMTvYwmBDFiOj&amp;start=4385" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
 
___
%%
tags:  #paggitygithub  #Git #GitHub #VisualStudioCode #Preparativos #ComandosBásicos #TablaDeComandos #gitInit #gitCommit #gitRemoteAddOrigin #gitPush #gitPull #gitClone #ConexiónDelRepositorioLocal #PushYPull #SincronizaciónDeCambios #ManejoDeRamas #RevisiónDeCommits #OtrasOperaciones #ActualizaciónDeProyecto
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


