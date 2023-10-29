---
"ID:": 15
nombre: git push, git pull
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 📌 Introducción
Los comandos `git push` y `git pull` son fundamentales cuando trabajamos con repositorios remotos como GitHub. Aquí desglosaremos cada uno de estos comandos, su utilidad y cómo interactuar con ellos.

### 🚀 Git Push

#### ¿Qué hace?
El comando `git push` sube tus cambios locales a un repositorio remoto. Este comando es como "presionar un botón" para compartir tus cambios con el equipo.

#### Flujo de trabajo típico
1. Realizas cambios en tu copia local del código.
2. Utilizas `git add` para mover los cambios al área de stage.
3. Utilizas `git commit` para guardar esos cambios en tu repositorio local.
4. Utilizas `git push` para subir esos cambios al repositorio remoto.

#### Ejemplo
```bash
# Agregar cambios al stage
git add archivo1.txt

# Hacer commit de los cambios
git commit -m "Agregamos archivo1"

# Empujar los cambios al repositorio remoto
git push origin master
```

---

### 🎣 Git Pull

#### ¿Qué hace?
El comando `git pull` descarga cambios del repositorio remoto y los integra en tu repositorio local.

#### Flujo de trabajo típico
1. Otro miembro del equipo realiza y sube cambios al repositorio remoto.
2. Utilizas `git pull` para traer esos cambios a tu copia local del repositorio.

#### Ejemplo
```bash
# Tirar los cambios más recientes del repositorio remoto
git pull
```

#### Solución de problemas
Si enfrentas problemas de enlace remoto al usar `git pull`, usa el siguiente comando para configurar tu rama local para que haga seguimiento de la rama remota.

```bash
git branch -u origin/master
```

---

### 📊 Tabla de comandos

| Comando | Descripción |
| ------- | ----------- |
| `git push` | Empuja los cambios del repositorio local al repositorio remoto. |
| `git pull` | Trae los cambios del repositorio remoto al repositorio local. |
| `git add` | Agrega cambios al área de stage. |
| `git commit` | Guarda los cambios en el repositorio local. |
| `git branch -u` | Configura la rama local para que haga seguimiento de la rama remota. |

---

### 💡 Tips

* El comando `git push -u origin master` configura la rama remota como predeterminada para futuros pushes.
* Algunos IDEs tienen botones para sincronizar (`push` y `pull` al mismo tiempo), como Visual Studio Code.


### Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=DhEExB2ta93ElEEt&amp;start=4968" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


___
%%
tags:  #paggitygithub  #Git #GitHub #git-push #git-pull #Introducción #GitPush #QuéHace #FlujoDeTrabajo #Ejemplo #GitPull #SoluciónDeProblemas #TablaDeComandos #git-add #git-commit #git-branch-u #Tips #Práctica
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


