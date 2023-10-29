---
ID: 175
"tags:": 
nombre: Manejo de datos faltantes
---
___
#  Manejo de Datos Faltantes  
![](https://www.youtube.com/watch?v=XiKYdHUsgyM&ab_channel=C%C3%B3digoM%C3%A1quina)
  
```python  
import pandas as pd  
  
datos = pd.read_csv("datos/clientes.csv")  
  
print(datos["nombre"])  
print(datos[ datos["nombre"].isnull() ])  
print(datos.dropna(subset=["nombre", "ingreso"], inplace=True))  
print(datos)  
print(datos.fillna(0))  
print(datos["nombre"].fillna("DESCONOCIDO"))  
  
promedio = datos["ingreso"].mean()  
mediana = datos["ingreso"].median()  
moda = datos["ingreso"].mode()[0]  
print(promedio, mediana, moda)  
print(datos["ingreso"].fillna(moda))  
```  
  
    0       Juan  
    1      Luisa  
    2        NaN  
    3     Carmen  
    4        NaN  
    5      Mario  
    6      Pedro  
    7    Gustavo  
    8     Carlos  
    Name: nombre, dtype: object  
      nombre  edad  ingreso  
    2    NaN  70.0  20000.0  
    4    NaN   NaN      NaN  
    None  
       nombre  edad  ingreso  
    0    Juan  35.0  15800.0  
    1   Luisa  25.0  17000.0  
    3  Carmen  49.0  22000.0  
    5   Mario  30.0  15800.0  
    6   Pedro   NaN  17400.0  
       nombre  edad  ingreso  
    0    Juan  35.0  15800.0  
    1   Luisa  25.0  17000.0  
    3  Carmen  49.0  22000.0  
    5   Mario  30.0  15800.0  
    6   Pedro   0.0  17400.0  
    0      Juan  
    1     Luisa  
    3    Carmen  
    5     Mario  
    6     Pedro  
    Name: nombre, dtype: object  
    17600.0 17000.0 15800.0  
    0    15800.0  
    1    17000.0  
    3    22000.0  
    5    15800.0  
    6    17400.0  
    Name: ingreso, dtype: float64

___






















___
%%
tags: #programación #paganálisis_de_datos #python  #análisis_de_datos

Vínculos:   [[000-Menú Análisis de datos 📃|Menú Análisis de datos 📃]] 
%%