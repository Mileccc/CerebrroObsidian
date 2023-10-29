---
"ID:": 21
nombre: git clone
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 🎯 ¿Qué es `git clone`?

El comando `git clone` es una de las instrucciones más fundamentales cuando trabajamos con repositorios Git en un ambiente remoto, como GitHub. Este comando permite no solo descargar un repositorio remoto, sino también mantener un enlace con dicho repositorio. Esto es útil para recuperar un proyecto en otra máquina o para empezar a colaborar en un proyecto existente.

### 🛠️ Funcionamiento de `git clone`

#### 🌈 Protocolos de Clonado

- **HTTPS**: Es el protocolo más comúnmente utilizado y requiere la URL del repositorio remoto.
- **SSH**: Este método es un poco más complejo de configurar pero ofrece una capa extra de seguridad. Requiere que el SSH esté configurado en tu ambiente de trabajo.
  
#### 🌠 Pasos para Clonar con HTTPS

1. ***Copiar la URL del Repositorio Remoto***
    - En GitHub, selecciona el repositorio que quieres clonar y copia la URL HTTPS.

    ```bash
    git clone https://example.com/your-repo.git
    ```

#### 🌠 Pasos para Clonar con SSH (Opcional)

1. ***Copiar la URL SSH del Repositorio Remoto***
    - Similar al paso anterior pero copiando la URL SSH.
  
    ```bash
    git clone git@github.com:your-username/your-repo.git
    ```
  
### 📝 Tabla de Comandos Importantes

| Comando | Descripción |
|---------|-------------|
| `git clone` | Clona un repositorio remoto y lo enlaza con tu ambiente local |
| `git clone <URL>` | Clona un repositorio utilizando su URL |
| `pwd` | Muestra la ubicación actual en el sistema de archivos |
| `git branch` | Muestra las ramas del repositorio local |
| `git checkout <branch_name>` | Cambia a una rama específica |
| `git push` | Sube cambios al repositorio remoto |

### 🌈 Ramas y `git clone`

- Cuando clonamos un repositorio, solo se descarga la rama principal (generalmente `master`) por defecto.
- Las otras ramas existentes en el repositorio remoto no se descargan automáticamente.
- Se pueden cambiar entre ramas y descargarlas después de clonar, manteniendo el enlace al repositorio remoto.

### 🚨 Permisos y `git push`

- Si tienes permisos sobre el repositorio remoto, puedes hacer un `git push` sin problemas.
- Si el repositorio no es tuyo, necesitarás que el dueño apruebe tus cambios para actualizar el repositorio remoto.

### 🌟 Resumen

Con `git clone`, no solo recuperas un repositorio remoto, sino que también mantienes un vínculo con él. Esto facilita la colaboración y el trabajo en diferentes máquinas. El comando es flexible y puede usarse con varios protocolos como HTTPS y SSH.

___
### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=BmgnI8kBI8C8_vYD&amp;start=7720" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

___
%%
tags:  #paggitygithub  #Git #GitHub #gitClone #HTTPS #SSH #Comandos #Protocolos #PasosParaClonar #TablaDeComandos #pwd #gitBranch #gitCheckout #gitPush #Ramas #Permisos #Resumen
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


