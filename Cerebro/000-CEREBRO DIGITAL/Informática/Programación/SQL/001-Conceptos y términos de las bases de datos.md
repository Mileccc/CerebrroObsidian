---
ID:: 001
tags::   #sql #pagsql #relación #modelo_lógico #modelo_físico #tipos_de_datos #acid #tipos_de_bases_de_datos #relacionales #norelacionales 
nombre:: "Conceptos y términos de las bases de datos"
---
___

# Conceptos y términos de las bases de datos:

![](https://www.youtube.com/watch?v=IBLKYX4sgLY&list=PLon--J7mANNWO0vWBQVOxK99CL_m9mQr_)

## Tipos de bases de datos:


#### Centralizadas
- Biblioteca central en una universal.
- La base de datos esta en un único nodo
#### Distribuidas
- Hadoop
- Big data
- Distribuido en varios servidores
#### Hierarchical
- Relación padre-hijo entre los datos
#### Object
- Datos representados y almacenados como objetos
#### Cloud
- Entorno virtual. GCP, AWS, AZURE
#### Network
- Nodos conectados por aristas. Grafos

#### Relacionales
- Ordenan los datos en forma de tablas, columnas y filas
##### Ventajas
- Los datos se estructuran fácilmente en categorías
- Los datos son consistentes en cuanto a su entrada y significado, y son fáciles de navegar
- Se pueden definir fácilmente las relaciones entre los puntos de datos
#### No-Relacionales
- Esquema de datos no claramente definido
##### Ventajas
- Los datos no se limitan a un grupo estructurado
- Se pueden realizar funciones que permiten una mayor flexibilidad
- Sus datos y análisis pueden ser más dinámicos y permitir más variantes de entrada

#tipos_de_bases_de_datos
## ACID
1)  _Atomicidad_
- Requiere que la transacción se ejecute correctamente como un todo o , si una parte de la transacción falla , que toda ella quede invalidada.
2) _Consistencia_
- Exige que los datos escritos en la base de datos como parte de la transacción cumplan todas las reglas definidas, así como las restricciones, incluidos los desencadenadores, las limitaciones y las cascadas
3) _Aislamiento_
- Es fundamental para lograr el control de concurrencia y asegurarse de que cada transacción sea independiente por sí misma.
4) _Durabilidad_
- Requiere que todos los cambios realizados en la base de datos sean permanentes luego de que la transacción se haya completado de forma correcta.

#acid
## Desafíos de las bases de datos
- Absorción de aumentos significativos en el volumen de datos
- Garantía de seguridad de los datos
- Mantenimiento al día con la demanda
- Gestión y mantenimiento de la base de datos y la infraestructura
- Eliminación de los límites de la escalabilidad

## Tipos de datos en una base de datos relacional

|Tipo de Dato|Descripción|Tamaño Máximo|Almacenamiento|
|---|---|---|---|
|CHAR|Cadena de caracteres de longitud fija|1 - 8,000 bytes|Tamaño especificado|
|VARCHAR|Cadena de caracteres de longitud variable|1 - 8,000 bytes|Longitud de dato + 2 bytes|
|TEXT|Cadena de texto larga|2^31 - 1 bytes (~2 GB)|Longitud de dato + 4 bytes|
|NCHAR|Cadena de caracteres Unicode de longitud fija|1 - 4,000 bytes|Tamaño especificado x 2|
|NVARCHAR|Cadena de caracteres Unicode de longitud variable|1 - 4,000 bytes|Longitud de dato |
|NTEXT|Cadena de texto larga Unicode|2^30 - 1 bytes (~1 GB)|Longitud de dato |
|BINARY|Datos binarios de longitud fija|1 - 8,000 bytes|Tamaño especificado|
|VARBINARY|Datos binarios de longitud variable|1 - 8,000 bytes|Longitud de dato |
|IMAGE|Datos binarios largos|2^31 - 1 bytes (~2 GB)|Longitud de dato |

|Tipo de Dato|Descripción|Rango de Valores|Almacenamiento|
|---|---|---|---|
|BIT|Valor booleano, generalmente 0 o 1|0 o 1|1 bit|
|TINYINT|Entero pequeño sin signo|0 a 255|1 byte|
|SMALLINT|Entero pequeño con signo|-32,768 a 32,767|2 bytes|
|INT|Entero con signo|-2,147,483,648 a 2,147,483,647|4 bytes|
|BIGINT|Entero grande con signo|-9,223,372,036,854,775,808 a 9,223,372,036,854,775,807|8 bytes|
|DECIMAL|Valor decimal fijo|Depende de la precisión|Variable|
|NUMERIC|Valor decimal fijo|Depende de la precisión|Variable|


|Tipo de Dato|Descripción|Características|Almacenamiento|
|---|---|---|---|
|DATETIME|Fecha y hora con precisión de 3.33 milisegundos|1753-9999|8 bytes|
|DATETIME2|Fecha y hora con alta precisión (100 nanosegundos)|0001-9999|6-8 bytes|
|SMALLDATETIME|Fecha y hora con precisión de un minuto|1900-2079|4 bytes|
|DATE|Solo fecha|0001-9999|3 bytes|
|TIME|Solo hora|00:00:00.0000000 to 23:59:59.9999999|3-5 bytes|
|DATETIMEOFFSET|Fecha y hora con desplazamiento de zona horaria|0001-9999|10 bytes|
|TIMESTAMP|Un valor único y cambiante generado automáticamente|Generado automáticamente|8 bytes|

#tipos_de_datos


## Diseño y creación de una base de datos
1) Determine el propósito de su base de datos
2) Buscar y organizar la información necesaria
3) Divida la información en tablas
4) Convierta los elementos de información en columnas 
5) Especifique las claves primarias
6) Establezca las relaciones de las tablas
7) Perfecciones su diseño
8) Aplique las reglas de normalización

![[Pasted image 20230811080837.png|400]]


#### Modelo lógico
![[Pasted image 20230811080923.png|600]]
#### Modelo físico

![[Pasted image 20230811081037.png|700]]


#modelo_lógico #modelo_físico

## Partes de una tabla
- **Entidad**: Cualquier cosa sobre la que se mantiene información
- **Atributo**: Una propiedad de una entidad
- **Instancia**: Una ocurrencia simple de una entidad

![[Pasted image 20230811081424.png|400]]

- **Relación**: Es un vínculo que nos permite definir una dependencia entre varias entidades, es decir , nos permite exigir que varias entidades compartan ciertos atributos de forma indispensable.
![[Pasted image 20230811081633.png|500]]

#relación
- **Cardinalidad**: Define el número de instancias de una entidad que se pueden relacionar con un número de instancias de otra entidad.
  - Uno a uno
  - Uno a muchos
  - Muchos a muchos
- **Modalidad**: Indica si una instancia debe participar en la relación. Es decir, si la relación es obligatoria u opcional.

- _**Claves:**_
   - **Clave primaria:** Valores únicos en una tabla que identifican un registro específico
   - **Clave foránea:** Registros en una tabla separada que se usan para hacer una conexión con las claves primarias 


## Base de datos analítica

![[Pasted image 20230814074028.png|800]]
![[Pasted image 20230814074406.png|1000]]






___
%%
tags: #sql #pagsql #relación #modelo_lógico #modelo_físico #tipos_de_datos #acid #tipos_de_bases_de_datos #relacionales #norelacionales 

Vínculos:  [[000-Menú SQL 📃|Menú SQL]]   
%%