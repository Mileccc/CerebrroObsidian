---
"ID:": 9
nombre: git log
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 🧠 Conceptos Clave
- **Commit**: Una "fotografía" de los archivos en un momento específico.
- **Hash**: Un identificador único para cada commit.
- **HEAD**: Indica dónde estamos ubicados actualmente en el historial de commits.
- **Master**: Es la rama principal de trabajo en Git.

### 📖 Visualizando el Historial de Commits con `git log`

La forma más básica de ver el historial de commits es utilizando el comando `git log`. Sin embargo, este comando puede ser verboso y proporcionar más información de la necesaria.

| Comando | Explicación |
|---------|-------------|
| `git log` | Muestra el historial detallado de commits. Es muy verboso y para salir necesitas usar `:q`. |

### 🕵️‍♀️ Comandos de Navegación en `git log`

Cuando usas `git log`, necesitas algunos comandos para navegar:

| Comando | Explicación |
|---------|-------------|
| Barra espaciadora | Para continuar viendo más commits. |
| `:q` | Para salir del log. Este comando también se utiliza para salir de Vim. |

### 🎯 Solución al Problema de Verbosidad: `git log --oneline`

| Comando | Explicación |
|---------|-------------|
| `git log --oneline` | Muestra cada commit en una sola línea, haciéndolo menos verboso pero igualmente informativo. |

### 🌐 Entendiendo el Output de `git log --oneline`

Cuando usas `git log --oneline`, ves algo como esto:

```
3d958e7 (HEAD -> master) Se modificó file1 y se agregó file3
```

Desglosémoslo:

- `3d958e7`: Es el Hash (o parte de él) que identifica al commit.
- `HEAD -> master`: Indica que estamos en el último commit de la rama principal (`master`).
- `Se modificó file1 y se agregó file3`: Es el mensaje que le asignamos al commit para describir los cambios.

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=MSUtnEcLgnJjxXQk&amp;start=2834" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

___
%%
tags:  #paggitygithub  #NavegandoCommitsGit #EntendiendoCommits #ConceptosClave #Commit #Hash #HEAD #Master #VisualizandoHistorialCommits #gitlog #ComandosNavegaciónGitLog #BarraEspaciadora  #SoluciónVerbosidad #gitlog--oneline #EntendiendoOutputGitLog--oneline
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


