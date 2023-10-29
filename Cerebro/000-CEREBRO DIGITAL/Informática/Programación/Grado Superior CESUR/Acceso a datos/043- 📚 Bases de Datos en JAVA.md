---
ID: 43
nombre: Bases de Datos en JAVA
tags:
  - pagacceso_a_datos
---
___
![](https://www.youtube.com/watch?v=9xybdEJmLWc&list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu&index=183&ab_channel=Aulaenlanube)

### 🌱 Conceptos Básicos de Bases de Datos

1. **Definición de Información**: La información es la base de nuestra sociedad actual. Para almacenar y acceder a esta información, necesitamos sistemas de almacenamiento fiables, fáciles de usar y eficientes.

2. **¿Qué es una Base de Datos?**: Una base de datos es un conjunto estructurado de datos interrelacionados y almacenados digitalmente. Estos datos están organizados de tal manera que un Sistema Gestor de Bases de Datos (SGBD) pueda acceder, manejar o actualizarlos de manera eficiente.

3. **Sistema Gestor de Bases de Datos (SGBD)**: Son aplicaciones específicas que gestionan las bases de datos. Permiten acceder, manipular, borrar, eliminar o modificar información.

```java
// Ejemplo de conexión a una base de datos en Java utilizando JDBC
import java.sql.Connection;
import java.sql.DriverManager;

public class DatabaseConnection {
    public static void main(String[] args) {
        try {
            Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydatabase", "username", "password");
            System.out.println("Conexión exitosa");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### 🔄 Transformación de Datos en Información

1. **Datos en Bruto**: Son los datos sin procesar almacenados en la base de datos. Por ejemplo, en una agenda telefónica, los datos serían todos los nombres de los contactos y todos los teléfonos.

2. **Procesamiento de Datos**: A través de distintas instrucciones y procesamiento, podemos acceder a datos específicos. 

```sql
-- Ejemplo de consulta SQL para obtener el teléfono de un contacto llamado Pepe
SELECT telefono FROM agenda WHERE nombre = 'Pepe';
```

### 📊 Componentes Comunes en Bases de Datos

1. **Tablas**: Son el componente principal en bases de datos relacionales. Están formadas por distintos campos y normalmente se relacionan unas con otras.

    - *Ejemplo*: Tabla de `Contacto` con campos `nombre`, `apellido`, `teléfono` y `correo electrónico`.

2. **Consultas**: Se utilizan para obtener información concreta de la base de datos. También se pueden utilizar para modificar o borrar datos.

    - *Ejemplo*: Consulta para obtener el número de teléfono de un contacto específico.

3. **Macros**: Representan un conjunto de instrucciones que realizan una operación determinada.

    - *Ejemplo*: Una macro que guarda un contacto eliminado en otra tabla llamada `Contactos_Eliminados`.

```sql
-- Ejemplo de macro SQL para mover un contacto eliminado a otra tabla
DELIMITER //
CREATE TRIGGER move_deleted_contact
BEFORE DELETE ON Contacto
FOR EACH ROW
BEGIN
    INSERT INTO Contactos_Eliminados (nombre, apellido, telefono, correo_electronico) VALUES (OLD.nombre, OLD.apellido, OLD.telefono, OLD.correo_electronico);
END;
//
DELIMITER ;
```

____
## Sistemas Gestores de Bases de Datos
### 🌟 Introducción a los Sistemas Gestores de Bases de Datos (SGBD)

Los Sistemas Gestores de Bases de Datos (SGBD) actúan como intermediarios entre los datos almacenados en una base de datos y las aplicaciones que necesitan acceder a esos datos. Facilitan la manipulación y acceso a la información de manera sencilla y eficiente.

### 📚 Modelos de Datos en SGBD

Un aspecto crucial de los SGBD es que se construyen en base a un **modelo de datos**. Este modelo es un conjunto de conceptos y reglas que determinan cómo se estructuran las bases de datos.

1. **Estructura de Datos**: Define cómo se almacenan y organizan los datos en la base de datos.

2. **Operadores Asociados**: Son las operaciones que se pueden realizar sobre los datos, como consultas, inserciones, actualizaciones y eliminaciones.

### 🌳 Generaciones de Modelos de Datos

Los modelos de datos han evolucionado a lo largo del tiempo, y podemos categorizarlos en diferentes generaciones:

1. **Modelos Jerárquicos y en Red**: Fueron los primeros en ser utilizados. En estos modelos, los datos se organizan en una estructura jerárquica o en una red de nodos.

2. **Modelos Relacionales**: Introdujeron el concepto de tablas y relaciones entre ellas, lo que facilitó la manipulación y consulta de datos.

    ```sql
    -- Ejemplo de consulta SQL en un modelo relacional
    SELECT * FROM empleados WHERE salario > 50000;
    ```

3. **Modelos Orientados a Objetos**: Permiten almacenar objetos y sus relaciones directamente en la base de datos, lo que es especialmente útil para aplicaciones orientadas a objetos.

    ```java
    // Ejemplo de almacenamiento de un objeto en una base de datos orientada a objetos
    Employee emp = new Employee("John", 30);
    db.store(emp);
    ```

4. **Modelos NoSQL**: Son modelos más flexibles que permiten el almacenamiento de datos no estructurados, como documentos JSON o pares clave-valor.

    ```json
    // Ejemplo de documento JSON en una base de datos NoSQL
    {
        "name": "Alice",
        "age": 25,
        "email": "alice@email.com"
    }
    ```

___
## 🌐 Introducción a SQL en el Contexto de Bases de Datos en JAVA 🛠️

### 📚 Panorama General de SQL

SQL (Structured Query Language) es el lenguaje estándar para trabajar con bases de datos relacionales. Este lenguaje se divide en varios sub-lenguajes, cada uno con una función específica:

1. **DDL (Data Definition Language)**: Define la estructura de las bases de datos y sus tablas.
2. **DML (Data Manipulation Language)**: Utilizado para manipular y acceder a los datos.
3. **DCL (Data Control Language)**: Gestiona los usuarios y sus permisos.
4. **TCL (Transaction Control Language)**: Controla las transacciones en la base de datos.

### 🏗️ DDL: Definición de la Estructura de Datos

DDL se encarga de definir la estructura de las bases de datos y las tablas. Permite crear tablas y definir los campos y sus tipos de datos. Al igual que en Java, las bases de datos pueden tener distintos tipos de datos como enteros o cadenas de texto.

```sql
-- Ejemplo de creación de tabla en SQL
CREATE TABLE Contacto (
    nombre VARCHAR(50),
    correo VARCHAR(50) PRIMARY KEY
);
```

### 🎛️ DML: Manipulación y Acceso a Datos

DML se utiliza para manipular y acceder a los datos almacenados. Las cuatro instrucciones principales son `SELECT`, `INSERT`, `UPDATE`, y `DELETE`.

```sql
-- Ejemplo de consulta para obtener todos los contactos
SELECT * FROM Contacto;
```

### 👥 DCL: Control de Usuarios y Permisos

DCL se encarga de gestionar los usuarios que tienen acceso a la base de datos y define los permisos que tienen.

```sql
-- Ejemplo de asignación de permisos en SQL
GRANT SELECT, INSERT ON Contacto TO 'usuario';
```

### 🔄 TCL: Control de Transacciones

TCL gestiona las transacciones en la base de datos. Una transacción es una secuencia de instrucciones que se deben ejecutar de forma atómica para mantener la consistencia de los datos.

```sql
-- Ejemplo de transacción en SQL
BEGIN;
UPDATE Contacto SET nombre='Juan' WHERE correo='juan@email.com';
COMMIT;
```

### 📋 Ejemplo Práctico: Creación de una Agenda de Contactos

Vamos a crear una base de datos simple para almacenar contactos en una agenda. La tabla tendrá campos para el nombre y el correo electrónico del contacto, y el correo será la clave primaria.

1. **Creación de la Base de Datos**: La llamaremos `Agenda`.
2. **Creación de la Tabla**: La tabla se llamará `Contacto`.
3. **Definición de Campos**: Tendrá campos para `nombre` y `correo`, ambos de tipo texto.
4. **Clave Primaria**: El correo será la clave primaria, lo que garantiza que cada contacto tenga un correo único.

```sql
-- Creación de la tabla Contacto con campos y clave primaria
CREATE TABLE Contacto (
    nombre VARCHAR(50),
    correo VARCHAR(50) PRIMARY KEY
);
```

### 🌟 MySQL: El SGBD que Utilizaremos

MySQL fue creado en 1995 y es ampliamente utilizado para gestionar grandes volúmenes de datos. Está escrito principalmente en C++ y también tiene componentes en C. Fue adquirido por Sun Microsystems en 2008, lo que llevó a la creación de un fork llamado MariaDB, que sigue siendo de código abierto y en desarrollo activo.

___
## 🛠️ Instalación de XAMPP para Bases de Datos en JAVA 🌐

### 📦 ¿Qué es XAMPP y Por Qué lo Necesitamos? 🤔

XAMPP es un paquete de software libre que proporciona un entorno de desarrollo local para web. Este paquete incluye varios componentes:

1. **Servidor Web Apache**: Para alojar aplicaciones web.
2. **Sistema Gestor de Base de Datos MySQL**: Para gestionar bases de datos.
3. **Lenguajes de Programación PHP y Perl**: Para el desarrollo backend.

Aunque nuestro enfoque principal es utilizar el Sistema Gestor de Base de Datos MySQL, XAMPP es beneficioso porque también nos ofrece un servidor web y una herramienta de gestión de bases de datos llamada `phpMyAdmin`.

### 📥 Pasos para la Descarga e Instalación 🔄

1. **Descargar XAMPP**: Haga clic en el botón de descarga de XAMPP adecuado para su sistema operativo. En este ejemplo, se utiliza Windows.

    ```markdown
    [Descargar XAMPP](https://www.apachefriends.org/index.html)
    ```

2. **Ejecutar el Instalador**: Una vez descargado, ejecute el archivo de instalación.

    ```plaintext
    Doble clic en el archivo descargado -> Siga las instrucciones del instalador
    ```

3. **Configuración del Idioma**: Durante la instalación, se le pedirá que seleccione el idioma. Elija según su preferencia y haga clic en `Next`.

4. **Finalizar la Instalación**: Espere a que se complete la instalación. Una vez finalizada, se le preguntará si desea iniciar el Panel de Control de XAMPP. Deje esta opción marcada.

### 🎛️ Panel de Control de XAMPP 🖥️

Una vez instalado, XAMPP incluye un Panel de Control que permite gestionar los distintos componentes. Para acceder a este panel:

1. **Ubicación del Panel de Control**: Vaya a la carpeta donde instaló XAMPP. Por defecto, suele ser `C:\xampp`.

    ```plaintext
    C:\xampp -> xampp-control.exe
    ```

2. **Iniciar Servicios**: En el Panel de Control, haga clic en `Start` junto a Apache y MySQL. Cuando se iluminen en verde, significa que los servicios están activos.

### 🛠️ Configuración Inicial de MySQL a través de phpMyAdmin 🗄️

1. **Acceso a phpMyAdmin**: Haga clic en el botón `Admin` junto a MySQL en el Panel de Control de XAMPP.

2. **Interfaz de phpMyAdmin**: Se abrirá una nueva ventana en su navegador con la interfaz de phpMyAdmin, que es una herramienta basada en PHP para gestionar bases de datos MySQL.

Con estos pasos, habrá instalado y configurado XAMPP en su sistema, lo que le permitirá interactuar con bases de datos MySQL a través de Java. Ahora está listo para empezar a desarrollar sus proyectos.

___
## 🗂️ Creación de la Base de Datos en JAVA 🛠️

### 🌟 Introducción a la Base de Datos 🌟

Antes de empezar con nuestro proyecto en Java, necesitamos una base de datos. Aquí, vamos a crear una base de datos muy sencilla llamada `Agenda` para almacenar contactos.

### 🖱️ Creación de la Base de Datos en phpMyAdmin 🖱️

1. **Acceso a phpMyAdmin**: Abre phpMyAdmin desde el Panel de Control de XAMPP.
2. **Nueva Base de Datos**: Haz clic en `Nueva` para crear una nueva base de datos.
3. **Nombre y Codificación**:
    - **Nombre**: `Agenda`
    - **Codificación**: `UTF-8 Spanish`
  
    ```markdown
    La codificación UTF-8 Spanish permite almacenar caracteres especiales como acentos y la ñ.
    ```
4. **Confirmar Creación**: Haz clic en `Crear`.

### 📋 Creación de la Tabla de Contactos 📋

1. **Nueva Tabla**: En la base de datos `Agenda`, crea una nueva tabla llamada `Contacto` con tres columnas.
2. **Columnas y Tipos de Datos**: Define las columnas y sus tipos de datos como sigue:

 | Columna | Tipo de Dato | Observaciones |
 | ------- | ------------ | ------------- |
 | ID      | INT          | Autoincrement |
 | Nombre  | VARCHAR(200) |               |
| Correo  | VARCHAR(200) |               |


```markdown
- **ID**: Se autoincrementa automáticamente. Actúa como un identificador único para cada contacto.
- **Nombre y Correo**: Tipo VARCHAR con una longitud máxima de 200 caracteres.
```
3. **Clave Primaria**: Establece `ID` como la clave primaria.

    ```markdown
    La clave primaria asegura que cada registro en la tabla sea único.
    ```
4. **Guardar Tabla**: Haz clic en `Guardar`.

### 📝 Inserción de Datos en la Tabla 📝

1. **Insertar Datos**: Ve a la pestaña `Insertar` y añade algunos contactos. Por ejemplo:

    ```sql
    INSERT INTO Contacto (Nombre, Correo) VALUES ('Pepe', 'pepe@pepe.com');
    INSERT INTO Contacto (Nombre, Correo) VALUES ('Jose', 'jose@jose.com');
    INSERT INTO Contacto (Nombre, Correo) VALUES ('Ana', 'ana@ana.com');
    ```

### 🔄 Modificación de la Clave Primaria 🔄

1. **Cambiar Clave Primaria**: Si deseas que `Correo` sea la clave primaria en lugar de `ID`, sigue estos pasos:
    - Elimina la columna `ID`.
    - Establece `Correo` como la nueva clave primaria.

    ```markdown
    Esto asegura que cada correo en la tabla sea único y no pueda ser nulo.
    ```

### 🎯 Objetivo Final 🎯

Ahora que tenemos una base de datos y una tabla, el próximo paso es crear un programa en Java que pueda interactuar con esta base de datos. Podremos realizar diversas operaciones como consultar, insertar, modificar y eliminar datos. Pero por ahora, nos centraremos en consultar los datos almacenados en nuestra tabla `Contacto`.

___
## 🌐 Conectar Java con MySQL en Visual Studio Code 🌐

### 📥 Descarga del Conector MySQL para Java 📥

1. **Enlace de Descarga**: Accede al sitio web oficial para descargar el conector MySQL para Java.
2. **Selección de Plataforma**: Elige la opción `Platform Independent`.
3. **Formato del Archivo**: Puedes descargar el archivo en formato `.tar` o `.zip`.
4. **Descarga**: Haz clic para descargar el archivo `.zip`.

    ```markdown
    El archivo descargado será algo como `mysql-connector-java-8.0.33.jar`.
    ```

### 🗂️ Configuración del Proyecto en Visual Studio Code 🗂️

1. **Ubicación del Archivo JAR**: Descomprime el archivo `.zip` y coloca el archivo `.jar` en la carpeta de tu proyecto. Por ejemplo, dentro de `Tema 8/Conector MySQL`.

    ```markdown
    Si estás siguiendo un curso y tienes el repositorio de GitHub actualizado, este archivo ya debería estar en la carpeta del proyecto.
    ```

2. **Configuración del Classpath**:
    - Abre Visual Studio Code.
    - Ve a `Java Projects`.
    - Haz clic en los tres puntos y selecciona `Configure Classpath`.
    - Haz clic en `Add` y navega hasta la ubicación del archivo `.jar`.
    - Selecciona el archivo y confirma.

    ```java
    // Tu proyecto ahora está configurado para usar el conector MySQL.
    ```

### 🛠️ Código para la Conexión a la Base de Datos 🛠️

1. **Información Necesaria**: Para conectarte a la base de datos, necesitas:
    - Usuario
    - Contraseña
    - URL de la base de datos

    ```java
    // Ejemplo
    String usuario = "root";
    String password = "";
    String url = "jdbc:mysql://localhost/Agenda";
    ```

2. **Conexión a la Base de Datos**: Utiliza la clase `Connection` y el método `DriverManager.getConnection()` para establecer la conexión.

    ```java
    try {
        Connection conn = DriverManager.getConnection(url, usuario, password);
        System.out.println("Se ha conectado correctamente con la base de datos");
    } catch (SQLException e) {
        e.printStackTrace();
    }
    ```

    ```markdown
    Este bloque de código intenta establecer una conexión y muestra un mensaje si la conexión es exitosa.
    ```

### 🚀 Ejecución y Verificación 🚀

1. **Ejecución del Código**: Ejecuta el código en Visual Studio Code.
2. **Verificación**: Si todo está configurado correctamente, deberías ver el mensaje "Se ha conectado correctamente con la base de datos".

    ```markdown
    Si encuentras errores, asegúrate de que:
    - El servidor MySQL está en marcha.
    - La URL, el usuario y la contraseña son correctos.
    - El archivo `.jar` está correctamente añadido al classpath.
    ```

___
%%
tags: #java  #pagacceso_a_datos  #ConceptosBásicosDeBasesDeDatos #DefiniciónDeInformación #BaseDeDatos #SistemaGestorDeBasesDeDatos #TransformaciónDeDatosEnInformación #DatosEnBruto #ProcesamientoDeDatos #ComponentesComunesEnBasesDeDatos #Tablas #Consultas #Macros #SistemasGestoresDeBasesDeDatos #ModelosDeDatosEnSGBD #GeneracionesDeModelosDeDatos #IntroducciónASQL #PanoramaGeneralDeSQL #DDL #DML #DCL #TCL #EjemploPráctico #MySQL #InstalaciónDeXAMPP #PanelDeControlDeXAMPP #ConfiguraciónInicialDeMySQL #CreaciónDeLaBaseDeDatosEnJAVA #ConectarJavaConMySQL #DescargaDelConectorMySQLParaJava #ConfiguraciónDelProyectoEnVisualStudioCode #CódigoParaLaConexiónALaBaseDeDatos #EjecuciónYVerificación
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%% 