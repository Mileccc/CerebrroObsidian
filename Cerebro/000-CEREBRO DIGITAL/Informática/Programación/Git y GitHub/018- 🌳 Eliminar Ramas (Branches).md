---
"ID:": 18
nombre: Eliminar Ramas (Branches)
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 🛠️ Comandos Clave en Eliminación de Ramas

| Comando | Descripción |
|---------|-------------|
| `git branch -d [nombre_de_rama]` | Elimina una rama localmente. |
| `git push origin --delete [nombre_de_rama]` | Elimina una rama en el repositorio remoto. |
| `git checkout [nombre_de_rama]` | Cambia a una rama específica. |
| `git push -u origin [nombre_de_rama]` | Publica una rama local en el repositorio remoto. |
| `git pull` | Actualiza la información del repositorio local con respecto al remoto. |

---

### 🌠 Pasos para Eliminar Ramas Localmente

1. **Asegúrate de No Estar en la Rama que Quieres Eliminar**
    - Usa `git checkout [nombre_de_otra_rama]` para cambiar de rama.

2. **Eliminar la Rama Localmente**
    ```bash
    git branch -d [nombre_de_rama]
    ```
    - Este comando borra la rama solamente en tu repositorio local.

3. **Verificar que la Rama se Eliminó**
    - Usa `git branch` para listar las ramas y confirmar que la rama ha sido eliminada.

---

### 🌐 Pasos para Eliminar Ramas Remotamente

1. **Publicar la Rama en el Repositorio Remoto (si aún no está publicada)**
    ```bash
    git push -u origin [nombre_de_rama]
    ```

2. **Eliminar la Rama en el Repositorio Remoto**
    ```bash
    git push origin --delete [nombre_de_rama]
    ```
    - Esto elimina la rama del repositorio remoto en GitHub.

3. **Actualizar el Repositorio Local**
    ```bash
    git pull
    ```
    - Para asegurarte de que tu repositorio local está sincronizado con el remoto.

---

### 🔄 Recuperar una Rama Eliminada Localmente pero no Remotamente

- Si eliminaste una rama localmente pero no en el repositorio remoto, puedes recuperarla.
    ```bash
    git checkout [nombre_de_rama_eliminada]
    ```
    - Este comando recupera la rama desde el repositorio remoto.

---

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=rf9cfj5MARMHDdDh&amp;start=6738" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

___
%%
tags:  #paggitygithub  #Git #GitHub #EliminarRamas #ObjetivoDelTutorial #ComandosClave #PasosEliminarRamasLocalmente #PasosEliminarRamasRemotamente #RecuperarRamaEliminada #gitBranch-d #gitPushOrigin--delete #gitCheckout #gitPush-uOrigin #gitPull
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


