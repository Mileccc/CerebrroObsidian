---
ID:: 040
tags:: #sql #pagsql #subqueries #subquerys #subconsultas
nombre:: "Subconsultas (Subqueries)"
---

___
# Subconsultas (Subqueries)

![](https://youtu.be/md5qdEsRkXo?t=1120)

___
## Introducción a las subconsultas o subqueries

Como indica su nombre, una subconsulta o subquery, es una query de SQL anidada dentro de una query mayor.

Hasta el momento trabajamos con consultas o queries relativamente chicas o sencillas, pero a medida que se complejiza el trabajo nos vamos a encontrar con situaciones en las que las subqueries resultan muy útiles.

Una subquery puede estar anidada dentro de una consulta de tipo SELECT, INSERT, UPDATE o DELETE pero se utiliza -generalmente- en conjunto con la clausula WHERE dentro de una sentencia SELECT.

Veámoslo con un ejemplo para entenderlo mejor: Retomando la siguiente tabla 'humai.Orders' de la clase pasada, tenemos
```sql
CREATE TABLE IF NOT EXISTS humai.Orders (  
	order_id INT NOT NULL,  
	customer_id INT NOT NULL,  
	order_date DATE NOT NULL,  
	order_price DECIMAL(8,2),  
	PRIMARY KEY (order_id),
	FOREIGN KEY (customer_id) REFERENCES humai.Customers(customer_id)  
);
```

Ahora supongamos que tenemos que consultar esa tabla y retornar los registros donde el 'order_price' sea máximo. ¿Cómo podemos lograr esto si de antemano no sabemos cual es el precio máximo?

```sql
SELECT * 
FROM humai.Orders
WHERE order_price = (
		SELECT MAX(order_price) 
		FROM humai.Orders
	)
```

Como mencionamos antes, esto también puede utilizarse en consultas del tipo INSERT, por ejemplo.

En un nuevo ejemplo, podemos tener el siguiente caso:

- Tenemos una tabla llamada 'humai.Orders_antiguas' con el mismo esquema que 'humai.Orders'
- Queremos insertar los registros de Orders_antiguas a la nueva tabla "humai.Orders" pero solo a partir de cierta fecha. Utilizar una subconsulta aquí nos facilitaría el trabajo

```sql
INSERT INTO humai.Orders
SELECT * 
FROM humai.Orders_antiguas o
WHERE o.order_date >= '2021-01-01'
```

Y así como vimos con la introducción a las vistas, esto puede extenderse y complejizarse tanto como lo necesitemos. De todas formas, acá cabe una aclaración no menor:

- Las subqueries o subconsultas NO son la forma más eficiente en todas las circunstancias. Por lo que si vemos que estamos "abusando" o reutilizando muchas veces las mismas subconsultas, probablemente sea conveniente re-pensar nuestras queries o diagrama de datos y analizar de que manera podemos mejorarlo.

___
%%
tags: #sql #pagsql #subqueries #subquerys #subconsultas

Vínculos:  [[000-Menú SQL 📃|Menú SQL]]   
%%