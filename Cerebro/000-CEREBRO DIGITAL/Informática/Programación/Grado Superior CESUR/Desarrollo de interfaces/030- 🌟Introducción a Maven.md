---
ID: 30
nombre: Introducción a Maven
tags:
  - pagdesarrollo_de_interfaces
---
___
## 🌟 Introducción a Maven en el contexto de Java FX

![](https://www.youtube.com/watch?v=fDZ-wT3b2Nw&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=211&ab_channel=**Aulaenlanube**)

### 📦 ¿Qué es Maven?

Maven es una herramienta de gestión de proyectos en Java. Su principal objetivo es simplificar el proceso de construcción de proyectos, desde la compilación hasta la distribución. En este contexto, se introduce como un paso previo para entender la estructura de un proyecto en Java FX.

#### 📝 Características Clave

1. **Archivo `pom.xml`**: Contiene toda la configuración del proyecto, desde el nombre hasta las dependencias y plugins.
2. **Gestión de Dependencias**: Permite añadir librerías de forma sencilla a través del archivo `pom.xml`.
3. **Ciclo de Vida**: Define una serie de fases para construir y desplegar un proyecto.

```xml
<!-- Ejemplo de un archivo pom.xml -->
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>my-app</artifactId>
  <version>1.0</version>
  <dependencies>
    <!-- Dependencias aquí -->
  </dependencies>
</project>
```

### 📂 Estructura de un Proyecto Maven

Un proyecto en Maven tiene una estructura de carpetas y archivos específica que facilita la organización del código y los recursos.

#### 🗂️ Carpetas Principales

- **src**: Contiene el código fuente.
  - **main**: Código fuente principal.
  - **test**: Código para pruebas.
- **target**: Contiene los archivos compilados.
- **`pom.xml`**: Archivo de configuración de Maven.

#### 📄 Archivos y Subcarpetas

- **src/main/java**: Archivos `.java` del código fuente.
- **src/test/java**: Archivos `.java` para pruebas.
- **src/main/resources**: Archivos de configuración, imágenes, etc.
- **src/test/resources**: Archivos necesarios para realizar pruebas.

### 🛠️ Gestión de Dependencias

Maven facilita la gestión de dependencias a través del archivo `pom.xml`. Simplemente añadiendo una sección de dependencias, Maven descargará e incluirá las librerías necesarias en el proyecto.

```xml
<!-- Ejemplo de cómo añadir una dependencia en pom.xml -->
<dependencies>
  <dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.26</version>
  </dependency>
</dependencies>
```

### 🔄 Ciclo de Vida de Maven

El ciclo de vida de Maven se compone de una serie de fases que definen los pasos para construir y desplegar un proyecto. Algunas fases comunes son:

1. **validate**: Valida que el proyecto es correcto.
2. **compile**: Compila el código fuente.
3. **test**: Realiza pruebas.
4. **package**: Empaqueta el código en un formato distribuible.
5. **install**: Instala el paquete en el repositorio local.
6. **deploy**: Copia el paquete en un repositorio remoto.
7. **clean**: Elimina todos los archivos compilados de la carpeta target

```bash
# Ejemplo de comandos de Maven
mvn validate
mvn compile
mvn test
```

___
## 🌟 Instalación y Configuración de Maven en Visual Studio Code

### 📥 Descarga de Maven

Para empezar con Maven, primero necesitas descargarlo. Puedes encontrar un enlace de descarga en la página oficial. Una vez en la página, dirígete a la sección de `Download` y selecciona uno de los binarios disponibles. Por ejemplo, puedes descargar el archivo ZIP.

```bash
# Ejemplo de cómo descargar Maven
1. Ir al enlace de descarga.
2. Hacer clic en 'Download'.
3. Seleccionar el archivo ZIP.
```

### 📂 Extracción y Ubicación del Archivo

Una vez descargado el archivo ZIP, debes extraerlo en una carpeta de tu sistema operativo. Por ejemplo, puedes extraerlo en la carpeta `Users` bajo tu nombre de usuario.

```bash
# Ejemplo de cómo extraer el archivo
1. Hacer clic derecho en el archivo ZIP.
2. Seleccionar 'Extraer aquí'.
3. Mover la carpeta extraída a la ubicación deseada.
```

### 🛠️ Configuración en Visual Studio Code

#### 🔌 Instalación de la Extensión de Maven

Para trabajar con Maven en Visual Studio Code, es necesario instalar la extensión de Maven para Java. Puedes hacerlo desde el panel de extensiones.

```bash
# Ejemplo de cómo instalar la extensión
1. Abrir Visual Studio Code.
2. Ir al panel de extensiones.
3. Buscar 'Maven for Java'.
4. Hacer clic en 'Instalar'.
```

#### 🗂️ Creación de un Nuevo Proyecto Maven

Una vez instalada la extensión, puedes crear un nuevo proyecto Maven desde el explorador de proyectos de Visual Studio Code.

```bash
# Ejemplo de cómo crear un nuevo proyecto
1. Abrir una nueva ventana en Visual Studio Code.
2. Ir al explorador de proyectos.
3. Hacer clic en 'Create Java Project'.
4. Seleccionar 'Maven' como tipo de proyecto.
```

#### 📝 Configuración de Arquetipos

Maven ofrece una lista de arquetipos, que son plantillas de proyectos preconfiguradas. Puedes seleccionar una según el tipo de aplicación que desees desarrollar. Sin embargo, para este ejemplo, crearemos un proyecto básico.

```bash
# Ejemplo de cómo seleccionar un arquetipo
1. En la lista de arquetipos, seleccionar 'Create Basic Maven Project'.
2. Ingresar el 'Group ID' y el 'Artifact ID'.
3. Seleccionar la carpeta donde se creará el proyecto.
```

#### 📄 Estructura del Proyecto

Una vez creado el proyecto, tendrás una estructura de carpetas y archivos generada automáticamente por Maven.

![[Pasted image 20231018105657.png|500]]

#### 🛠️ Configuración del Path de Maven

Para que Visual Studio Code reconozca Maven, debes especificar la ruta del ejecutable `mvn.cmd` en las configuraciones del editor.

```json
{
  "maven.executable.path": "/ruta/a/mvn.cmd"
}
```

![[Pasted image 20231018105826.png]]
### 🚀 Ejecución de Comandos Maven

Una vez configurado el path, podrás ejecutar comandos de Maven desde la interfaz de Visual Studio Code. Por ejemplo, puedes compilar el proyecto y verificar que todo funciona correctamente.

```bash
# Ejemplo de cómo ejecutar comandos
1. Ir al panel de Maven en Visual Studio Code.
2. Seleccionar el comando deseado, como 'Compile'.
3. Ejecutar el comando.
```

Con estos pasos, habrás configurado Maven en Visual Studio Code y estarás listo para empezar a desarrollar tus proyectos Java.

___
## 🌟 Creación de un Proyecto de Ejemplo con Maven en Java

### 🎮 Introducción al Proyecto de Juego de Mecanografía

Para ilustrar cómo funciona Maven en un proyecto Java real, vamos a crear un juego de mecanografía. Este juego requerirá una conexión a una base de datos MySQL, por lo que también necesitaremos gestionar dependencias.

### 📁 Preparación del Proyecto

#### 📋 Copiar Clases Existentes

Si ya tienes clases Java para el juego de mecanografía, puedes copiarlas en la carpeta `src/main/java` de tu proyecto Maven. Asegúrate de que las clases estén en el paquete correcto.

```bash
# Pasos para copiar las clases
1. Localiza las clases `JuegoMecanografia.java` y `JuegoMecanografiaABC.java`.
2. Copia y pega ambas clases en `src/main/java/com/aula/`.
```

#### 🛠️ Ajustes en el Código

Es posible que necesites hacer algunos ajustes en el código, como actualizar el paquete en el que se encuentran las clases.

```java
// Asegúrate de que el paquete sea el correcto
package com.aula;
```

### 📚 Gestión de Dependencias con Maven

#### 📝 Actualización del Archivo `pom.xml`

Para gestionar las dependencias, debemos modificar el archivo `pom.xml`. En este caso, necesitamos añadir la dependencia del conector MySQL.

```xml
<!-- Dependencia del conector MySQL -->
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-java</artifactId>
  <version>8.0.33</version>
</dependency>
```

#### ⚠️ Resolución de Problemas de Dependencias

Si Maven te alerta sobre vulnerabilidades en la versión del conector, puedes actualizarla fácilmente. Maven incluso te sugerirá la versión recomendada.

```xml
<!-- Versión actualizada del conector MySQL -->
<version>8.0.33</version> <!-- Versión recomendada -->
```


#### 🐛 Resolución de Errores en Tiempo de Ejecución

Si olvidas incluir la dependencia del conector MySQL, la aplicación se ejecutará, pero no podrás almacenar ni recuperar puntuaciones. Este es un error en tiempo de ejecución, no en tiempo de compilación.

```java
// Ejemplo de cómo capturar la excepción
try {
  // Código para conectar con la base de datos
} catch (SQLException e) {
  e.printStackTrace();
}
```

___
## 🌟 Acciones Comunes con Maven en Java

### 🛠️ Limpieza del Proyecto con Maven

#### 🗑️ Uso del Comando `clean`

Maven ofrece un comando útil para limpiar tu proyecto, eliminando todos los archivos compilados y la carpeta `target`. Para hacer esto, ejecuta el comando `clean`.

Este comando eliminará la carpeta `target` y todos los archivos compilados dentro de ella. Si observas la estructura de carpetas de tu proyecto, notarás que la carpeta `target` ha desaparecido.

### 📦 Empaquetado del Proyecto

#### 📝 Uso del Comando `package`

Para empaquetar tu proyecto, puedes utilizar el comando `package`. Este comando generará un archivo `.jar` o `.war` en la carpeta `target`, dependiendo de lo que hayas especificado en tu archivo `pom.xml`.

### 🏗️ Instalación de Paquetes en el Repositorio Local

#### 📥 Uso del Comando `install`

Si deseas instalar el paquete en tu repositorio local de Maven para usarlo como dependencia en otros proyectos, puedes hacerlo con el comando `install`.


#### 📑 Referencia en `pom.xml`

Para utilizar este paquete como dependencia en otros proyectos, deberás añadir la información correspondiente en el archivo `pom.xml` del nuevo proyecto.

```xml
<!-- Dependencia del proyecto instalado localmente -->
<dependency>
  <groupId>com.aula</groupId>
  <artifactId>meca2</artifactId>
  <version>1.0</version>
</dependency>
```

### 🔄 Uso de Dependencias en Proyectos Nuevos

#### 🆕 Creación de un Nuevo Proyecto

Para demostrar cómo usar una dependencia local, vamos a crear un nuevo proyecto Maven.

1. Abre un nuevo proyecto en tu IDE.
2. Configura el `groupId` y el `artifactId` (por ejemplo, `com.aula2` y `meca2`).
3. Guarda el proyecto en una carpeta en tu escritorio llamada `meca2`.

#### 📋 Añadir Dependencia al Nuevo Proyecto

Para utilizar clases del proyecto original en este nuevo proyecto, añade la dependencia en el archivo `pom.xml`.

```xml
<!-- Dependencia del proyecto original -->
<dependency>
  <groupId>com.aula</groupId>
  <artifactId>meca</artifactId>
  <version>1.0</version>
</dependency>
```

#### 🎮 Ejecución del Juego desde el Nuevo Proyecto

Una vez añadida la dependencia, puedes crear una instancia de la clase `JuegoMecanografia` en el `main` del nuevo proyecto.

```java
// Crea una instancia de la clase JuegoMecanografia
new JuegoMecanografia();
```

Al ejecutar este nuevo proyecto, deberías poder jugar al juego de mecanografía y ver tus puntuaciones almacenadas en la base de datos, todo gracias a la dependencia añadida.

### 📚 Dependencias Anidadas

#### 🔄 Dependencias en Proyectos Dependientes

Si el proyecto original tenía dependencias (como el conector MySQL), no necesitas volver a añadirlas en el nuevo proyecto. Estas dependencias se heredan automáticamente.

```xml
<!-- No es necesario añadir la dependencia del conector MySQL en el nuevo proyecto -->
```



___
%%
tags: #pagdesarrollo_de_interfaces #Maven #JavaFX #GestiónDeProyectos #CaracterísticasClave #EstructuraDeProyecto #GestiónDeDependencias #CicloDeVida #Instalación #Configuración #VisualStudioCode #Descarga #Extracción #ExtensiónMaven #CreaciónDeProyecto #Arquetipos #PathDeMaven #EjecuciónDeComandos #ProyectoDeEjemplo #JuegoDeMecanografía #PreparaciónDelProyecto #CopiarClases #AjustesEnCódigo #ActualizaciónPomXml #ResoluciónDeProblemas #ErroresEnTiempoDeEjecución #LimpiezaDelProyecto #EmpaquetadoDelProyecto #InstalaciónDePaquetes #ReferenciaPomXml #UsoDeDependencias #DependenciasAnidadas
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%