---
ID:: 020
tags::  #programación #paganálisis_de_datos #python #análisis_de_datos #index_col #indice #exportación #importación #exportar #importar
nombre:: "Pandas_ Importando y Exportando DataFrames"
---
___
# Pandas_ Importando y Exportando DataFrames
![](https://www.youtube.com/watch?v=rrAuN0god_g&list=PL5C9QKu8AsmUK_7AEP0hSmt-8vcE8gnIB&index=4)

___
## Importación de DataFrames:

1. **Desde archivos CSV:** Puedes importar datos desde archivos CSV utilizando `pd.read_csv('archivo.csv')`. Pandas leerá el archivo y creará un DataFrame.
```python
import_df = pd.read_csv("data.csv", index_col=0) 
#Index_col se utiliza para especificar cuál columna del archivo CSV debe utilizarse como índice para el DataFrame resultante.

import_df
```
$$Consola$$
![[Pasted image 20230820192124.png]]
    
2. **Desde archivos Excel:** Pandas también puede importar datos desde archivos Excel mediante `pd.read_excel('archivo.xlsx')`. Puedes especificar la hoja que deseas leer y otras opciones.
    
3. **Desde bases de datos:** Utiliza `pd.read_sql_query()` o `pd.read_sql_table()` para importar datos desde bases de datos SQL, como SQLite o MySQL.
    
4. **Desde otros formatos:** Pandas admite la importación desde otros formatos, como JSON, HTML, y más, utilizando funciones como `pd.read_json()`, `pd.read_html()`, etc.

___

## Exportación de DataFrames:

1. **A archivos CSV:** Puedes exportar un DataFrame a un archivo CSV mediante `data.to_csv('archivo.csv', index=False)`. Puedes personalizar opciones como el delimitador y el formato.
```python
df.to_csv("data.csv")
```
$$Explorador$$
![[Pasted image 20230820192249.png]]

2. **A archivos Excel:** Para exportar a un archivo Excel, utiliza `data.to_excel('archivo.xlsx', sheet_name='Hoja1', index=False)`. Puedes especificar la hoja y otras opciones.
    
3. **A bases de datos:** Usa `data.to_sql('nombre_tabla', con=conexion)` para exportar un DataFrame a una tabla en una base de datos.
    
4. **A otros formatos:** Pandas también permite exportar a otros formatos, como JSON, HTML, LaTeX y más, utilizando funciones específicas como `data.to_json()`, `data.to_html()`, etc.

___
# Leer y guardar archivos EXCEL, CSV, HTML y TXT Python Pandas
![](https://www.youtube.com/watch?v=FeDy31JKVbc&list=PLAKj9P7fPCGGmDF9C8Hu670HfCO9t7_gj&index=3)



___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos #index_col #indice #exportación #importación #exportar #importar

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%