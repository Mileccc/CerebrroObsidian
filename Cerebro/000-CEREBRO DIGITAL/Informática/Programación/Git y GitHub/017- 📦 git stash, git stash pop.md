---
"ID:": 17
nombre: git stash, git stash pop
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 🎯 Propósito

Este tutorial se enfoca en los comandos `git stash` y `git stash pop`, que son especialmente útiles cuando estás trabajando en una rama pero necesitas cambiar a otra sin comprometer los cambios no terminados. 

### 🛠️ Comandos Clave 

| Comando | Descripción |
|---------|-------------|
| `git stash` | Guarda tus cambios en un área de almacenamiento temporal sin hacer commit. |
| `git stash pop` | Recupera los cambios guardados en el stash y los aplica a tu rama actual. |
| `git stash list` | Lista todos los stashes creados. |
| `git switch` | Cambia entre ramas que ya existen localmente. |
| `git add` | Agrega cambios para ser comprometidos en el próximo commit. |
| `git stash drop` | Elimina el stash más reciente. |
| `git stash apply` | Similar a `git stash pop`, pero no elimina el stash después de aplicarlo. |


### 🌠 Uso del `git stash`

*Stashing* te permite guardar cambios que no estás listo para *committear*. Esto es particularmente útil si necesitas cambiar de rama para trabajar en algo diferente pero no quieres perder tus cambios actuales.

1. **Guardar Cambios Temporalmente**
    ```bash
    git stash
    ```
    - Te permite guardar los cambios en un área temporal.
  
2. **Listar Cambios Guardados**
    ```bash
    git stash list
    ```
    - Muestra todos los stashes que has creado.

### 🔄 Cambiando de Rama con Seguridad

Una vez que has guardado tus cambios con `git stash`, puedes cambiar de rama de forma segura.

```bash
git switch main
```

- Cambia a la rama `main` sin llevar los cambios no terminados.

### 🌈 Recuperar Cambios con `git stash pop`

Para regresar a tu rama original y aplicar los cambios que habías guardado:

1. **Volver a la Rama Original**
    ```bash
    git switch [nombre_de_tu_rama]
    ```
  
2. **Aplicar Cambios Guardados**
    ```bash
    git stash pop
    ```
    - Aplica los cambios guardados en tu rama original.
  
### 🛠️ Opciones Adicionales

- **Descartar Cambios Temporalmente Guardados**
    ```bash
    git stash drop
    ```
    - Elimina el stash más reciente.

- **Aplicar Cambios Sin Eliminar del Stash**
    ```bash
    git stash apply
    ```
    - Similar a `git stash pop`, pero no elimina el stash después de aplicarlo.

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=ceTKWo9yIx4Vd04f&amp;start=6417" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

___
%%
tags:  #paggitygithub  #Git #GitHub #gitStash #gitStashPop #gitStashList #gitSwitch #gitAdd #Stashing #CambiarRama #RamaOriginal #gitStashDrop #gitStashApply
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


