---
ID: 3
nombre: Manejo  de Ficheros y Directorios en Sistemas Informáticos con Java
tags:
  - pagacceso_a_datos
---
___
[![](https://mermaid.ink/img/pako:eNp9U8tu2zAQ_BWCJxkwDPkd61bYadCijoO4QIDCl424tplQpEBSiV0jH5Njz_0E_1hXtl5Ggt60s6PZ2eXugcdGII94IrVIIF1pxqwxPgjmoPHJMIHsq4y3aI1jezaTFmNvrKQINVtK5zEBx77ptbHJ8d3LmDKx0ew7vECrlcsxFkyN9rjzht2gRguqwBm7tsAg9hmovJACJmshKEk36Lw8_tU5ZV14qQSct-BxI8lEpiWlQUCRDZrJ1NjSLlukZMLLF1P5-CF1tisDVhGpYCEa5wZKwgPNyry6mj-Ta7RIPTrmipGck62pApdPUGE-r3woQflbMLV41s3rLB6f0BtXOQrmxz_eCJrmnZU6likorLOMxaDvEcQF8GClxwZC-h5v8TUvX8MCFTZpuCPLjWY26G8hwQvgy6MzKvN4B357kZiCNprmoz5kPgHyEdWQdKVqEys3bN8ELxugkfq5EfQu2Ohfod40Kyrq6jKiLSQhb00NJ89C2jokg9T5z4IQ3KPLEtSt_y0iHYWoj-KztSTyclEmPu4Db_MEbQJS0BUect6K-y3SA_CIPgXY5xVf6TfiQebNcq9jHnmbYZtnqaAiMwkbCwmP1qBchV4LSZYqEE_h_Hzrp5Nv8xT0L2OSUo1CHh34jkfDsNO_moRhfzzsj0a9brfN9zzqhr1Ovz8eDMLBJBz3eqPRW5v_Pgl0OyEho8lwMhh0r-i_8ds_Kepbxg?type=png)](https://mermaid.live/edit#pako:eNp9U8tu2zAQ_BWCJxkwDPkd61bYadCijoO4QIDCl424tplQpEBSiV0jH5Njz_0E_1hXtl5Ggt60s6PZ2eXugcdGII94IrVIIF1pxqwxPgjmoPHJMIHsq4y3aI1jezaTFmNvrKQINVtK5zEBx77ptbHJ8d3LmDKx0ew7vECrlcsxFkyN9rjzht2gRguqwBm7tsAg9hmovJACJmshKEk36Lw8_tU5ZV14qQSct-BxI8lEpiWlQUCRDZrJ1NjSLlukZMLLF1P5-CF1tisDVhGpYCEa5wZKwgPNyry6mj-Ta7RIPTrmipGck62pApdPUGE-r3woQflbMLV41s3rLB6f0BtXOQrmxz_eCJrmnZU6likorLOMxaDvEcQF8GClxwZC-h5v8TUvX8MCFTZpuCPLjWY26G8hwQvgy6MzKvN4B357kZiCNprmoz5kPgHyEdWQdKVqEys3bN8ELxugkfq5EfQu2Ohfod40Kyrq6jKiLSQhb00NJ89C2jokg9T5z4IQ3KPLEtSt_y0iHYWoj-KztSTyclEmPu4Db_MEbQJS0BUect6K-y3SA_CIPgXY5xVf6TfiQebNcq9jHnmbYZtnqaAiMwkbCwmP1qBchV4LSZYqEE_h_Hzrp5Nv8xT0L2OSUo1CHh34jkfDsNO_moRhfzzsj0a9brfN9zzqhr1Ovz8eDMLBJBz3eqPRW5v_Pgl0OyEho8lwMhh0r-i_8ds_Kepbxg)
### 📑 Contexto General

En la era actual de la informática, los dispositivos pueden contener millones de ficheros, haciendo vital su adecuada gestión, localización y uso. Los sistemas operativos organizan estos ficheros de forma jerárquica para acceder primero a directorios y luego a los ficheros que contienen. Esta gestión se ha adaptado a la evolución de dispositivos de almacenamiento, ofreciendo estrategias unificadas para el acceso a ficheros, sin importar su ubicación.

### 🌐 Estrategias por Sistema Operativo

* ***Linux***: Utiliza un sistema de unificación de estrategias para acceder a ficheros. Por ejemplo, `/direccion/donde/esta/el/fichero.txt`.
  
* ***Windows***: Manteniene diferentes sistemas y dispositivos para el acceso, utilizando denominaciones específicas como `F:\direccion\donde\se\encuentra\el\fichero.txt` o `\\servidor\donde\esta\el\fichero.txt`.

### 🗂️ Clase File en Java

#### 🛠️ Creación de Objetos
La clase `File` es fundamental en Java para la gestión de archivos y directorios. Está ubicada en el paquete `java.io`. Para crear un objeto, se usa el constructor `public File(String path);`, donde `path` es la dirección absoluta o relativa al directorio actual.

#### 📋 Métodos Principales
* ***canRead()***: Verifica la legibilidad del fichero.
* ***canWrite()***: Verifica la escritura en el fichero.
* ***createNewFile()***: Crea un nuevo fichero.
* ***delete()***: Elimina un fichero o directorio.
* ***exists()***: Verifica la existencia del fichero o directorio.
* ***getName()***: Obtiene el nombre del fichero o directorio.
* ***getAbsolutePath()***: Obtiene la ruta absoluta.
* ***getCanonicalPath()***: Obtiene la ruta única absoluta.
* ***getPath()***: Obtiene la ruta original.
* ***getParent()***: Obtiene el directorio padre.
* ***isAbsolute()***: Verifica si la ruta es absoluta.
* ***isDirectory()***: Verifica si es un directorio válido.
* ***isFile()***: Verifica si es un fichero válido.
* ***lastModified()***: Tiempo de la última modificación en milisegundos.
* ***length()***: Obtiene el tamaño en bytes.
* ***list()***: Lista todos los ficheros y directorios del directorio indicado.
* ***list(FilenameFilter filtro)***: Lista ficheros y directorios según un filtro.
* ***mkdir()***: Crea un directorio.
* ***renameTo(File file)***: Renombra el fichero.

### 📊 Resumen

La gestión de ficheros y directorios es una actividad crucial en el desarrollo de aplicaciones informáticas. Los sistemas operativos tienen sus propias estrategias para facilitar esta tarea. En Java, la clase `File` proporciona una amplia gama de métodos para hacerlo de manera efectiva, desde la creación de ficheros hasta su modificación y verificación. Estos métodos ofrecen una gestión eficiente, permitiendo a los desarrolladores adaptarse a las diversas necesidades y contextos en los que se encuentra el almacenamiento de datos.

___
%%
tags: #pagacceso_a_datos  #GestiónDeFicheros #SistemasOperativos #Java #ClaseFile #Métodos #Linux #Windows #Directorios #Objetos #UbicaciónFicheros #Almacenamiento #DesarrolloDeAplicaciones #Informática #EstrategiasDeAcceso #PaqueteJavaIO #CreaciónDeFicheros #EliminaciónDeFicheros #VerificaciónDeFicheros #Rutas #Filtros #RenombrarFicheros #TiempoModificación #TamañoEnBytes #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%