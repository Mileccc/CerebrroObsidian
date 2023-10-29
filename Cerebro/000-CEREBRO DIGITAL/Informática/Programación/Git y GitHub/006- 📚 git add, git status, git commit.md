---
"ID:": 6
nombre: git add, git status, git commit
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 🌱 Inicialización y Configuración del Entorno
1. **Abrir la terminal:** Usar `Shift + clic derecho` para abrir la terminal de Git.
2. **Comandos iniciales:**
    - `ls`: Para listar los archivos y carpetas en el directorio actual.
    - `pwd`: Para conocer en qué directorio estamos ubicados.
    - `clear`: Para limpiar la terminal.

3. **Crear un nuevo directorio:** 
    - `mkdir proyecto_git`: Crea un nuevo directorio llamado `proyecto_git`.

4. **Cambiar al directorio creado:** 
    - `cd proyecto_git`: Cambia al directorio que acabamos de crear.
  
5. **Inicializar el repositorio Git:** 
    - `git init`: Este comando inicializa un nuevo repositorio Git en el directorio.

### 📝 Creación y Modificación de Archivos
1. **Abrir el editor de código:** 
    - `code .`: Abre el editor de código en el directorio actual.
  
2. **Crear un archivo de texto:** 
    - En el editor, crear un archivo llamado `file1.txt` y escribir "Hola mundo".

3. **Guardar cambios:**
    - Guardar el archivo en el editor de código.

### 🕵️‍♂️ Comandos para Consultar el Estado del Repositorio
| Comando        | Explicación                                                 |
|----------------|-------------------------------------------------------------|
| `git status`   | Muestra el estado de los archivos en el repositorio actual.  |

### 🚀 Comandos para Cambios y Stage
1. **Agregar archivos al Stage:** 
    - `git add file1.txt`: Agrega el archivo `file1.txt` al Stage.
  
2. **Verificar estado nuevamente:**
    - `git status`: Ahora mostrará que `file1.txt` está en el Stage.

3. **Agregar más archivos y hacer cambios:**
    - Crear `file2.txt`, agregar contenido, y guardar.
    - `git add file2.txt`: Agrega el nuevo archivo al Stage.

4. **Modificar un archivo ya agregado:**
    - Editar `file2.txt` y guardar los cambios.

| Comando                      | Explicación                                                        |
| ---------------------------- | ------------------------------------------------------------------ |
| `git add <filename>`         | Agrega los cambios en `<filename>` al Stage.                       |
| `git rm --cached <filename>` | Elimina `<filename>` del Stage, pero no del directorio de trabajo. |
| `git add -A`  | Agrega todos los cambios al Stage.                                    |

5. **Actualizar cambios en el Stage:**
    - `git add file2.txt`: Actualiza los cambios de `file2.txt` en el Stage.

### 📸 Comandos para Commit
| Comando                              | Explicación                                              |
|--------------------------------------|----------------------------------------------------------|
| `git commit -m "mensaje del commit"` | Crea un commit con los archivos que están en el Stage.   |

1. **Crear el primer Commit:**
    - `git commit -m "Se actualizó la información del archivo 2"`

2. **Hacer un segundo Commit:**
    - Editar `file1.txt` y agregarlo al Stage.
    - `git commit -m "Modificamos el file1 con una nueva descripción"`

Al seguir estos pasos y utilizar estos comandos, podrás manejar un flujo de trabajo básico en Git y GitHub. Cada comando tiene su propio propósito y es crucial para mantener tu código organizado y tu historial de cambios claro.


<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=pjIcozVeRT8gVFbg&amp;start=1808" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
___
%%
tags:  #paggitygithub  #Git #GitHub #Inicialización #Configuración #Entorno #Terminal #Comandos #ls #pwd #clear #mkdir #cd #git_init #Creación #Modificación #Archivos #EditorDeCódigo #code_ #Estado #Repositorio #git_status #Cambios #Stage #git_add #git_rm_cached #Commit #git_commit  

Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


