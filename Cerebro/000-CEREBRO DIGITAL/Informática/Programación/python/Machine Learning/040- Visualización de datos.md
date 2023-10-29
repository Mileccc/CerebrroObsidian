---
ID: " 040"
tags: "#pagmachine_learning #python"
nombre: Visualización de datos
---
___
# Visualización de datos
___

## 1- Gráficas con MatPlotLib  

![](https://www.youtube.com/watch?v=foLHkB6W_Ww&ab_channel=C%C3%B3digoM%C3%A1quina)
___

![[Pasted image 20230928074805.png|1000]]
___
### Creación de Gráficas de Líneas (plot)  
  
  
```python  
import matplotlib.pyplot as plt  
  
eje_x = ["a","b","c","d","e"]  
datos1 = [10, 20, 30, 40, 50]  
datos2 = [20, 30, 40, 50, 60]  
  
plt.plot(eje_x, datos1)  
plt.show()  
  
plt.plot(eje_x, datos2)  
plt.show()  
```  
  
  
     
![png|700](output_1_0.png)  
     
     
![png|700](output_1_1.png)  
     
  
  
### Generar Datos a Graficar  
#### Examen de Certificación para Estudiantes de 5 niveles  
  
  
```python  
import numpy as np  
  
años = ["2011", "2012", "2013", "2014", "2015",  
        "2016", "2017", "2018", "2019", "2020"]  
  
nivel1 = np.random.rand(10)*100  
nivel2 = np.random.rand(10)*200 + 100  
nivel3 = np.random.rand(10)*300 + 200  
nivel4 = np.random.rand(10)*400 + 300  
nivel5 = np.random.rand(10)*500 + 400  
```  
  
### Personalización de Gráficas
```python  
# Introducir series de datos con color, marcador, etiqueta y estilo  
  
plt.plot(años, nivel1, label="Nivel 1", color="purple", marker="<", linestyle="-")  
plt.plot(años, nivel2, label="Nivel 2", color="red", marker="*", linestyle="--")  
plt.plot(años, nivel3, label="Nivel 3", color="blue", marker="^", linestyle=":")  
plt.plot(años, nivel4, label="Nivel 4", color="black", marker=".", linestyle="-.")  
plt.plot(años, nivel5, label="Nivel 5", color="green", marker="+", linestyle=" ")  
  
# Activar leyendas  
plt.legend()  
  
# Título de Gráfica  
plt.title("Examen de Certificación")  
  
# Etiquetas de los ejes  
plt.xlabel("Años que se ha realizado el examen")  
plt.ylabel("Puntaje")  
  
# Personalizar Eje de Puntaje de 0 a 1000 en incrementos de 50  
  
plt.yticks(np.arange(0, 1001, 50))  
  
# Activar cuadrícula  
  
plt.grid()  
  
# Activar marcas menores  
plt.minorticks_on()  
  
plt.show()  
  
```  
  
  
     
![png|700](output_5_0.png)


### Gráfica de Barras Verticales (bar)  
  
  
```python  
eje_x = np.arange(0, 10)  
  
plt.bar(eje_x, nivel5, width=1/5)  
plt.bar(eje_x+0.2, nivel4, width=1/5)  
plt.bar(eje_x+0.4, nivel3, width=1/5)  
plt.bar(eje_x+0.6, nivel2, width=1/5)  
plt.bar(eje_x+0.8, nivel1, width=1/5)
plt.show()  
```  
  
  
     
![png|700](output_7_0.png)  
     
  
  
### Gráfica de Barras Horizontales (barh)  
  
  
```python  
plt.barh(eje_x+0.8, nivel5, height = 1/5)  
plt.barh(eje_x+0.6, nivel4, height = 1/5)  
plt.barh(eje_x+0.4, nivel3, height = 1/5)  
plt.barh(eje_x+0.2, nivel2, height = 1/5)  
plt.barh(eje_x,     nivel1, height = 1/5)  
  
plt.show()  
```  
  
  
     
![png|700](output_9_0.png)  
     
  
  
### Gráfica de Barras Verticales Apiladas  
  
  
```python  
  
plt.bar(eje_x, nivel5)  
plt.bar(eje_x, nivel4, bottom=nivel5)  
plt.bar(eje_x, nivel3, bottom=nivel4+nivel5)  
plt.bar(eje_x, nivel2, bottom=nivel3+nivel4+nivel5)  
plt.bar(eje_x, nivel1, bottom=nivel2+nivel3+nivel4+nivel5)  
  
plt.show()  
```  
  
  
     
![png|700](output_11_0.png)  
     
  
  
### Gráfica de Dispersión (scatter)  
  
  
```python  
plt.scatter(eje_x, nivel1, marker="*")  
plt.scatter(eje_x, nivel2)  
plt.scatter(eje_x, nivel3)  
plt.scatter(eje_x, nivel4)  
plt.scatter(eje_x, nivel5)
plt.show()  
```  
  
  
     
![png|700](output_13_0.png)  
     
  
  
### Gráfica de Pie  
  
  
```python  
plt.pie(nivel1,  
        labels=["México","Colombia", "España", "Estados Unidos", "Ecuador",  
                "Argentina", "Venezuela", "Puerto Rico", "Honduras", "Uruguay"])  
  
plt.show()  
```  
  
  
     
![png|700](output_15_0.png)  
     
  
  
### Combinar Gráficas  
  
  
```python  
plt.bar(eje_x,     nivel1,  width = 1/5)  
plt.bar(eje_x+0.2, nivel2,  width = 1/5)  
  
plt.plot(años, nivel3)  
  
plt.scatter(eje_x, nivel4)  
plt.scatter(eje_x, nivel5)  
  
plt.show()  
```  
  
  
     
![png|700](output_17_0.png)

___
## 2- Distribución de Datos e Histogramas  
  
  
  
```python  
import matplotlib.pyplot as plt  
  
datos = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]  
plt.hist(datos, bins=5, color="pink", ec="black")  
  
plt.show()  
```  
  
  
     
  ![[output_1_0 4.png|700]]
     
  
  
### Generar arreglos con datos aleatorios  
  
  
```python  
import numpy as np  
  
np.random.rand(10)  
np.random.normal(loc=5, scale=10, size=1000).std()  
```  
  
  
  
  
    9.833031005445132  
  
  
  
#### Tres distribuciones importantes:  
### Normal, Uniforme y Exponencial  
  
  
```python  
datos = np.random.normal(size=1000000)  
plt.hist(datos, color="pink", ec="black", alpha=0.5)  
plt.title("Distribución Normal")  
plt.show()  
  
datos = np.random.uniform(size=1000000)  
plt.hist(datos, color="skyblue", ec="black", alpha=0.5)  
plt.title("Distribución Uniforme")  
plt.show()  
  
datos = np.random.exponential(size=1000000)  
plt.hist(datos, color="green", ec="black", alpha=0.5)  
plt.title("Distribución Exponencial")  
plt.show()  
```  
  
  
     ![[output_5_0 4.png|700]]
  
     ![[output_5_1 3.png|700]]
  
     ![[output_5_2 3.png|700]]
___

## 3- Creación de Diagramas de Caja (BoxPlots)  

![](https://www.youtube.com/watch?v=wsfV4AO8UFw&ab_channel=C%C3%B3digoM%C3%A1quina)
  
```python  
import numpy as np  
import matplotlib.pyplot as plt  
  
edades = np.array([4, 17, 29, 33, 50, 51, 61, 71, 85, 92, 99])  
  
plt.yticks(np.arange(0, 110, 5))  
plt.grid(True)  
plt.boxplot(edades)  
plt.show()  
  
```  
  
     ![[output_1_0 5.png|700]]
  
```python  
(np.min(edades), np.quantile(edades, 0.25), np.median(edades),  
np.quantile(edades, 0.75), np.max(edades))  
```  
  
  
    (4, 31.0, 51.0, 78.0, 99)  
  
   
  
### Datos Anormales / Atípicos / Outliers  
  
  
```python  
edades = np.array([6,  
                   41, 51, 51, 52, 54, 57, 60, 61, 65,  
                   95, 100])  
  
plt.grid(True)  
plt.yticks(np.arange(0, 110, 5))  
plt.boxplot(edades)  
plt.show()  
  
```  
  
     
   ![[output_12_0.png|700]]
  
### La regla empírica 68–95–99.7  
  
  ![[empirical_rule.png]]
### Rango Intercuartil para Detectar Outliers  

![[IRQmejorado.png]]


____































___

%%
tags: #pagmachine_learning #python   

Vínculos: [[000-Menú Machine Learning 📃|Menú Machine Learning 📃]] 
%%