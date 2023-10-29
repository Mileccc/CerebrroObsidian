---
ID: 18
nombre: Ficheros de texto
tags:
  - pagacceso_a_datos
---
___
![[d bICXSovc.svg]]
## 📑 Gestión de Ficheros de Texto en Java

### 🛠️ Herramientas Clave para la Gestión de Ficheros

Cuando se trabaja con ficheros de texto en Java, existen tres clases fundamentales que facilitan la manipulación de datos.

1. `FileReader`: Especializada en la lectura secuencial de caracteres desde un archivo de texto.
    - **Método de Acceso**: Secuencial
    - **Operación Principal**: Lectura

2. `FileWriter`: Diseñada para la escritura secuencial de caracteres en un archivo de texto.
    - **Método de Acceso**: Secuencial
    - **Operación Principal**: Escritura

3. `PrintWriter`: Va más allá de la simple escritura y permite otorgar un formato específico a los caracteres que se escriben en el archivo.
    - **Método de Acceso**: Secuencial
    - **Operación Principal**: Escritura con Formato

| Clase        | Método de Acceso | Operación Principal  |
|--------------|------------------|----------------------|
| *FileReader*  | Secuencial       | Lectura              |
| *FileWriter*  | Secuencial       | Escritura            |
| *PrintWriter* | Secuencial       | Escritura con Formato|

### 📖 Cómo Funcionan Estas Clases

#### 📚 FileReader
- Para usar esta clase, solo hay que instanciar un objeto de ``FileReader`` y usar sus métodos para recorrer el fichero de forma secuencial.
- ***Uso común***: Ideal para operaciones de lectura simples donde no se requiere de un formato específico.

#### 📝 FileWriter
- Al igual que ``FileReader``, se crea una instancia de ``FileWriter`` para escribir caracteres en un archivo.
- ***Uso común***: Cuando solo se necesita escribir texto sin necesidad de un formato especial.

#### 🖋️ PrintWriter
- La ``PrintWriter`` es un poco más sofisticada y permite la escritura en el fichero con un formato específico.
- ***Uso común***: Útil cuando se quiere dar formato al texto escrito, como la inclusión de saltos de línea, tabulaciones, etc.

#### 📊 Comparativa

| Clase        | Uso Común                                        |
|--------------|---------------------------------------------------|
| *FileReader*  | Operaciones de lectura simples                    |
| *FileWriter*  | Escritura de texto sin formato                    |
| *PrintWriter* | Escritura de texto con formato específico         |

### 🎭 Aplicaciones y Limitaciones

Las clases mencionadas son ideales para gestionar archivos de texto de forma secuencial, pero tienen sus limitaciones. No ofrecen la flexibilidad de acceso aleatorio ni son aptas para la manipulación de datos binarios.

***Nota***: Es fundamental entender que estas clases son específicas para ficheros de texto y operan de forma secuencial, lo que puede ser una limitación en escenarios que requieran un acceso más flexible a los datos.

Es crucial elegir la clase adecuada según el tipo de operación que se desea realizar, tomando en cuenta tanto las capacidades como las limitaciones de cada una.

___
%%
tags: #pagacceso_a_datos   #Java #FicherosDeTexto #FileReader #FileWriter #PrintWriter #AccesoSecuencial #GestiónDeFicheros #OperacionesDeLectura #OperacionesDeEscritura #FormateoDeTexto #Limitaciones #ClasesJava #ManipulaciónDeDatos #UsoComún #Comparativa #Aplicaciones #OperaciónPrincipal #MétodoDeAcceso #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%