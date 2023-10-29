---
"ID:": 8
nombre: git diff
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 🎯 Introducción a `git diff`
`git diff` es una herramienta valiosa que te permite ver las diferencias entre archivos en tu repositorio Git. Esto es esencial para entender los cambios que se han hecho antes de realizar un commit.

### 📝 Cómo Verificar el Estado del Repositorio

1. **Comandos Básicos de Estado**


 | Comando       | Explicación                                                |
  |---------------|------------------------------------------------------------|
  | `git status`  | Muestra el estado detallado del repositorio.               |
  | `git status -s`| Muestra el estado en un formato simplificado.              |


### 🎭 Estados de Archivos en Git



| Código       | Significado                                            |
|--------------|--------------------------------------------------------|
| `M`          | Archivo modificado pero no en el Stage.                |
| `A`          | Archivo agregado al Stage.                             |
| `?`          | Archivo no rastreado.                                  |


### 🛠️ Cómo Utilizar `git diff`

1. **Ver Diferencias Antes del Stage**
    - `git diff`

    *Explicación*: Este comando muestra las diferencias entre el índice y el directorio de trabajo.

2. **Ver Diferencias Después del Stage**
    - `git diff --staged`

    *Explicación*: Este comando muestra las diferencias entre los archivos en el stage y los últimos commits.

### 📋 Diferencias de Líneas

- Líneas eliminadas se muestran en rojo.
- Líneas agregadas se muestran en verde.


<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=u4Hq4yDxxsAjE34f&amp;start=2559" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
___
%%
tags:  #paggitygithub  #GuíaAvanzada #Git #GitHub #Introducción #gitdiff #CómoVerificarEstadoRepositorio #gitstatus #gitstatus-s #EstadosDeArchivos #MModificado #AAgregado #NoRastreado #CómoUtilizargitdiff #gitdiff--staged #DiferenciasDeLíneas #TrabajarConArchivosEspecíficos #gitadd #gitrm--cached #RealizarCommit #gitcommit-m #CódigosDeEstado #gitstatus-s
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


