---
ID:: 060
tags::  #pagprogramacion #sql #pagsql #join #inner #full #left #right 
nombre:: "Joins"
---

___
# Joins  
![](https://youtu.be/md5qdEsRkXo?t=1462)

___
## Introducción a los Joins

Los "joins" son una de las partes más importantes del lenguaje SQL. En términos sencillos nos permiten unir y cruzar datos entre tablas (o incluso cruzar una tabla consigo misma)

En la última parte de la clase anterior vimos un caso donde queríamos seleccionar un "Total Gastado" que se obtenía de la tabla 'humai.Orders' y traer además el nombre de quien había gastado ese monto - dato que existía en la tabla 'humai.Customers'.

Para este tipo de situaciones y muchas otras que se encuentran en el día a día trabajando con bases de datos, los joins son la herramienta principal.

En éste sentido, existen 4 tipos de joins:

- **(INNER) JOIN:** Devuelve los registros que existan en _ambas tablas exclusivamente_.
    - En el ejemplo de la clase pasada donde queríamos "unir" datos de las tablas 'Orders' y 'Customers', éste join nos retornaría exclusivamente registros en donde un 'Customer' tiene una 'Order' y viceversa.
```sql
SELECT *
FROM humai.Orders o
INNER JOIN humai.Customers c
ON o.customer_id = c.customer_id -- Solo retornará registros donde exista la coincidencia o.customer_id = c.customer_id 
```

- **LEFT (OUTER) JOIN:** Devuelve todos los registros de la tabla que esté 'a _la izquierda' del join_ y además aquellos que coincidan con la tabla 'a la derecha'.
    - Continuando con el ejemplo anterior

```sql
SELECT *
FROM humai.Orders o
LEFT JOIN humai.Customers c
ON o.customer_id = c.customer_id 
-- Retornará TODOS los registros de humai.Orders 
-- y además aquellos de humai.Customers donde exista la coincidencia o.customer_id = c.customer_id 
```

- **RIGHT (OUTER) JOIN:** Es la versión "complementaria" al LEFT JOIN  
      
- **FULL (OUTER) JOIN:** Devuelve todos los registros de ambas tablas, uniendo aquellos en los que haya coincidencia.

![[Pasted image 20230818075152.png|1200]]

___
%%
tags: #pagprogramacion #sql #pagsql #join #inner #full #left #right 

Vínculos:  [[000-Menú SQL 📃|Menú SQL]]   
%%