---
ID: 34
nombre: Ficheros - java.io y java.nio
tags:
  - pagacceso_a_datos
---
___
![](https://www.youtube.com/watch?v=VjU_B45Chbw&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=172&ab_channel=Aulaenlanube)

### 📂 Introducción a los Ficheros en Java

- **Tipos de Ficheros**
  - *Ficheros de Texto*: Almacenan datos en forma de caracteres y son legibles por humanos.
  - *Ficheros Binarios*: Almacenan datos en forma de bytes y no son legibles por humanos.

- **Proceso General para Trabajar con Ficheros**
  1. Importar paquetes necesarios (`java.io` o `java.nio`).
  2. Crear una instancia de la clase `File`.
  3. Abrir el fichero.
  4. Leer o escribir datos.
  5. Cerrar el fichero.

---

### 🛠 Herramientas y Clases en Java para Trabajar con Ficheros

- **Clase `File`**
  - Permite acceder al sistema de ficheros.
  - Crear ficheros y carpetas.
  - Obtener información de un fichero.

- **Flujos o Streams**
  - Utilizados para leer y escribir datos en ficheros.
  
- **Serialización**
  - Permite trasladar objetos a un fichero.

---

### 🗄 Acceso y Manipulación de Bases de Datos

- Se abordará cómo acceder y manipular datos almacenados en bases de datos.

---

### 📦 Paquetes en Java para Entrada y Salida de Datos

- **`java.io`**
  - Basado en flujos y bloqueos.
  
- **`java.nio`**
  - Basado en canales y buffers.
  
#### 🌐 Diferencias Técnicas entre `java.io` y `java.nio`

- **Flujos vs Canales**
  - `java.io` usa flujos unidireccionales.
  - `java.nio` usa canales bidireccionales.

- **Operaciones Bloqueantes vs No Bloqueantes**
  - `java.io` tiene operaciones bloqueantes.
  - `java.nio` permite operaciones no bloqueantes.

- **Selectores**
  - Solo disponibles en `java.nio`.

- **Mapeo de Archivos en Memoria**
  - Solo disponible en `java.nio`.

- **Codificación de Caracteres**
  - Ambos paquetes ofrecen soporte, pero `java.nio` es más flexible.

#### 🤔 ¿Cuándo usar `java.io` vs `java.nio`?

- **Para aplicaciones sencillas**: `java.io` es más fácil de usar.
- **Para aplicaciones con alta concurrencia**: `java.nio` es más eficiente.


___
%%
tags: #java  #pagacceso_a_datos  #Java #Ficheros #BasesDeDatos #TiposDeFicheros #FicherosDeTexto #FicherosBinarios #ProcesoGeneral #ClaseFile #Flujos #Streams #Serialización #PaquetesJava #javaio #javanio #FlujosVsCanales #OperacionesBloqueantes #OperacionesNoBloqueantes #Selectores #MapeoDeArchivosEnMemoria #CodificaciónDeCaracteres #AplicacionesSencillas #AplicacionesConAltaConcurrencia
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%