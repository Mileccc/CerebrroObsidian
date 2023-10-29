---
"ID:": 20
nombre: git reset, git reset --hard
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 🎯 ¿Qué son `git reset` y `git reset --hard`?

Ambos comandos de Git son esenciales para retroceder en el historial de tu repositorio, aunque funcionan de manera diferente.

---

### 🛠️ Fundamentos de `git reset`

#### 📚 Definición
- `git reset` se utiliza para **desestimar cambios en el área de preparación (staging)**, sin alterar los archivos en tu directorio de trabajo.

#### 🌠 Pasos Básicos con `git reset`
1. ***Realizar Cambios y Añadir al Área de Preparación***
    - Supongamos que tienes archivos `archivo1.txt` y `archivo2.txt` con cambios.
    ```bash
    git add archivo1.txt archivo2.txt
    ```
   
2. ***Aplicar `git reset`***
    ```bash
    git reset
    ```
    - Al ejecutar este comando, los cambios en `archivo1.txt` y `archivo2.txt` se quitan del área de preparación, pero permanecen en el directorio de trabajo.

---

### 🌈 Características de `git reset --hard`

#### 📚 Definición
- `git reset --hard` es más agresivo. Este comando **reinicia tu directorio de trabajo y el área de preparación al estado de un commit específico**.

#### 🌠 Pasos Básicos con `git reset --hard`

1. ***Identificar el Commit Objetivo***
    - Asumiendo que quieres volver al commit con hash `abc123`.
    
2. ***Ejecutar `git reset --hard`***
    ```bash
    git reset --hard abc123
    ```
    - Al hacer esto, tu directorio de trabajo y el área de preparación se restablecen al estado del commit `abc123`.

---

### 🌐 Comparación entre `git reset` y `git reset --hard`

| Comando | Área de Preparación | Directorio de Trabajo | Caso de Uso |
|---------|---------------------|-----------------------|-------------|
| `git reset` | Desestima cambios | No modifica | Desestimar cambios en el área de preparación |
| `git reset --hard` | Restablece al commit | Restablece al commit | Retroceder a un estado específico del repositorio |

---

### 📚 Otros Comandos Relacionados

- `git checkout` ***para Deshacer Cambios en Archivos Específicos***
    ```bash
    git checkout archivo_con_error.txt
    ```
    - Este comando te permite volver al último estado comiteado de un archivo específico.

---

### 🚀 Prácticas Avanzadas

Si necesitas retroceder múltiples commits, identifica el hash del commit objetivo y utiliza `git reset --hard`. Ten en cuenta que es una acción peligrosa; úsalo con precaución.

___
### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=i7waNKCFsWsvkvMX&amp;start=7428" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

___
%%
tags:  #paggitygithub  #Git #gitreset #gitresethard #historialderepositorio #áreadepreparación #directoriodetrabajo #gitadd #commit #hash #gitcheckout #prácticasavanzadas
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


