---
ID:: 110
tags::  #pagprogramacion #sql #pagsql 
nombre:: "Prácticas"
---

___
# Prácticas
___


![](https://youtu.be/md5qdEsRkXo?t=2623)

___

## Set Up

Conectamos a postgresql como root y creamos una base de datos

```sql
# install
!apt install postgresql postgresql-contrib &>log
!service postgresql start
!sudo -u postgres psql -c "CREATE USER root WITH SUPERUSER"
# set connection
%load_ext sql
%Config SqlMagic.feedback = False
%Config SqlMagic.autopandas=True
%sql postgresql + psycopg2://@/postgres
%sql CREATE SCHEMA IF NOT EXISTS humai
```
$$Consola$$
![[Pasted image 20230821075117.png]]


Importamos las librerías y los datos

```sql
# extra dependencies
import pandas as pd
import sqlalchemy

engine = sqlalchemy.create_engine("postgresql+psycopg2://@/postgres")
conn = engine.connect()



conn.execute(sqlalchemy.text('CREATE SCHEMA IF NOT EXISTS humai'))
conn.commit()

akas = pd.read_csv("https://drive.google.com/uc?id=1MDgiAel34RZULi9a1WXuzGQOE9M5_aGp",nrows=200000,sep="\t")
akas.columns = [i.lower() for i in akas.columns]
crew = pd.read_csv("https://drive.google.com/uc?id=1vzlcrhm77MFw7ha_Xj3MyfPwhM7XhqW2",nrows=200000,sep="\t")
crew.columns = [i.lower() for i in crew.columns]
names = pd.read_csv("https://drive.google.com/uc?id=1Co0bwQQhmtMcTnZwZqWo_W1-nrFVgBFm",nrows=200000,sep="\t")
names.columns = [i.lower() for i in names.columns]
principals = pd.read_csv("https://drive.google.com/uc?id=1ojsyx3m-8-3x9LM_X_TS0EBN4JMrkyR4",nrows=200000,sep="\t")
principals.columns = [i.lower() for i in principals.columns]
ratings = pd.read_csv("https://drive.google.com/uc?id=1XCN67VhsVQmlr5BudNJGjHnqZR_DqetR",nrows=200000,sep="\t")
ratings.columns = [i.lower() for i in ratings.columns]
ratings.to_sql("ratings",engine,if_exists="append",method="multi",schema="humai",index=False)

del(ratings)
akas.to_sql("akas",engine,if_exists="append",method="multi",schema="humai",index=False)
del(akas)
crew.to_sql("crew",engine,if_exists="append",method="multi",schema="humai",index=False)
del(crew)
names.to_sql("names",engine,if_exists="append",method="multi",schema="humai",index=False)
del(names)
principals.to_sql("principals",engine,if_exists="append",method="multi",schema="humai",index=False)
del(principals)
conn.commit()
conn.close()

def exec_sql(query):
  text_query = sqlalchemy.sql.text(query)

  with engine.connect() as conn:
    res = conn.execute(text_query)
    if query.strip().lower().startswith('select'):
      return pd.DataFrame(res)
    else:
      conn.commit()
```
$$Consola$$

## Modelo de datos

Para la parte de ejercitación creamos una base un tanto más cercana a lo que sería una base real.

Tenemos 5 tablas, cada una con cientos de miles de registros y vamos a poner en práctica todos los conceptos que estuvimos viendo hasta el momento.

---

![modelo](https://drive.google.com/uc?id=1xXfeu5ZlbEDrK_vo-vbsZ5Jv1TROgrsr)

---

### 1) Subquery iniciales
Empezamos utilizando un conjunto de subqueries para devolver con un único comando SELECT la cantidad de filas en cada una de las tablas que tenemos para ir familiarizándonos con nuestros datos.

```sql
select = """
SELECT (SELECT COUNT(*) FROM humai.akas) as "Count AKAs",
  (SELECT COUNT(*) FROM humai.ratings) as "Count Ratings",
  (SELECT COUNT(*) FROM humai.names) as "Count Names",
  (SELECT COUNT(*) FROM humai.principals) as "Count Principals",
  (SELECT COUNT(*) FROM humai.crew) as "Count Crew"
"""

exec_sql(select)
```
$$Consola$$
![[Pasted image 20230821080055.png]]

### 2)Obtener rating

Supongamos ahora el siguiente caso:
Nos solicitan retornar aquellas películas que tengan un rating superior al rating promedio.
Nuevamente, podemos obtener esto  usando un subquery


```sql
exec_sql("SELECT * FROM humai.ratings WHERE averagerating > (SELECT AVG(averagerating) FROM humai.ratings)")
```
$$Consola$$
![[Pasted image 20230821080236.png]]

### 3)Traer títulos y regiones

Continuando con el ejercicio anterior, ahora nos solicitan que traigamos también los títulos y regiones de dichas películas. Como ya vimos en la clase anterior, podemos obtener esto fácilmente utilizando un JOIN. ¿Pero que tipo de JOIN?

Resumamos lo que necesitamos:

- Traer las películas, cuyo rating es superior al promedio - 'humai.ratings'
- Agregarle información de la tabla 'humai.akas' en caso exista.
- Sabemos además que, por fuera del titulo, no precisaríamos más datos de la tabla 'humai.akas'

A priori pareciera ser que un LEFT JOIN cumpliría con todos los requisitos.

Probemos lo siguiente:



```sql
select = """
SELECT r.tconst "R_Title_ID",
       r.averagerating "R_Rating",
       r.numvotes "R_Numero_de_votos",
       a.title "A_Titulo",
       a.region "A_Region"
FROM humai.ratings r
LEFT JOIN humai.akas a
ON r.tconst = a.titleid
WHERE r.averagerating > (SELECT AVG(averagerating) FROM humai.ratings)
"""

exec_sql(select)
```
$$Consola$$

![[Pasted image 20230821080500.png]]


### 3)LEFT JOIN

¿Qué sucede si nos confundimos el tipo de JOIN?

La realidad es que no pasa nada, simplemente no obtendremos el resultado que queremos ya sea porque filtramos datos de más - o de menos - pero no es que el motor vaya a arrojar ningún error. Por esto es muy importante que revisemos y analicemos si los resultados obtenidos son consistentes con lo que necesitamos.

Como ejemplo, ejecutemos la misma query del ejercicio anterior cambiando el LEFT JOIN por otro tipo de JOIN y veamos cual es el resultado.

```sql
select = ""
SELECT r.tconst "R_Title_ID",
       r.averagerating "R_Rating",
       r.numvotes "R_Numero_de_votos",
       a.title "A_Titulo",
       a.region "A_Region"
FROM humai.ratings r
INNER JOIN humai.akas a
ON r.tconst = a.titleid
WHERE r.averagerating > (SELECT AVG(averagerating) FROM humai.ratings)
"""

exec_sql(select)
```
$$Consola$$
![[Pasted image 20230821080608.png]]

### 4)Vista

Inmediatamente después, nos comentan que ésta data la necesitarían disponible por separado y que, idealmente, el usuario final no se deba preocupar por escribir correctamente los JOINS, las subqueries ni nada por el estilo.

Podemos crear una vista para hacerlo!

```sql
select = """
CREATE OR REPLACE VIEW pelis_buenas_con_titulo AS
SELECT *
FROM humai.ratings r
LEFT JOIN humai.akas a
ON r.tconst = a.titleid
WHERE r.averagerating > (SELECT AVG(averagerating) FROM humai.ratings)
"""

exec_sql(select)
```


```sql
exec_sql("SELECT * FROM pelis_buenas_con_titulo")
```
$$Consola$$
![[Pasted image 20230821080820.png]]



### 5)Consultar vista

Como comentamos en la clase teórica, ahora nuestra vista existe como "una tabla virtual" a la que podemos consultar de la misma manera que lo haríamos con una tabla real.

Por ejemplo:

```sql
exec_sql("SELECT COUNT(*) FROM pelis_buenas_con_titulo")
```
$$Consola$$
![[Pasted image 20230821080933.png]]


```sql
exec_sql("SELECT MAX(numvotes) FROM pelis_buenas_con_titulo")
```
$$Consola$$
![[Pasted image 20230821080940.png]]



### 6)Consulta mas avanzada

Probemos algo un tanto más complejo.

Supongamos que nos solicitan lo siguiente:

- El titulo de la pelicula
- Con el numero de votos máximo
- Con las condiciones de:
    - Que haya un actor con "John" en su nombre
    - Y cuyo actor tenga menos de 75 años

Para poder cumplir con esto vamos a tener que conocer bien en detalle nuestro modelo de datos - es decir las tablas y los datos que viven en ellas.


```sql
select = """
SELECT a.title, CAST(r.numvotes AS INTEGER)
FROM humai.names n
LEFT JOIN humai.principals p
ON n.nconst = p.nconst

LEFT JOIN humai.ratings r
ON p.tconst = r.tconst

LEFT JOIN humai.akas a
ON p.tconst = a.titleid

WHERE n.birthyear NOT LIKE '%N%'
AND CAST(date_part('year', NOW()) AS INTEGER) - CAST(n.birthyear AS INTEGER) < 75
AND n.primaryname LIKE '%John%'
AND r.numvotes IS NOT NULL

ORDER BY 2 DESC
LIMIT 1;
"""

exec_sql(select)
```
$$Consola$$
![[Pasted image 20230821081141.png]]

___
%%
tags: #pagprogramacion #sql #pagsql #set_up #modelo_de_datos #subquery #join #left_join #vista #exec_sql #ejecutar_query #cast

Vínculos:  [[000-Menú SQL 📃|Menú SQL]]   
%%