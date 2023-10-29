---
"ID:": 3
nombre: Configuración
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
### 🎯 Pasos Iniciales

1. **Abrir la terminal de Git**: Mantener presionado `Shift`, hacer clic derecho y seleccionar `Git Bash Here`.

#### 📝 Tabla de Comandos para Pasos Iniciales

| Comando | Descripción |
| ------- | ----------- |
| `Shift + Click Derecho` | Abre un menú contextual donde puedes seleccionar `Git Bash Here` |

### 🙋 Configuración del Usuario

1. **Nombre de usuario**: Es crucial identificarte, especialmente para repositorios externos como GitHub.
2. **Correo Electrónico**: Debe ser el mismo que usarás en GitHub o cualquier otro repositorio externo.

#### 📝 Tabla de Comandos para Configuración de Usuario

| Comando | Descripción |
| ------- | ----------- |
| `git config --global user.name "tu_nombre"` | Establece tu nombre de usuario globalmente en Git |
| `git config --global user.email "tu_email"` | Establece tu email globalmente en Git |

### 📝 Editor de Código

1. **Seleccionar editor**: Define el editor de código que se utilizará con Git. 
2. **Opciones del editor**: Añadir opciones específicas para cómo Git interactúa con tu editor.

#### 📝 Tabla de Comandos para Editor de Código

| Comando | Descripción |
| ------- | ----------- |
| `git config --global core.editor "code --wait"` | Establece Visual Studio Code como el editor predeterminado y espera hasta que el archivo se cierre |

### 🔄 Manejo de Saltos de Línea

1. **Windows o Unix**: La forma en que los saltos de línea son tratados varía dependiendo del sistema operativo.
2. **Configuración**: Configura cómo Git debería manejar los saltos de línea.

#### 📝 Tabla de Comandos para Saltos de Línea

| Comando | Descripción |
| ------- | ----------- |
| `git config --global core.autocrlf true` | En Windows, convierte los saltos de línea CRLF a LF en el repositorio y viceversa |
| `git config --global core.autocrlf input` | En Unix/Mac, solo convierte los saltos de línea CRLF a LF en el repositorio |

### 🔍 Verificar y Consultar Configuración

1. **Verificar**: Comprobar que todos los comandos han surtido efecto.
2. **Ayuda**: Si necesitas más información sobre las opciones de configuración.

#### 📝 Tabla de Comandos para Verificar Configuración

| Comando | Descripción |
| ------- | ----------- |
| `git config --global -e` | Abre el archivo de configuración global para verificar los cambios |
| `git config --global -l` | Lista toda la configuración global actual en la terminal |
| `git config -h` | Muestra las opciones de ayuda para la configuración de Git |

### Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=WV3WO7EDPyPx7YoW&amp;start=783" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

___
%%
tags:  #paggitygithub  #gitConfigUserName #gitConfigUserEmail #coreEditor #coreAutocrlf #gitConfigGlobalE #gitConfigGlobalL #gitConfigH
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


