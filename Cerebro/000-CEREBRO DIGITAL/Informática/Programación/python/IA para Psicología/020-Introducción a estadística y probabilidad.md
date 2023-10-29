---
ID:: 020
tags:: #pagiapsicologia #python  #pagpython #matemáticas 
nombre:: "Introducción a estadística y probabilidad"
---
___
# Introducción a estadística y probabilidad
___
## Definiciones de probabilidad
Disciplina de las matemáticas que trata con la incertidumbre, buscan cuantificar la aleatoriedad de eventos

 - **Experimento**: Un experimento o ensayo es un procedimiento que puede ser repetido infinitas veces y tiene un conjunto de salidas posibles bien definidas, conocido como espacio muestral.
 - **Espacio muestral** ( $\Omega$ ): Posibles resultados de un experimento
    - Ejemplo (moneda): {CC,CS,SC,SS} ( C= Cara , S=Seca)
- **Evento:** Un subconjunto de salidas posibles.
    - Ejemplo ( monedas): A={CC} , B={CS,SS} 

```python
import numpy as np

def tirar_dado():
	return np.random.randint(1,7)
```

```python
tirar_dado()
```
$$Consola$$
![[Pasted image 20230823074639.png]]

Ejercicio:
Tirar dado 1000 veces y guardar los resultados en una lista llamada "resultados"

```python
lista = []

for x in range(1000):
    resultado = tirar_dado()
    lista.append(resultado)
  
print(lista)
```
$$Consola$$
![[Pasted image 20230823075908.png]]

Por comprensión:
```python
lista = [tirar_dado() for x in range(1000)]

print(lista)
```
$$Consola$$
![[Pasted image 20230823075950.png]]

Usamos librería seaborn para visualizar gráficas:
```python
import seaborn as sns

sns.displot(lista)
```
$$Consola$$
![[Pasted image 20230823080510.png|500]]

## Medidas de tendencia central
### Media o promedio
Valor medio de nuestro conjunto de valores. Se consigue mediante la suma de los valores dividida entre la cantidad de estos:
$$\color{Yellow}\mu=\frac{2}{n}\sum\limits_{i=1}^{n}x_{1}=\frac{x_{1}+x_{2}+\dots+x_{n}}{n} $$
$$\color{purple}E[X]=\sum\limits_{x\epsilon X}xp(x)$$

Ejemplo: el promedio de un dado:
$$\color{Cyan}E[X]=1*\frac{1}{6}+2*\frac{1}{6}+3*\frac{1}{6}+4*\frac{1}{6}+5*\frac{1}{6}+6*\frac{1}{6}=3.5$$

#### Ejercicio : lanzar dado y calcular promedio
- **Forma 1:** Usando funciones
```python
sum(lista)/(len(lista))
```
$$Consola$$
![[Pasted image 20230823223313.png]]

- **Forma 2:** Usando bucle
```python
total = 0
  
for i in range(len(lista)):
    valor = lista[i]
    total += valor
  
total/len(lista)
```
$$Consola$$
![[Pasted image 20230823223356.png]]

- **Forma 3:** Usando método de numpy
```python
np.mean(lista)
```
$$Consola$$
![[Pasted image 20230823223356.png]]


___
### Mediana
Representa el valor de posición central en un conjunto de datos ordenados

Usando método de numpy
```python
np.median(lista)
```
$$Consola$$
![[Pasted image 20230823224154.png]]

Usa el valor central de una lista ordenada , la comparación con el promedio puede verse mejor con esta lista:
```python
x = [1,1,1,3,5,10000,10001]
print(np.median(x))
print(np.mean(x))
```
$$Consola$$
![[Pasted image 20230823224547.png]]

___
### Moda o modo
Valor que tiene mayor frecuencia absoluta. Son los picos que vemos en el histograma. Dependiendo de la distribución de los datos puede existir más de una.

![[Pasted image 20230823225230.png|900]]

___
### Ley de grandes números
La ley de los grandes números establece que si $X_{1},X_{2},X_{3},\dots$ es una sucesión infinita de variables aleatorias independientes que tienen el mismo valor esperado $\mu$ y varianza $\sigma^2$, entonces el promedio $\overline{X}_{n}=\frac{X_{1}+\dots+X_{n}}{n}$ converge en probabilidad a $\mu$ .
$$\color{Yellow}\lim_{ n \to \infty }P(
\lvert \overline{X}_{n}-\mu \rvert
<\varepsilon)=1 $$

