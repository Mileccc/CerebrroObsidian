---
ID: 13
nombre: Configuración del Entorno de Desarrollo en Java
tags:
  - pagdesarrollo_de_interfaces
---
___
### 🚀 Inicio con OpenJDK 14

Si estás buscando trabajar en proyectos de Java de manera gratuita, OpenJDK 14 es tu elección ideal. Para instalarlo, sigue estos pasos:

1. Ve al sitio web del fabricante y descarga el paquete correspondiente a tu sistema operativo.
2. Descomprime el paquete.
3. Añade la dirección de la carpeta `bin` al PATH del sistema.

### 🎬 Configuración de OpenFX

OpenFX es una biblioteca que necesitarás para trabajar con JavaFX. Puedes elegir entre su versión LTS (Long Term Support), que es la versión 11, o la más reciente, que es la versión 14. Al igual que con OpenJDK, deberás:

1. Descargar desde el sitio web del fabricante.
2. Añadir las librerías al PATH del sistema.

### 💾 Instalación de Eclipse como IDE

Eclipse es el IDE de desarrollo recomendado para Java en este contexto. Para instalarlo:

1. Descarga el paquete del proveedor.
2. Descomprime en la carpeta de tu elección.

### 📚 Integración de OpenJavaFX en Eclipse

Para un desarrollo fluido en JavaFX con Eclipse, sigue los siguientes pasos:

![[Pasted image 20231011173335.png]]

1. Asegúrate de que el JRE y el JDK (en este caso OpenJDK 14) estén bien detectados por Eclipse.
2. Añade el SDK de JavaFX 14 a las librerías de Eclipse mediante el menú ``Eclipse -> Window -> Preferences -> Java -> Build Path -> User Libraries -> New``.

![[Pasted image 20231011173405.png]]

![Introducción JAVAFX/OPENJFX v14 - 01 - Entorno de trabajo - YouTube](https://www.youtube.com/watch?v=bvMoo67LzIA)

### 🏗️ Creación de un Nuevo Proyecto

Una vez configurado todo, puedes crear un nuevo proyecto JavaFX en Eclipse. Asegúrate de:

![[Pasted image 20231011173300.png]]

1. Añadir tu librería de JavaFX al CLASSPATH del nuevo proyecto.
2. Evitar la creación del archivo `module-info.java`.
3. Crear un `Main.java`, un archivo FXML y un controlador, tomando como base el ejemplo del fabricante.

![[Pasted image 20231011173211.png]]

![Introducción JAVAFX/OPENJFX v14 - 02 - Hola mundo - YouTube](https://www.youtube.com/watch?v=lbjg1I9hkZA)

### 🎨 Mejorando la Experiencia con E(fx)clipse y Scene Builder

Para una experiencia de desarrollo más rica, añade las siguientes herramientas:

* ***E(fx)clipse***: Este plugin mejora la experiencia con Eclipse, especialmente en lo que respecta a la sintaxis resaltada en archivos FXML.
* ***Scene Builder de Gluon***: Esta herramienta permite el diseño visual de las interfaces en archivos FXML.

![Introducción JAVAFX/OPENJFX v14 - 03 - Scene Builder - YouTube](https://www.youtube.com/watch?v=m3HjEvj4A70)

### 🎭 Áreas Principales de Scene Builder

Scene Builder es una herramienta útil para la manipulación visual de archivos FXML y consta de:

![[Pasted image 20231011173131.png]]

1. ***Lista de componentes***: Aquí encontrarás las diferentes librerías y componentes que puedes añadir a tu diseño.
2. ***Árbol de componentes***: Esta zona muestra un árbol con todos los elementos y sus contenedores.
3. ***Zona de trabajo***: Previsualización de tu diseño.
4. ***Propiedades***: Aquí puedes modificar las propiedades de un elemento seleccionado.

Con estos pasos, tienes todo lo necesario para empezar a desarrollar aplicaciones Java con una sólida base de herramientas y un entorno de desarrollo bien configurado.



___








































___
%%
tags: #pagdesarrollo_de_interfaces #Java #OpenJDK14 #OpenFX #Eclipse #IDE #JavaFX #OpenJavaFX #CLASSPATH #module-info.java #Main.java #FXML #Controlador #E(fx)clipse #SceneBuilder #Gluon #Componentes #ÁrbolDeComponentes #ZonaDeTrabajo #Propiedades 
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%