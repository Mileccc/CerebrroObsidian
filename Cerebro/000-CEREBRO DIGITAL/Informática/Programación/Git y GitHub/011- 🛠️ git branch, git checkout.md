---
"ID:": 11
nombre: git branch, git checkout
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___ 
### 🌳 Concepto de Ramas (Branches)

Las ramas en Git permiten trabajar en flujos paralelos sin afectar la rama principal del código. Se usan para implementar nuevas funcionalidades o corregir errores sin afectar la rama principal (usualmente `master`).


### 📝 Comandos de Git para Trabajar con Ramas

| Comando | Descripción |
|---------|-------------|
| `git branch` | Lista las ramas existentes y señala la rama actual con un asterisco. |
| `git branch [nombre]` | Crea una nueva rama con el nombre especificado. |
| `git checkout [nombre]` | Cambia a la rama especificada. |
| `git checkout -b [nombre]` | Crea una nueva rama y cambia a ella en un solo paso. |
| `git merge [nombre]` | Fusiona la rama especificada con la rama actual. |

### 🚀 Pasos para Trabajar con Ramas

1. **Verificar Rama Actual**: Usa `git branch` para saber en qué rama te encuentras.
    - `* master` indica que estás en la rama `master`.

2. **Crear y Cambiar de Rama**: Utiliza `git checkout -b [nombre]` para crear una nueva rama y cambiarte a ella.
    - Aparecerá un mensaje como: "Switched to a new branch '[nombre]'".

3. **Verificar Cambio de Rama**: `git branch` ahora debería mostrar dos ramas, con el asterisco en la nueva.

4. **Hacer Cambios en el Código**: Realiza las modificaciones necesarias en los archivos del proyecto.

5. **Hacer Commit**: Una vez que hayas hecho los cambios, realiza un commit para guardarlos.
    - `git commit -m "Tu mensaje"`

6. **Cambiar a la Rama Principal**: Utiliza `git checkout master` para volver a la rama principal.

7. **Fusionar Ramas**: Usa `git merge [nombre]` para fusionar los cambios de la rama nueva en la rama principal.

### 🎯 Casos de Uso Comunes

- `master`: Es la rama principal y suele contener el código en su estado más estable.
- `development`: Rama secundaria para tareas de desarrollo antes de fusionarlas con `master`.

### 🖼️ Visualizando el Flujo de Trabajo con Ramas

Es posible utilizar herramientas gráficas o comandos como `git log --oneline --graph` para visualizar cómo se bifurcan y unen las ramas. El último commit, o "HEAD", es donde te encuentras actualmente y esto puede ser visto tanto en la línea de comandos como en herramientas gráficas.

![[Pasted image 20231027190048.png]]

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=1RcCqImpc7Cj_1e3&amp;start=3337" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
___
%%
tags:  #paggitygithub  #Git #Ramas #Branches #Terminal #Comandos #gitbranch #gitcheckout #gitmerge #VerificarRama #CrearRama #CambiarRama #Commit #FusionarRamas #master #development #gitlog #FlujoDeTrabajo #HEAD
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


