---
ID: 13
nombre: Formas de acceso a un fichero
tags:
  - pagacceso_a_datos
---
___
![[d Hw0moLLC.svg]]
### 📝 Introducción al Acceso a Ficheros

Cuando trabajamos con ficheros, la forma en que accedemos a los datos es crucial para determinar la eficiencia de nuestras operaciones. Generalmente, los ficheros se componen de registros que suelen tener el mismo tamaño. Dos métodos dominantes para acceder a estos registros son el acceso secuencial y el acceso aleatorio.


### 📚 Tipos de Acceso a Ficheros

#### 🚶 Acceso Secuencial

En el acceso secuencial, los registros se leen y se escriben en un orden específico, de principio a fin. No se puede insertar un nuevo registro en medio del fichero; toda nueva inserción se hace al final. Este método es especialmente útil para operaciones como copiar un archivo completo.

* **Clases Utilizadas en Java:**
  - ``FileReader`` y ``FileWriter`` para datos de texto.
  - ``FileInputStream`` y ``FileOutputStream`` para datos binarios.

#### 🎯 Acceso Aleatorio

El acceso aleatorio, por otro lado, permite leer o escribir datos en cualquier parte del archivo, sin tener que pasar por todos los registros previos. Esto es útil cuando necesitamos acceder a una parte específica del archivo rápidamente.

* **Clase Utilizada en Java:**
  - ``RandomAccessFile``, que implementa las interfaces ``DataInput`` y ``DataOutput``.

| Tipo de Acceso  | Características                                                 | Clases en Java            |
|-----------------|-----------------------------------------------------------------|---------------------------|
| Acceso Secuencial| Orden estricto, lectura completa, inserciones al final           | ``FileReader, FileWriter``|
| Acceso Aleatorio | Acceso no secuencial, rápido acceso a partes específicas         | ``RandomAccessFile``      |

 
___
%%
tags: #pagacceso_a_datos  #AccesoAFicheros #Java #AccesoSecuencial #AccesoAleatorio #FileReader #FileWriter #FileInputStream #FileOutputStream #RandomAccessFile #Eficiencia #DatosBinarios #DatosDeTexto #Lectura #Escritura #Recomendaciones #ClasesJava #Interfaces #DataInput #DataOutput #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%