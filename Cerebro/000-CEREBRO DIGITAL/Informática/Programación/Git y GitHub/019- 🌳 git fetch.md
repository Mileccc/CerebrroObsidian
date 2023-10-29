---
"ID:": 19
nombre: git fetch
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 🎯 Propósito de `git fetch`

`git fetch` se utiliza para obtener el historial de cambios de un repositorio remoto sin modificar los archivos en tu repositorio local. Este comando es útil para revisar cambios remotos antes de decidir si quieres incorporarlos en tu rama local.

---

### 🛠️ Comandos Esenciales

| Comando | Descripción |
|---------|-------------|
| `git fetch` | Obtiene el historial del repositorio remoto sin actualizar los archivos locales. |
| `git log --oneline --all` | Muestra un registro de todos los cambios, incluidos los obtenidos con `git fetch`. |
| `git pull` | Actualiza tanto el historial como los archivos en el repositorio local desde el remoto. |

---

### 🌠 Pasos para Utilizar `git fetch`

1. ***Verificar el Repositorio Actual***
    - Antes de ejecutar `git fetch`, asegúrate de saber en qué rama te encuentras y de tener la última versión.

2. ***Ejecutar `git fetch`***
    ```bash
    git fetch
    ```
    - Al hacer esto, obtendrás el historial de cambios del repositorio remoto sin modificar tus archivos locales.

3. ***Inspeccionar los Cambios***
    - Para ver los cambios remotos, usa el comando:
    ```bash
    git log --oneline --all
    ```
    Esto muestra un registro de todas las modificaciones, incluidas las que se obtuvieron con `git fetch`.

---

### 🌐 `git fetch` vs `git pull`

Mientras que `git fetch` solo obtiene el historial, `git pull` realiza una operación más completa: actualiza el historial y también incorpora los cambios en los archivos locales. Utiliza `git fetch` si sólo quieres inspeccionar los cambios antes de decidir si integrarlos o no.

---

### 📚 Herramientas Alternativas y Limitaciones

- *Git Tree*: Si estás utilizando macOS o Linux, puedes usar `git tree` para una visualización más gráfica del historial. Este comando no está disponible en Windows.

- *Navegador Web*: Si no quieres usar `git fetch`, puedes revisar el historial de cambios directamente en la página del repositorio remoto.

---

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=65y3uihOhxaDGcxm&amp;start=7108" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

___
%%
tags:  #paggitygithub  #Git #GitHub #gitFetch #PropósitoDeGitFetch #ComandosEsenciales #gitLog--oneline--all #gitPull #PasosParaUtilizarGitFetch #VerificarElRepositorioActual #EjecutarGitFetch #InspeccionarLosCambios #gitFetchVsGitPull #HerramientasAlternativasYLimitaciones #GitTree #NavegadorWeb
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


