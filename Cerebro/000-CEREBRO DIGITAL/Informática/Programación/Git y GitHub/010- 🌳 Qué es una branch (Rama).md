---
"ID:": 10
nombre: Qué es una branch (Rama)
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 📜 Introducción a Branches
Las Branches o Ramas son como flujos paralelos de desarrollo en un repositorio Git. Permiten a los desarrolladores trabajar en diferentes tareas o características simultáneamente sin interferir en el flujo principal de código.

### 🎬 Analogía de la Película
- **Película**: Representa una rama.
- **Fotogramas/Frames**: Representan commits.
- **HEAD**: Punto en el que estamos ubicados, como si fuese el fotograma actual de una película.

![[Pasted image 20231027184619.png|1500]]

### 🗺 Analogía de la Ruta
- **Ruta Principal**: La rama principal del código.
- **Ramas Secundarias**: Desviaciones o rutas alternativas en la carretera.
- **Fotografías**: Representan los commits en cada punto de la ruta.

![[Pasted image 20231027184730.png|1500]]

### 📚 Términos y Comandos Clave

| Comando | Descripción |
|---------|-------------|
| `git branch` | Lista todas las ramas del repositorio. |
| `git branch [nombre]` | Crea una nueva rama con el nombre especificado. |
| `git checkout [nombre]` | Cambia a la rama especificada. |
| `git merge [nombre]` | Fusiona la rama especificada con la rama actual. |
| `git branch -d [nombre]` | Elimina la rama especificada. |

### 📂 Casos de Uso de Ramas
- `master`: Suele ser la rama principal donde se encuentra la versión estable del código.
- `development`: Usada para realizar tareas de desarrollo antes de fusionarlas con la rama `master`.

![[Pasted image 20231027184758.png|1500]]

### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=3TGOGy0_sCb5jCaU&amp;start=3052" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
___
%%
tags:  #paggitygithub  #Introducción  #Analogía  #HEAD  #Ruta  #Ramas  #Términos  #git  #gitbranch   #Casos  #master #development
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


