---
"ID:": 16
nombre: git tag, git switch, git checkout
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___

En este tutorial, nos centraremos en los comandos `git tag`, `git switch` y `git checkout`, que son esenciales para etiquetar commits importantes y cambiar entre ramas en un repositorio de Git.

### 🎯 Objetivos

1. Aprender a usar `git tag` para marcar commits importantes.
2. Entender `git switch` y `git checkout` para cambiar entre ramas y commits.

### 📌 Comandos Esenciales de Git

| Comando | Descripción |
|---------|-------------|
| `git tag [tagname]` | Crea una etiqueta con el nombre especificado en el commit actual. |
| `git checkout [branch/commit]` | Cambia a una rama o commit específico, incluso si está en un repositorio remoto. |
| `git switch [branch]` | Cambia entre ramas que ya existen localmente. |
| `git commit -m "[message]"` | Realiza un commit con el mensaje especificado. |

#### 🌟 Etiquetando Commits con `git tag`

Etiquetas o *tags* son útiles para marcar versiones específicas de tu código. Son especialmente útiles para marcar versiones estables o lanzamientos.

1. Crear una etiqueta en el commit actual:
   ```bash
   git tag v1.0
   ```
2. Ver etiquetas existentes:
   ``` bash
   git tag
   ```

#### 🌲 Cambiando Ramas con `git checkout` y `git switch`

Estos comandos te permiten cambiar entre diferentes ramas en tu repositorio local o remoto.

1. Usar `git checkout` para cambiar a una rama o commit específico:
   ```bash
   git checkout feature-branch
   ```
   
2. Utilizar `git switch` para cambiar entre ramas locales:
   ```bash
   git switch main
   ```

#### 🔄 Navegación entre Commits

1. Ir a un commit específico usando su hash:
   ```bash
   git checkout [commit_hash]
   ```

2. Regresar al último commit de la rama actual:
   ```bash
   git switch -
   ```
   o
   ```bash
   git checkout [branch_name]
   ```

#### 📁 Ejemplo de Flujo de Trabajo

1. Inicializar un repositorio y crear archivos:
   ```bash
   git init
   touch file1.py
   ```

2. Hacer commits:
   ```bash
   git add file1.py
   git commit -m "First commit"
   ```

3. Crear una nueva rama y cambiar a ella:
   ```bash
   git checkout -b new-branch
   ```

4. Crear una etiqueta en el commit actual:
   ```bash
   git tag v1.0
   ```

#### 🎭 `git switch` vs `git checkout`

- `git switch`: Utilizado para cambiar entre ramas **locales**.
- `git checkout`: Utilizado para cambiar a cualquier rama o commit y también para crear nuevas ramas.

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=hCml62m3vNWKgK55&amp;start=5793" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

___
%%
tags:  #paggitygithub  #Git #GitHub #Etiquetas #Ramas #Tutorial #Objetivos #ComandosEsenciales #gitTag #gitSwitch #gitCheckout #gitCommit #EtiquetandoCommits #CambiandoRamas #NavegaciónEntreCommits #FlujoDeTrabajo #gitInit #touch #gitAdd #newBranch #gitSwitchVsGitCheckout
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