#### Gráfica  de tendencia de la ley de los grandes números

```python
resultados = []
for lanzamientos in range(1,10000):
    lanzamientos = np.random.choice([1,2,3,4,5,6], lanzamientos)
    dados = lanzamientos.mean()
    resultados.append(dados)
  
plt.plot(resultados)
plt.title("Ley de grandes números")
plt.axhline(3.5)
plt.xlabel("Número de lanzamientos")
plt.ylabel("Frecuencia caras")
plt.show()
```
$$Consola$$
![[Pasted image 20230823232106.png]]

##### ¿ Que pasa si tomamos de a dos dados ?

```python
from itertools import product
  
espacio = [roll for roll in product([1,2,3,4,5,6], repeat = 2)]
print(*espacio, sep="\n")
totales = [sum(roll) for roll in espacio]
```
$$Consola$$
![[Pasted image 20230823232216.png]]

### Teorema del limite central
El teorema del límite central o teorema central del límite indica que, en condiciones muy generales, si $S_n$ es la suma de $n$ variables aleatorias independientes, con media conocida y varianza no nula pero finita, entonces la función de distribución de $S_n$ "se aproxima bien " a una distribución normal
#### Gráfica de distribución con dos dados

```python
plt.figure(figsize = (20, 4))
plt.subplot(121)
plt.hist(totales, bins =11)
plt.title("Total, dos dados")
plt.xlabel("Valores totales")
plt.ylabel("Número de ocurrencias")
plt.xticks(range(2,12))
plt.subplot(122)
ax = sns.kdeplot(np.array(totales))
ax.set(xlabel = "Valores totales", ylabel = "Número de ocurrencias",
       title = "Total, dos dados", xticks = range(2, 12),
       xlim = (1, 13));
```
$$Consola$$
![[Pasted image 20230823232754.png]]

___
## Axiomas clásicos de la probabilidad
- **Probabilidad de un evento**- Número asignado a un evento.
    - Ejemplo (moneda): $Pr(A)=\frac{1}{4}$
- **Axiomas**:
    1. $0< Pr(A)\leq 1$
    2. $Pr(\Omega)=1$
    3. $Pr(A\cup B)=Pr(A)+Pr(B)-P(A\cap B)$ (si $A$, $B$ son independientes $P(A\cap B)=0$)

#### ¿Cuál es la probabilidad de sacar un número $\color{RED}par$ o un número que sea $\color{RED}múltiplo$ de 3?
![[Pasted image 20230824183930.png|500]]
- $S=\{1,2,3,4,5,6\}$
- $P(A=par)=\frac{3}{6}=0.5$
- $P(B=multiplo\quad de\quad3)=\frac{2}{6}=\frac{1}{3})$
- $P(A\cap B)=\frac{1}{6},ya\quad que\quad A\cap B=\{6\}$
- $Pr(A\cup B)=\frac{3}{6}+\frac{2}{6}-\frac{1}{6}=\frac{4}{6}=\frac{2}{3}$

___
## Definiciones de estadística

| $\color{red}Concepto$             | $\color{red}Definición$                                   | $\color{red}Descripción$                                                                                                                                               |
|----------------------|----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Población            | Conjunto completo de elementos bajo estudio | La población se refiere a la totalidad de los elementos que estamos investigando o analizando en un estudio estadístico.                                 |
| Muestra              | Subconjunto de la población                  | Una muestra es un grupo seleccionado de elementos tomados de la población total. Es utilizada para hacer inferencias sobre la población en su conjunto. |
| Inferencia estadística | Extracción de conclusiones sobre población basadas en muestra | La inferencia estadística es el proceso de hacer afirmaciones o predicciones sobre la población basadas en el análisis de la muestra.          |
| Parámetro            | Característica numérica de la población     | Un parámetro es un valor numérico que describe alguna propiedad de la población total.                                                                    |
| Estadístico           | Característica numérica de la muestra        | Un estadístico es un valor numérico calculado a partir de la muestra, que se utiliza para estimar o inferir propiedades de la población.              |

