---
ID:: 050
tags::  #sql #pagsql #vista #view 

nombre:: "Vistas (view)"
---

___
# Vistas (view)
![](https://youtu.be/md5qdEsRkXo?t=725)

___
## Introducción a las vistas o views

Una vista es una tabla "virtual" basada en el resultado de una consulta de tipo "SELECT" a una tabla.

Existen varias razones por las cuales las vistas nos pueden resultar útiles:

- Por temas de seguridad, podríamos necesitar que un grupo de usuarios tenga acceso exclusivamente a algunos datos y no otros dentro de una tabla.
- Por temas de conveniencia, nos podría interesar filtrar las columnas que queremos que un usuario vea.
- Etc,.

Crear una vista es muy similar a crear una tabla con la importante diferencia que tenemos que especificar un comando SELECT a la hora de crearla.

Como ejemplo, vamos a crear una vista en la cual queremos mostrar datos de la tabla 'humai.Customers' que trabajamos la clase anterior [[100-Ejemplo Customer_orders_Shipment|Ejemplo Customer_orders_Shipment]], con la condición de que solo vamos a mostrar los clientes cuyo nombre contenga la letra 'A'.


En este caso, vamos a crear una vista con las mismas columnas que la tabla original pero filtrando los registros o las filas.

```sql
CREATE VIEW vista_ejemplo 
AS
SELECT 
FROM humai.Customers c
WHERE c.customer_name LIKE '%a%'
```

De la misma manera podríamos crear una vista que contenga las mismas filas que la tabla original pero filtrando las columnas que queremos mostrar.

```sql
CREATE VIEW vista_ejemplo_2 
AS
SELECT c.customer_name, c.fecha_inicio
FROM humai.Customers c
```

Por último, lógicamente ésto se puede complejizar tanto como lo deseemos. Pongamos como ejemplo que algún usuario nos solicita tener una vista disponible que muestre lo siguiente:

- Solamente el nombre de los usuarios
- Que se dieron de alta el día de ayer

```sql
CREATE VIEW vista_ejemplo_3 
AS
SELECT c.customer_name, c.fecha_inicio
FROM humai.Customers c
WHERE c.fecha_inicio = current_date - 1
```

___
%%
tags:  #sql #pagsql #vista #view 

Vínculos:  [[000-Menú SQL 📃|Menú SQL]]   
%%