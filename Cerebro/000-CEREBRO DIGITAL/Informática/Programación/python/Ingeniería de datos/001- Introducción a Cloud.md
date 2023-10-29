---
nombre: Introducción a Cloud
tags:
  - "#pagingeniería_de_datos"
  - "#python"
ID: 1
---
___
# Introducción a Cloud
___
![](https://www.youtube.com/watch?v=-aLguS2CyRo&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS)

## 1- Conceptos básicos del Cloud en la Nube, características

![[Pasted image 20230912223624.png|900]]

**Puntos clave de la arquitectura:**
   - Cliente
   - Servidor

**¿Qué es Cloud Computing?**
"El Cloud Computing o Cómputo en la nube, es una nueva tecnología que nos permite acceder mediante un sistema remoto, al software, al procesamiento de datos y al almacenamiento de archivos."

**Cloud Computing y Big Data**
"A diferencia de esquemas de servidores tradicionales, el Cloud Computing permite el tratamiento de los grandes volúmenes de información del Big Data gracias a una de sus características clave : la escalabilidad"

_Ventajas:_
    - Abaratamiento de costes
    - Inmediatez
    - Capacidad de proceso
    - Concurrencia

**El principio 5-3-2**
Este principio se compone de:
    - 5 características     
    - 3 métodos de entrega
    - 2 modelos de implementación

- _5 características_
    - Autoservicio y bajo demanda
    - Acceso amplio y ubicuo
    - Ubicación transparente y agrupación de recursos
    - Elasticidad rápida (estirarse y contraerse)
    - Servicio medido (e incluso pago por uso)

- _3 Método de Entrega_
    - Infraestructuras como servicio (IaaS)
    - Plataforma como servicio (PaaS)
    - Software como servicio (SaaS)

![[Pasted image 20230912224954.png|900]]

- _Modelos de Implementación_
    - Nube Privada
    - Nube Pública

![[Pasted image 20230912225137.png|800]]


## 1.1 - Proveedores de servicios en la nube
![](https://www.youtube.com/watch?v=3QS9U03trGM&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=3)
- ***Amazon Web Services***
![[Pasted image 20230912225612.png|200]]
"Quizás Amazon Web Services, es una de las plataformas de servicios en la nube más conocidas, proporciona una variedad de servicios de infraestructura, tales como almacenamientos, redes, bases de datos, servicios de aplicaciones, potencia de cómputo, mensajería, inteligencia artificial, servicios móviles, seguridad, identidad y conformidad, entre otros. ¿Cuál es su principal ventaja?, sin dudas la _experiencia_ en el mercado y el servicio de _atención al cliente_ que ofrece."

- ***Microsoft Azure***
![[Pasted image 20230912225735.png|250]]

Microsoft Azure, proporciona una gama de servicios en la nube, incluidos servicios vinculados con la computación, analítica, almacenamiento y redes. Los usuarios pueden elegir entre estos servicios para desarrollar y escalar nuevas aplicaciones, o ejecutar aplicaciones existentes. ¿Cuál es su principal ventaja?, la _rapidez_.

- ***Google Cloud Platform***
Google Cloud Platform, también conocida por la nomenclatura GCP, es una suite que contiene diversos servicios que funcionan en la misma infraestructura que utiliza Google de manera interna, por ejemplo con servicios como YouTube o Google Search. ¿Cuál es su principal ventaja?. la _seguridad_

___
***¿Cuál elegir?***
Resulta relevante destacar, que las distintas soluciones anteriormente mencionadas, ofrecen una serie de ventajas, similitudes y ciertas diferencias. La elección de una u otra tecnología, deberá realizarse en función de las necesidades computacionales de la organización y acompañado por la asesoría de un profesional capacitado en la temática. Quizás, una buena recomendación antes de tomar una decisión definitiva al respecto, sería tomar una prueba gratuita de cada una de las herramientas, para vivenciar de esa manera la experiencia de utilizar cada una de ellas.

***Modelos de costos en la Nube***
Los servicios en la Nube proporcionan un modelo de precios basados en "pago por uso" o "consumo".

Este modelo basado en el consumo aporta muchas ventajas, por ejemplo:

- No hay costos iniciales de infraestructura.
- No es necesario comprar ni administrar infraestructuras costosas que es posible que no se aprovechen del todo.
- Se puede pagar para obtener recursos adicionales, y solo si se necesitan y en el momento en el que se necesiten.
- Se puede dejar de pagar por los recursos que ya no se necesiten.

## 1.2- Riesgos del Cloud computing, modelos de costos y niveles de servicio.
![](https://www.youtube.com/watch?v=XV3PDPIcZ9o&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=3)
***SPOF Single Point Of Failure o Punto Simple de Fallo***
La regla básica para hacer un sistema de alta disponibilidad es la replicación de elementos (Recordando la idea de RAID, Redundant Array of Independent Disk). Con SPOF se quiere hacer referencia a cualquier elemento no replicado y que pueda estar sujeto a fallos; afectando con ello al servicio. Se debe evitar el SPOF en cualquier subsistema del sistema, ya que en caso de fallo puede peligrar el servicio de datos por culpa de un subsistema.

![[Pasted image 20230912231559.png|600]]

***Riesgos del Cómputo en la Nube***
- Perdida de gobernanza
- Dependencia
- Integración
- Incumplimiento de servicio
- Aspectos vinculados con la privacidad

***Acuerdo de Nivel de Servicio***
Un Service Level Agreement (SLA) es un contrato que describe el nivel de servicio que un cliente espera de su proveedor. Los Service Level Agreement, sirven para establecer unos indicadores que se puedan medir, para regular el servicio que un proveedor presta y así, asegurar el cumplimiento de las expectativas de los clientes.

***Gastos de capital vs Gastos operativos***
Los servicios informáticos suelen variar en función de cada proveedor. Normalmente estos servicios incluyen:
- Potencia de proceso: por ejemplo, aplicaciones web o servidores Linux.
- Almacenamiento: por ejemplo, archivos y bases de datos.
- Redes: por ejemplo, conexiones seguras entre el proveedor de nube y la empresa.

**Costos de los gastos de capital (``CapEx``):**
- Costos de servidores
- Costos de red
- Costos de almacenamiento
- Costos de copia de seguridad y archivo
- Personal técnico
- Costos de continuidad y recuperación ante desastres de la organización
- Costos de infraestructura del centro de datos

Aclaración: Los costos tipo CapEx, suelen estar relacionados con la compra de infraestructuras físicas como puede ser hardware.

**Costos de los gastos de Operaciones (``OpEx``):**
- Leasing de software y características personalizadas.
- El escalado se cobra en función del uso o la demanda, en lugar del hardware fijo o la capacidad.
- Facturación en el nivel de usuario o la organización.

Aclaración: Los costos tipo OpEx, suelen estar asociados al dinero que se invierte en servicios o productos y se facturan al instante.

___
## 1.3- Principales servicios de GCP, características y aplicación teórica
___
![](https://www.youtube.com/watch?v=Rh_43qCjOVI&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=4)
___
***Principales servicios***
![[Pasted image 20230914073007.png]]

***Creación de cuenta***
Para empezar tu viaje en la nube de Google necesitarás abrir una cuenta de Google Cloud.

Afortunadamente Google Cloud cuenta con dos herramientas para que puedas experimentar con confianza. La primera es una asignación automática de 300 dolares al momento de abrir la cuenta. L asegunda es el programa de uso gratis bajo ciertos límites de consumo de  algunos servicios durante 12 meses, puedes ver el detalle en el siguiente link:

https://console.cloud.google.com/welcome?project=inner-grove-394307

En GCP trabajamos dentro de una estructura conocida como :Proyectos

![[Pasted image 20230914074228.png|700]]


***Proyectos en GCP***
Los proyectos tienen ciertas características:

__Nombre de proyecto(alias):__
- Nombre amigable fácilmente identificable por las personas
- Puede ser editado después de su creación
- Las APIS y demás servicios no hacen referencia por nombre
- El nombre puede ser igual a otro a nivel global

Los proyectos tienen ciertas características:

**ID de proyecto(identificador Global):**
- Identificador único global del proyecto ( no puede haber dos iguales en todo el mundo)
- Se genera automáticamente pero podemos editarlo solo al momento de crearlo. No se puede modificar después de crearse.
- Es usado por nuestras APIS, recursos y servicios GCP

**Número de proyecto(Código interno):**
- Código interno generado automáticamente por Google para identificar el proyecto


***IAM (Administración de identidades y Accesos)***
Permite otorgar acceso a recursos específicos de Google Cloud. Adopta el principio de seguridad de mínimo privilegio (recomendación Google), en el que otorgas solo los permisos necesarios para acceder a recursos específicos.

Para administrar el control de acceso con la IAM, define quién (identidad) tiene qué acceso (función) a qué recurso.

![[Pasted image 20230914075434.png|400]]

**Roles permitidos**

![[Pasted image 20230914075508.png|700]]

**Roles Predefinidos**
Se utiliza cuando deseamos otorgar permisos específicamente sobre un recurso o servicio de Googel Cloud.

Por ejemplo:
- Acceso solo de viewer al storage, bogquery, entre otros.
- Storage Admin
- Compute Admin
- Network Admin


Se utiliza cuando necesitamos otorgar un set de permisos específicamente.

![[Pasted image 20230914075825.png|500]]

Aclaración: Un rol utilizado para un proyecto que tiene acceso a los recursos del ámbito de ese proyecto

## 1.4- Abordaje practico en GCP y Crear una VM
![](https://www.youtube.com/watch?v=Ydf2l3ipMNI&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=5)

- Registro como practica en GCP
- Ejemplo de Creación de una MV (Maquina virtual)

___

## 1.5- Secciones de Billing ( Facturación)
![](https://www.youtube.com/watch?v=0R13RJUoWOk&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=6)

Como trabajar con proyectos y cuestiones de billing asociadas.

___
## 1.6- Quick labs
![](https://www.youtube.com/watch?v=wrvHRxVrEko&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=7)

___
# 2- Modelo Relacional
![](https://www.youtube.com/watch?v=iViIHY6TSAU&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=8)

___
## 2.1- Modelo Relacional
Es una estructura de tablas, las cuales a su vez se relacionan con otras tablas. Su principal característica es no poseer información repetida de forma innecesaria, lo que permite adicionar más información sin llegar a afectar la otra almacenada.

![[Pasted image 20230914082010.png|600]]

![[Pasted image 20230914082037.png|700]]

### Tablas
También llamada entidad y en algunos textos relación. Es una estructura compuesta por tuplas ( filas, registros) y atributos ( campos, columnas)

![[Pasted image 20230914082235.png|600]]

### Tipos de relaciones
**Uno a Uno:** Cada registro en cada tabla solo aparece una vez

![[Pasted image 20230914082432.png]]


**Uno a muchos:** Un registro en una tabla puede tener relación con varios elementos de otra tabla.

![[Pasted image 20230914082540.png]]

**Muchos a Muchos:** Cuando uno o más registros en una tabla puede tener una relación con uno o más elementos de otra tabla.

![[Pasted image 20230914082817.png|700]]


***Claves***
- **Clave Primaria PK:** También llamada llave primaria o primary key, hace que el registro sea unívoco y obligatoriamente no nulo.
- **Clave foránea FK:** También llamada foreign key, clave secundaria o clave externa, puede ser o no una clave primaria dentro de la tabla. Su característica es que es el punto de enlace con otra tabla donde ésta, es primary key.
- **Clave índice:** Es un campo que facilita la búsqueda dentro de una tabla. Generalmente son campos primary key

___
## 2.2- Intro a SQL
___
***Sublenguajes de SQL***

![[Pasted image 20230914083433.png|800]]

- DDL
- DML
- DCL
- TCL

### 1.1-  Estructuras
Existen múltiples sentencias en SQL que podemos utilizar para manipular nuestros datos, las más importantes son:

***DML (Data Manipulation Language)***
- _Select:_ Consultar registros de una o varias tablas
- _Delete:_ Eliminar registros de una tabla
- _Insert:_ Insertar registros en una tabla
- _Update:_ Modificar registros de una tabla

Otra clausula muy utilizada es : ``Where``. Con esta sentencia podemos seleccionar qué filtro aplicar a nuestros datos.

***DDL ( Data Definition Language)***
Las sentencias más importantes son:

- _CREATE DATABASE:_ Crea una nueva base de datos
- _ALTER DATABASE:_ Modifica una base de datos
- _CREATE TABLE:_ Crea una nueva tabla
- _ALTER TABLE:_ Modifica una tabla
- _DROP TABLE:_ Elimina una tabla

***DCL (Data Control Language)***
Las sentencias más importantes son:

- _GRANT:_ Autoriza a uno o más usuarios a realizar una operación o conjunto de operaciones sobre un objeto
- _REVOKE:_ Elimina una concesión, que puede ser la concesión predeterminada

___

### 1.3- Sentencias

#### SELECT
Para consultar datos de una tabla, deberemos usar la instrucción SELECT de SQL. La declaración SELECT contiene la sintaxis para seleccionar columnas, seleccionar filas, agrupar datos, unir tablas y realizar cálculos simples.

- Sintaxis básica para recuperar datos de una tabla:
```sql
SELECT nombre_de_columna
FROM nombre_de_tabla
```


- Consultar datos de todas las columnas:
```SQL
SELECT *
FROM nombre_de_tabla
```

#### ORDER BY
Para especificar exactamente el orden de las filas en el conjunto de resultados, deberemos agregar una cláusula ORDER BY en la declaración del SELECT de la siguiente manera:

```sql
SELECT nombre_de_columna
FROM nombre_de_tabla
ORDER BY nombre_de_columna ASC
```

La cláusula ORDER BY aparece después de la cláusula FROM. En caso de que la declaración SELECT contenga una cláusula WHERE, la cláusula ORDER BY debe aparecer después de la cláusula WHERE.

Para la ordenación usaremos:
- _Ascendente (ASC)_
- _Descendente (DEC)_

Por defecto es ascendente

#### DISTINCT
Cuando consultamos nuestros datos, puede llegar a pasar que tengamos registros duplicados dentro de los resultados de la query. Para eliminar los duplicados deberemos utilizar el operador DISTINCT en la cláusula SELECT de la siguiente manera:

```sql
SELECT DISTINCT nombre_de_columna
FROM nombre_de_tabla
ORDER BY nombre_de_columna ASC
```

#### WHERE
Para seleccionar ciertas filas de una tabla, se usa la cláusula WHERE en la declaración SELECT. 

```sql
SELECT DISTINCT nombre_de_columna
FROM nombre_de_tabla
WHERE condicion
```



### 1.4- Operadores de comparación
La forma más básica de filtrar datos es utilizar operadores de comparación.

![[Pasted image 20230914085908.png|400]]


### 1.5- Operadores lógicos

![[Pasted image 20230914085952.png|1000]]


___
## 2.3- Big Query
![](https://www.youtube.com/watch?v=AYF02LpU37k&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=10)
#### Bigquery y el almacén de datos como servicio
- El almacén de datos corporativos en la nube de Google
- Escala de Petabyte y la facilidad del SQL
- Datos cifrados, Durables y Altamente disponibles
- Servicio completamente gestionado

### Tipos de datos

![[Pasted image 20230915072919.png|900]]


### Otros servicios importantes en GCP

- ***Cloud Storage:*** Servicio para almacenar y recuperar cualquier cantidad de datos en todo el mundo y en cualquier momento.
Cloud storage se puede utilizar en varias situaciones, como la entrega de contenido de un sitio web, el almacenamiento de datos con fines de archivo y recuperación ante desastres, o la distribución de grandes objetos de datos a los usuarios a través de una descarga directa.

- ***Compute Engine:*** Servicio de computación seguro y personalizable con el que podemos crear y ejecutar máquinas virtuales en la infraestructura de Google. Los nuevos clientes reciben 300 USD en crédito gratis para invertirlos en Google Cloud. Todos los clientes tienen acceso a una máquina de uso general ( instancia f1-micro) cada mes de forma gratuita (Cloud shell).

- ***Otros:*** 
    - Cloud Functions.
    - Cloud SQL
    - Data Flow

#### Buenas practicas y recomendaciones en la Nube
- **Centrarse en el Negocio:** Hay que concentrarse en la identificación de los requerimientos del negocio y su valor asociado, y usar estos esfuerzos para desarrollar relaciones sólidas con el negocio.

- **Construir una infraestructura de información adecuada:** Diseñar una base de información única, integrada, fácil de usar, de alto rendimiento donde se reflejará la amplia gama de requerimientos de negocio identificados en la empresa.

- **Capacitación del Personal:** Aplicar conceptos vinculados al mundo del Data Literacy y la alfabetización de datos.

#### Políticas de costos GCP

- **Trabajar con Cuotas:**
Google Cloud aplica cuotas sobre el uso de recursos para propietarios de proyectos, lo que establece un límite estricto en relación con qué tanto puede usar tu proyecto un recurso particular de Google Cloud. A continuación, se muestran las cuotas que limitan dos tipos de usos de recursos:

   - Cuota de tarifa, como la cantidad de solicitudes a la API por día. Esta cuota se restablece luego de un tiempo especificado, como un minuto o un día.
   - Cuota de asignación, como el número de máquinas virtuales o balanceadores de cargas que usa tu proyecto. Esta cuota no se restablece con el tiempo y debe retirarse de manera explicita cuando ya no quieras usar el recurso, por ejemplo, mediante el borrado de un cluster de GKE.

### Práctica de BigQuery en GCP

![](https://www.youtube.com/watch?v=qQoC2q-X3iI&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=11)


#### Crear primer DataSet
![](https://www.youtube.com/watch?v=dsoLfC_W8Cs&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=12)

___

#### Crear una tabla a partir de un archivo que tenemos localmente
![](https://www.youtube.com/watch?v=XqCzhVJSsHg&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=13)

___
#### Vincular el servicio de Cloud Storage de GCP con Big Query
![](https://www.youtube.com/watch?v=7DDFAp1hl_g&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=14)

___
#### Crear un conjunto de datos a partir de un archivo alojado en Google Drive
![](https://www.youtube.com/watch?v=5FAl8ZhoCg4&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=15)

___
#### Crear backet y cargar archivos en el Cloud Storage utilizando directamente el SDK de GCP.
![](https://www.youtube.com/watch?v=2adauKrc7nE&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=16)

___
#### Eliminar todos los recursos creados a lo largo de la practica para que no consuman saldo
![](https://www.youtube.com/watch?v=20tD3Hk2r78&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=17)

___
## 3- Vertex AI & Data Studio
![](https://www.youtube.com/watch?v=vJYYUz5qZK8&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=18)
___
### 3.1- Introducción
***Vertex AI***
- Es un servicio de Google Cloud Plataform que permite que equipos con distintos ``niveles de expertise`` en Machine Learning, desde novatos hasta expertos, puedan realizar las tareas principales de un proyecto de Ciencia de Datos en una plataforma ``centralizada`` e ``integrada``
- Es una plataforma ``visual`` e intuitiva para los novatos pero a la vez flexible para los expertos que la pueden acceder de forma ``programática``

### 3.2- Flujo de trabajo de ML
Luego de definir el tipo de tarea de predicción, un flujo de trabajo de un proyecto consiste a grandes rasgos en las siguientes etapas:

- **Ingestar, analizar y transformar data**
    - Fundamentalmente consiste en la preparación de datos con los managed dataset
    - Se puede importar la data usando la Consola o mediante APIs.
    - En la misma también se pueden anotar los datos, en caso de que no lo estén.

- **Crear y entrenar un modelo**
    - Puede hacerse con ``AutoML`` o entrenar ``modelos propios``.
    - ``AutoMl`` soporta datos de tipo tabulares como también imágenes, video o texto. Se encarga de la mayor parte de la escritura del código y de encontrar el mejor modelo para esa tarea.
    - Si se necesita más control sobre la arquitectura o el framework del modelo como PyTorch o TensorFlow, se puede usar los de tipo ``Custom``. En el mismo podemos nosotros escribir el código.

- **Evaluar y optimizar el modelo**
    - Para entender las señales detrás del mismo se puede utilizar ``Explainable AI`` y observar qué factores están jugando un rol en la predicción del modelo.

- **Deployarlo para hacer predicciones**
    - Los modelos se desployan a un ``endpoint`` para poder servirlo en predicciones online usando la Consola o la API.
    - Este "deployment" incluye todos los recursos físicos y el ``hardware`` necesario para poder escalar en caso de ser necesario y manteniendo baja la latencia en las predicciones online.
    - El modelo entrenado que se genera en este proceso, también llamado ``artefacto``, se puede usar para hacer predicciones batch.
    - Una vez que el modelo fue deployado se le pueden solicitar predicciones a través de la CLI, la consola, los SDKs o las APIs.

Vertex AI provee herramientas para cada uno de estos pasos, desde la gestión de los datos hasta las predicciones, de la siguiente manera.

### 3.3- Datasets
- ``Datasets`` permite que la data pueda ser accesible desde un lugar centralizado.
- Permite anotar y etiquetar datos en la Consola.
- Se puede llevar un registro del "linaje" de la data para implementar Gobierno de Datos y poder comparar métricas de los modelos entrenados con los mismos.
- Para crear un dataset debemos seleccionarlo, subirlo e importarlo en ``Datasets``
- Luego de modificarlo y transformarlo podemos usarlo para entrenar los modelos.
- Actualmente hay cuatro tipos de datos soportados: Imágenes, Data tabular, Texto y Video.
    - ***Imágenes***: 
        - **Clasificación**: Para predecir una o más etiquetas desde una imagen. Ejemplo; razas de perros entre fotos de perros.
        - **Detección de objetos**: El modelo dibuja cajas en la foto, llamadas "bounding boxes", alrededor de los ítems encontrados por el mismo. Ejemplo; identificar los diferentes vegetales en una foto de una ensalada.
        - **Segmentación**: El modelo le asigna una etiqueta a regiones de una imagen a nivel de pixel.
    - ***Data tabular***:
        - **Regresión**: En estos problemas se predice un valor numérico. Soporta cientos de columnas y millones de filas.
        - **Clasificación**: En este caso lo que se predice es una categoría.
        - **Forecasting**: El modelo predice la probabilidad de eventos repentinos o de demanda. Por ejemplo; ventas en un periodo de tiempo.
    - ***Texto***:
        - **Clasificación**: Se le asigna una o más etiquetas a cada uno de los documentos del dataset. Por ejemplo; en un caso de Soporte al Cliente, un email de inbox podría clasificarse como "Reclamo" o "Sugerencia".
        - **Extracción de entidades**: El modelo identifica porciones de texto de interés dentro de un documento. Por ejemplo; identificar todas las frases referidas a precio dentro de un mail como podría ser "muy caro" o "bueno y barato".
        - **Análisis de sentimiento:** Permite entender el sentimiento general expresado en un bloque de texto. Por ejemplo; si un cliente estuvo satisfecho o molesto con un servicio provisto.
    - ***Video***:
        - **Clasificación**: Predice etiqueta en un video entero, en una toma de video o una captura. Por ejemplo; en un video de fútbol se puede etiquetar la sección de comerciales y la sección con el partido.
        - **Reconocimiento de acción**: Identifica clips en el video donde acciones específicas ocurren. Por ejemplo; en el video del partido de fútbol, cuando ocurre un gol.
        - **Seguimiento de objetos**: Se predicen etiquetas en bounding boxes en ciertos momentos del video, con los objetos que se deseen detectar. Por ejemplo; en el mismo partido de fútbol, podemos capturar el movimiento de la pelota a lo largo del clip de video.

#### Recomendaciones a la hora de construir datasets
- Para que no haya ``training-serving`` skew, debemos asegurarnos que los datos de entrenamiento sean similares a los que los usuarios van a enviar al modelo deployado.
- Por ejemplo: Si las imágenes van a ser de baja resolución, deberíamos asegurarnos de tener imágenes borrosas con varios ángulos, fondos y resoluciones.
- Lo recomendable es proveer al menos mil datos por categoría.
- Se pueden importar a Vertex AI datasets externos para entrenar modelo, pero los managed datasets traen algunos beneficios adicionales que exploraremos en el Hands-On

### 3.4- Entrenamiento de modelos (AutoML)
Las dos grandes opciones para entrenar modelos son AutoML y Custom.

- ``AutoMl`` nos permite crear modelos de alta calidad con mínimo esfuerzo y conocimiento de ML.
    - **Casos de uso**: Si el caso de uso está soportado por la oferta de AutoML, es una buena idea empezar por ahí.
    - Si tenemos un equipo con poca experiencia en ML, lo mejor es arrancar explorando con AutoML antes de ir por modelos custom. Esto permite **bajar la barrera de entrada**.
    - Si el tamaño del **equipo es pequeño**, AutoML puede ser una buena opción.
    - AutoML también nos permite **prototipar** un primer modelo rápido que puede ser usado como baseline o prueba de concepto y hasta podría terminar convirtiéndose en el modelo productivo.
- ``Custom`` cuando necesitamos entrenar modelos personalizados en la nube utilizando contenedores preconstruidos o construidos por nosotros. 
    - **Casos de uso**: Si no, por ejemplo, si el tipo de dato es mixto (imágenes + metadata descriptiva), optar por un modelo Custom.
    - Puede ser el caso también que tengamos un **requerimiento técnico** específico con el modelo a construir, que necesitemos más control sobre la arquitectura, sobre el framework del mismo (TensorFlow o PyTorch) o los assets del modelo exportado
    - Un modelo custom requiere de **más tiempo y mantenimiento**.
    - En cambio si queremos **mejorar el baseline o la heurística existente**, puede ser una mejor elección escribir un modelo custom.

#### Entrenamiento modelo con AutoML
![](https://www.youtube.com/watch?v=f82FW703q-A&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=19)

___
#### Notebooks- Como instanciar y personalizar una notebook de Jupyter en GCP
![](https://www.youtube.com/watch?v=hwCH1qhPNfw&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=20)

___
#### Entrenamiento de modelos custom
- Antes de enviar un **custom Job** a Vertex AI debemos crear una aplicación de entrenamiento en Python o un custom conteiner para que contenga el código de entrenamiento y sus dependencias.
- Existen **contenedores preconstruidos** sobre los cuales podemos correr nuestro código si la aplicación de entrenamiento está escrita en Python. Están soportados los framework TensorFlow, XGBoost, PyTorch o Scikit-Learn.
- Para este caso debemos proveer la ruta del paquete de entrenamiento almacenado en un backet de Cloud Storage.
- Si usamos un **contenedor propio** debemos proveer la ruta del conteiner en el Conteiner Registry o en el Registro de Artefactos.
- En ambos casos necesitamos una carpeta en un backet de Cloud Storage para depositar los **artefactos de salida** del modelo.

#### Hiperparámetros
- Dentro de los training jobs se encuentra el servicio de tuning de hiperparámetros.
- Los hiperparámetros son las variables que gobiernan el proceso de entrenamiento de los modelos como el batch size o el número de capas ocultas de una red neuronal.
- Este servicio dispara "ensayos" con diferentes configuraciones de hiperparámetros en la forma de training jobs y busca la mejor combinación de los mismos entre todas las posibles.

#### Training jobs
- Para lanzar estos training jobs se necesitan recursos de cómputo, que podrían ser desde un único nodo hasta un pool de workers en entrenamiento distribuido.
- En este paso se deben seleccionar el tipo de máquina, CPU, tamaño y tipo de disco y aceleradores como GPUs o TPUs.

#### Inferencia
- Cuando el entrenamiento se termina, el modelo entrenado se deploya en un **endpoint** para ser servido en predicciones.
- Este proceso de llama **inferencia** y se puede realizar con containers preconstruidos que soportan modelos entrenados en TensorFlow, Scikit-Learn o PyTorch o con containers propios almacenados en Container Registry o en el Registro de Artefactos.
- Si solo se necesitan los artefactos binarios del modelo, se pueden descargar sin necesidad de ser deployados en un endpoint.
- Los mismos pueden ser utilizados para **predicciones batch**.

#### Practica
![](https://www.youtube.com/watch?v=MBiRUukltxM&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=21)

___
#### Lanzamiento y deploy en modelo custom
![](https://www.youtube.com/watch?v=iAVF49qUQg0&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=22)

___
### 3.5- Vertex AI - SDK:
#### Entrenamiento y deployment de un modelo mínimo viable de detección de fraude con AutoML importando un dataset de BigQuery mediante el SDK de Vertex AI
![](https://www.youtube.com/watch?v=OrvnfmZcEjw&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=23)

___
![[Pasted image 20230918072640.png|800]]
![[Pasted image 20230918072719.png|800]]
![[Pasted image 20230918072836.png|800]]

### 3.6- DataStudio
![](https://www.youtube.com/watch?v=gvV4R5WQJMI&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=24)

#### Funcionalidades
![[Pasted image 20230918073459.png|800]]

##### Principales funcionalidades

![[Pasted image 20230918073546.png|1200]]
![[Pasted image 20230918073706.png|1200]]

***Fuentes de datos***
![[Pasted image 20230918073814.png|1000]]

***Métricas y dimensiones***

![[Pasted image 20230918073927.png|1000]]
![[Pasted image 20230918074034.png|1000]]

##### Principales Gráficos
![](https://www.youtube.com/watch?v=aFzETGkD0WU&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=25)

___
![[Pasted image 20230918074210.png|1000]]

- ***Scorecards***

![[Pasted image 20230918074307.png|1000]]

- ***Time Series***

![[Pasted image 20230918074354.png|1000]]

- ***Tables***

![[Pasted image 20230918074431.png|1000]]

- ***Bar Charts***

![[Pasted image 20230918074503.png|1000]]

- ***Pie charts***

![[Pasted image 20230918074550.png|1000]]

- ***Geo charts***

![[Pasted image 20230918074632.png|1000]]

##### Controles y filtros

![](https://www.youtube.com/watch?v=Mm9rKZS1nis&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=26)

___
![[Pasted image 20230918075107.png|1000]]


- ***Date Range Control***

![[Pasted image 20230918075207.png|1000]]

- ***Time comparison***

![[Pasted image 20230918075250.png|1000]]

- ***Search bar***

![[Pasted image 20230918075327.png|1000]]


- ***Dropdown list***

![[Pasted image 20230918075406.png|1000]]

- ***Internal filters***
![[Pasted image 20230918075445.png|1000]]


___
## 4- FastApi
### 4.1- Conceptos generales de APIs y principales funcionalidades de FastAPI
![](https://www.youtube.com/watch?v=cBTkXbBeYpM&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=27)

___

![[Pasted image 20230918080326.png|1000]]
![[Pasted image 20230918080433.png|1000]]

#### APIs

![[Pasted image 20230918080552.png|1000]]

#### Acciones

![[Pasted image 20230918080744.png|1000]]

![[Pasted image 20230918080825.png|1200]]

#### FastApi

![[Pasted image 20230918080930.png|1000]]
![[Pasted image 20230918081057.png|1000]]

### 4.2- Creación de la primera API funcional
![](https://www.youtube.com/watch?v=rtPd613KHWo&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=28)

___
### 4.3- Versionado y publicación en GitHub
![](https://www.youtube.com/watch?v=hBNJ75auwow&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=29)

___
### 4.4- Deploy en App Engine
![](https://www.youtube.com/watch?v=jzA7geTNdfk&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=30)

![[Pasted image 20230918082856.png|1000]]
![[Pasted image 20230918083010.png|1000]]

### 4.5- Análisis de costos
![](https://www.youtube.com/watch?v=Sf3HGYd0dBw&list=PLon--J7mANNXFvpfJ3h7P09jByDGOVuGS&index=31)

___





















___

%%
tags: #pagingeniería_de_datos #python 

Vínculos: [[000-Menú Machine Learning 📃|Menú Machine Learning 📃]]  ,[[000-Menú Python 📃|Menú python]]
%%