| $\color{orange}Concepto$                   | $\color{orange}Definición$                                                 | $\color{orange}Descripción$                                                                                                                                                                      |
|----------------------------|------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Hipótesis nula o alternativa | Suposiciones sobre la población bajo estudio              | La hipótesis nula es una afirmación que asume que no hay diferencia o efecto entre los grupos o condiciones. La hipótesis alternativa sugiere que sí existe una diferencia.    |
| Test estadístico            | Procedimiento para evaluar la evidencia de los datos     | Un test estadístico es una metodología que utiliza los datos de la muestra para decidir si rechazamos o no la hipótesis nula, basándonos en un valor calculado llamado estadístico. |
| P-valor & Interpretación   | Probabilidad de obtener resultados al menos extremos     | El p-valor es la probabilidad de observar resultados tan extremos como los obtenidos, suponiendo que la hipótesis nula sea verdadera. Un p-valor bajo sugiere evidencia contra la nula. |
| Nivel de significancia      | Probabilidad de cometer un error tipo I al rechazar nula | El nivel de significancia (α) es el umbral predefinido para considerar los resultados como estadísticamente significativos. Controla la tasa de error tipo I en un test.         |

___
## Medidas de dispersión
### Rango
Valor numérico que indica la diferencia entre el valor máximo y el mínimo de una población o muestra estadística.
$$Max-Min$$
```python
tiempos_de_reaccion = [3.2,4.3,1,4.5,6,3,10]

def rango(lista):
	return max(lista) - min(lista)

rango(tiempos_de_reaccion)
```
$$Consola$$
![[Pasted image 20230824190822.png]]

### Varianza
$$\sigma^2_{n}=\frac{1}{n-1}\sum\limits_{i=1}^{n}(x_{i}-\overline{x})^2$$
La varianza es una medida de la dispersión de una distribución.
- $var[X]=E[(X-\mu)^2]$
- Ejemplo: la varianza de un dado de 6 lados :
$$var[X]=\sum\limits_{i=1}^{6}\frac{1}{6}(i-3.5)^2$$
$$E[X^2]=1^2*\frac{1}{6}+2^2*\frac{1}{6}+3^2*\frac{1}{6}+4^2*\frac{1}{6}+5^2*\frac{1}{6}+6^2*\frac{1}{6}=\frac{91}{6}$$
$$var[X]=E[X^2]-\mu^2=\frac{91}{6}-3.5^2\approx2.92$$

Con un ciclo for en python sería
```python
promedio = 3.5

for x in resultados:
	v = (x - promedio)**2
	total += v

total/(len(resultados) - 1)
```
$$Consola$$
![[Pasted image 20230824191730.png]]

Con numpy sería
```python
np.var(resultados)
```
$$Consola$$
![[Pasted image 20230824191730.png]]

___
#### Desvió estándar
Medida que se utiliza para cuantificar la variación o la dispersión de un conjunto de datos numéricos
$$\sigma=\sqrt{\frac{1}{n}\sum\limits_{i=1}^{n}(x_{i}-\overline{x})^2  }$$

___
### Covarianza
Valor que indica el grado de variación conjunta de dos variables aleatorias respecto a sus medidas

$$s_{xy}=\frac{1}{n}\sum\limits_{i=1}^{n}(x_{i}-\overline{x})(y_{i}-\overline{y})$$
 ### Correlación
 El coeficiente de correlación de Pearson indica la relación entre dos variables, independientes de sus unidades ya que está normalizado según las desviaciones de las variables. E r va desde -1 hasta 1 . ¿Qué significan estos valores?
$$r_{xy}=\frac{\sum(x_{i}-\overline{x})(y_{i}-\overline{y})}{(n-1)s_{x}s_{y}}$$
![[Pasted image 20230827200209.png|1000]]







___

%%
tags: #pagiapsicologia #python  #pagpython #matemáticas 

Vínculos: [[000-Menú IA Psicología 📃|Menú IA para Psicología📃]] , [[000-Menú Estadística y probabilidad📃|Menú Estadística y probabilidad📃]]
%%