---
ID:: 100
tags::  #sql #pagsql #sentencias #select #full_join #avg #like #cast
nombre:: "Ejemplo Customer_orders_Shipment"
---

___
# Customer_orders_Shipment

![](https://youtu.be/IBLKYX4sgLY?t=3532)
___
## Modelado

![[Pasted image 20230815223733.png|800]]

___
## Preparación conexión a postgres psql desde Google colab

```sql
# install
!apt install postgresql postgresql-contrib &>log
!service postgresql start
!sudo -u postgres psql -c "CREATE USER root WITH SUPERUSER"
# set connection
%load_ext sql

import sqlalchemy
import pandas as pd
  
engine = sqlalchemy.create_engine('postgresql+psycopg2://@/postgres')
  
def exec_sql(query):
  text_query = sqlalchemy.sql.text(query)

  
  with engine.connect() as conn:
    res = conn.execute(text_query)
    if query.strip().lower().startswith('select'):
      return pd.DataFrame(res)
    else:

      conn.commit()
```

## Crear base de datos
```MySQL
create_schema = 'CREATE SCHEMA IF NOT EXISTS humai'
exec_sql(create_schema)
```

## DDL - Crear tablas

### Tabla Customers
```sql
create_customers = """
CREATE TABLE IF NOT EXISTS humai.Customers (
  customer_id INT NOT NULL,
  customer_name VARCHAR(50) NOT NULL,
  fecha_inicio DATE NOT NULL,
  fecha_fin DATE,
  PRIMARY KEY (customer_id));
"""

exec_sql(create_customers)
```

### Tabla Orders
```sql
create_orders = """
CREATE TABLE IF NOT EXISTS humai.Orders (
  order_id INT NOT NULL,
  customer_id INT NOT NULL,
  order_date DATE NOT NULL,
  order_price DECIMAL(8,2),
  PRIMARY KEY (order_id),
  FOREIGN KEY (customer_id) REFERENCES humai.Customers(customer_id)
);
"""

exec_sql(create_orders)
```

### Tabla Shipments
```sql
create_shipments = """
CREATE TABLE IF NOT EXISTS humai.Shipments (
  shipment_id INT NOT NULL,
  order_id INT NOT NULL,
  shipment_date DATE NOT NULL,
  shipment_city VARCHAR(50),
  PRIMARY KEY (shipment_id),
  FOREIGN KEY (order_id) REFERENCES humai.Orders(order_id)
);
"""

exec_sql(create_shipments)
```

#### Check que se hayan creado las tablas
```sql
exec_sql("SELECT * FROM information_schema.tables WHERE table_schema = 'humai';")
```
![[Pasted image 20230815233157.png]]


## DML - Insertar datos ficticios
```sql
insert_customers = """
INSERT INTO humai.Customers VALUES
  (1, 'Eugenio', '08/21/1998', Null),
  (2, 'Mario', '05/05/2005', Null),
  (3, 'Pedro', '03/08/2020', '02/05/2022')
"""

exec_sql(insert_customers)
```

```sql
insert_orders = """
INSERT INTO humai.Orders VALUES
  (1, 1, '06/05/2022', 45),
  (2, 1, '06/05/2021', 60),
  (3, 1, '06/06/2022', 70),
  (4, 2, '01/05/2022', 5),
  (5, 3, '06/10/2022', 145),
  (6, 3, '03/02/2022', 2);
"""

exec_sql(insert_orders)
```

```sql
insert_shipments = """
INSERT INTO humai.Shipments VALUES
  (1, 1, '06/06/2022', 'Belgrano'),
  (2, 2, '06/06/2021', 'Mar del Plata'),
  (3, 3, '06/10/2022', 'Belgrano'),
  (4, 4, '02/05/2022', 'San Isidro'),
  (5, 5, '06/15/2022', 'Belgrano'),
  (6, 6, '03/05/2022', 'Mar del Plata');
"""

exec_sql(insert_shipments)
```


## DDL - Consultas SELECT
1. Retorna todos los registros de la tabla Customers.
```sql
select_customers = 'SELECT * FROM humai.Customers;'

exec_sql(select_customers)
```
![[Pasted image 20230815233513.png]]

2. Retorna la cantidad de envíos por shipment_city
```sql
select_shipment = 'SELECT shipment_city as "Barrio", count(*) as "Envios" FROM humai.Shipments  GROUP BY shipment_city'

exec_sql(select_shipment)
```
![[Pasted image 20230815233656.png]]

3. Retorna la cantidad de envíos a Belgrano
```sql
exec_sql("SELECT count(*) as \"Envios a Belgrano\" FROM humai.Shipments  WHERE shipment_city = 'Belgrano';")
```
![[Pasted image 20230815233705.png]]

4. Retorna todas las ordenes mayores a $50
```sql
exec_sql("SELECT * FROM humai.Orders WHERE order_price > 50;")
```
![[Pasted image 20230815233753.png]]

5. Retorna el cliente que más dinero gasto
```sql
exec_sql("SELECT customer_id, sum(order_price) as \"Total gastado\" FROM humai.Orders GROUP BY customer_id ORDER BY sum(order_price) DESC LIMIT 1;")
```
![[Pasted image 20230815233830.png]]


6. Y que si queremos ver el nombre del cliente? Dato que se encuentra en otra tabla.
```sql
select = """
SELECT c.customer_name, sum(order_price) as \"Total gastado\"
  FROM humai.Orders o
  FULL JOIN humai.Customers c
  ON o.customer_id = c.customer_id
  GROUP BY c.customer_name
  ORDER BY sum(order_price) DESC
  LIMIT 1;
"""

exec_sql(select)
```
![[Pasted image 20230815233931.png]]


7. Retornar la duración promedio de los clientes que se dieron de baja.
```sql
exec_sql("SELECT CAST(AVG(fecha_fin-fecha_inicio) AS INT) AS \"Promedio Total dias\" FROM humai.Customers WHERE fecha_fin IS NOT NULL")
```
![[Pasted image 20230815234015.png]]


8. Retornar los clientes que tienen una 'e' en el nombre.
```sql
exec_sql("SELECT customer_name FROM humai.Customers WHERE customer_name LIKE '%e%';")
```
![[Pasted image 20230815234046.png]]

___
%%
tags: #sql #pagsql #sentencias #select #full_join #avg #like #cast

Vínculos:  [[000-Menú SQL 📃|Menú SQL 📃]]   , [[030-Anatomía del comando SELECT||Anatomía del comando SELECT]]
%%