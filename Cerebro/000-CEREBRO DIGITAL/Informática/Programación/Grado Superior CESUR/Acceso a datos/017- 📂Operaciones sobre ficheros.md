---
ID: 17
nombre: Operaciones sobre ficheros
tags:
  - pagacceso_a_datos
---
___
![[d mEn15Urh.svg]]
### 🎓 Conceptos Básicos

Las operaciones fundamentales que se pueden llevar a cabo en ficheros, independientemente del tipo de acceso, son:

- Crear el fichero
- Abrir el fichero
- Cerrar el fichero
- Leer datos del fichero
- Escribir datos en el fichero

### 📖 Acceso Secuencial: Operaciones y Particularidades

El acceso secuencial se refiere a la manera en la que los registros se leen y se escriben en un orden específico, de principio a fin. Algunas operaciones particulares de este tipo de acceso son:

#### 🕵️‍♀️ Consulta de Datos

Para consultar información en un fichero de acceso secuencial, es necesario comenzar desde el primer registro y moverse secuencialmente a través de cada uno hasta encontrar el registro deseado.

#### 📝 Añadir Datos

Con el acceso secuencial, la inserción de nuevos datos o registros solo se puede realizar al final del fichero.

#### ❌ Eliminación de Datos

Para eliminar registros, se debe usar un fichero auxiliar donde se copian todos los registros excepto el que se desea eliminar.

### 🎯 Acceso Aleatorio: Operaciones y Flexibilidad

En el acceso aleatorio, los registros se pueden leer o escribir en cualquier punto del archivo, lo que facilita ciertas operaciones:

#### 🕵️‍♀️ Consulta de Datos

Realizar consultas es más directo: basta con conocer la clave del registro que se busca. Al aplicar una función a esta clave, se obtiene la dirección exacta del registro.
 
#### 📝 Añadir Datos

Para insertar un nuevo registro, se usa la clave y una función de cálculo para determinar la ubicación exacta dentro del fichero donde se insertará.

#### ❌ Eliminación de Datos

En este caso, se puede marcar un campo específico en el registro para indicar que debe ser eliminado, aunque físicamente puede seguir existiendo en el fichero. También se permite la eliminación física si se requiere.

---

En resumen, tanto el acceso secuencial como el acceso aleatorio tienen sus pros y contras, y cada uno es útil para diferentes escenarios. El acceso secuencial es más lineal y restringido en cuanto a manipulación de datos, mientras que el acceso aleatorio ofrece más flexibilidad y eficiencia en ciertas tareas.

 
___
%%
tags: #pagacceso_a_datos  #Ficheros #AccesoSecuencial #AccesoAleatorio #OperacionesBasicas #CrearFichero #AbrirFichero #CerrarFichero #LeerDatos #EscribirDatos #ConsultaDeDatos #AñadirDatos #EliminarDatos #Flexibilidad #Eficiencia #ManipulaciónDeDatos #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%