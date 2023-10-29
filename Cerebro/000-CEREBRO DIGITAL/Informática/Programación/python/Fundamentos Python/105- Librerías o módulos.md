---
ID:: 105
tags:: #programación #pagfundamentospython #python 
nombre:: "Librerías o módulos"
---
___
# Librerías o módulos
___
![](https://youtu.be/gPN294xBbdc?t=2994)

___

Los módulos son archivos de Python que contienen funciones y variables. Podemos importar los módulos y acceder a las funciones y variables con el operador "." (punto) o agregándolos a nuestro **namespace**. Contamos con las siguientes maneras de importar funciones de un módulo:

1. Importar todo el módulo con el mismo nombre que tiene

`import datetime`

2. Importar el módulo con un alias más corto (por comodidad)

`import datetime as dt`

3. Importar únicamente un sub-módulo

`from datetime import datetime`

4. Importar directamente todos los nombres de funciones (en general no recomendado)

`from datetime import *`

___
## 1 Módulos de "Python nativo"
Cuando instalamos Python, hay algunos módulos que contienen funcionalidad básica y para poder utilizarlos los tenemos que importar explícitamente.

Hay módulos para trabajar con fechas (datetime), para interactuar con el sistema operativo donde nuestro programa está corriendo (os), para generar números aleatorios (random), para hacer operaciones matemáticas (math) y muchos otros más.



**`datetime` Modulo**

```python
# Ejemplo de uso de datetime
import datetime
print(datetime.datetime.now())
```
$$Consola$$
![[Pasted image 20230820221105.png]]

```python
import datetime as dt
print(dt.datetime.now())
```
$$Consola$$
![[Pasted image 20230820221131.png]]

```python
import misfunciones
misfunciones.misuma(3,2)
```
$$Consola$$
![[Pasted image 20230820221506.png]]


```python
from datetime import datetime
print(datetime.now())
```
$$Consola$$
![[Pasted image 20230820221623.png]]

```python
from datetime import *

print(datetime.now())
```
$$Consola$$
![[Pasted image 20230820221634.png]]


**`math` Modulo**
Nos permite hacer tener acceso a funciones matemáticas, que originalmente, están programadas en C.

```python
import math

print(dir(math))
```
$$Consola$$
'__doc__', '__loader__', '__name__', '__package__', '__spec__', 'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'ceil', 'comb', 'copysign', 'cos', 'cosh', 'degrees', 'dist', 'e', 'erf', 'erfc', 'exp', 'expm1', 'fabs', 'factorial', 'floor', 'fmod', 'frexp', 'fsum', 'gamma', 'gcd', 'hypot', 'inf', 'isclose', 'isfinite', 'isinf', 'isnan', 'isqrt', 'lcm', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'log2', 'modf', 'nan', 'nextafter', 'perm', 'pi', 'pow', 'prod', 'radians', 'remainder', 'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'tau', 'trunc', 'ulp'


```python
log_21 = math.log(21)
print(log_21)
```
$$Consola$$
![[Pasted image 20230820221938.png]]



```python
coseno_pi = math.cos(math.pi)
print(coseno_pi)
```
$$Consola$$
![[Pasted image 20230820222006.png]]

___
## 2. Módulos propios
Cuando estemos creando aplicaciones grandes y complejas, será necesario llevar alguna de la funcionalidad que desarrollemos a módulos.

Para eso es necesario escribir archivos que tengan nuestro código, y luego importar los módulos localmente.

```python
with open('misfunciones.py', 'w') as out:
    out.write("""def misuma(a,b):
        print('Sumando!')
        return a+b""")
```


```python
from misfunciones import misuma

misuma(3,2)
```
$$Consola$$
![[Pasted image 20230820222157.png|400]]


___
## 3. Módulos de terceros
Cada lenguaje de programación tiene su propio sistema de gestión de paquetes donde la comunidad contribuye con distintos módulos. En el caso de Python este sistema es [PyPI](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fpypi.org%2Fproject%2Fpip%2F) . Los organizadores de este proyecto se encargan de fijar estándares de calidad para las librerías que se distribuyan a través del mismo.

Los entornos (como collab) que tienen instalado python, en general, también tienen instalado un software que se llama python-pip. Este nos permite ejecutar el comando pip para descargar librerías desde PyPI.

Este comando lo podemos ejecutar desde una terminal, o desde la propia jupyter notebook si utilizamos la sintaxis "!" para cada línea o el comando \%%bash para cada celda.

La sintaxis es:

`pip install [nombre del paquete]`

Opcionalmente podemos especificar una versión de ese paquete. Si no lo hacemos, va a descargar la última que encuentre para la versión de python-pip que tenemos instalada.

`pip install [nombre del paquete][==version]`

Cuando desarrollamos aplicaciones en Python, es muy importante tener en cuenta el manejo de versiones. Para que nuestro código funcione adecuadamente, el ambiente donde la aplicación corre tiene que tener las mismas versiones de librerías que usamos al momento de desarrollar.

Esto generalmente se maneja a través de un archivo, **requirements.txt**, que contiene todos los paquetes que la aplicación necesita con sus respectivas versiones.


#### Ejemplo de uso de pip


```python
!pip install seaborn==0.9.0
```
$$Consola$$
![[Pasted image 20230820222510.png]]



```python
import seaborn as sns
```

```python
# Con este comando podemos consultar la versión de cualquier módulo.
sns.__version__
```
$$Consola$$
![[Pasted image 20230820222635.png]]

```python
sns.scatterplot(x=[3,4,5,6],y=[6,8,10,12]);
```
$$Consola$$
![[Pasted image 20230820222702.png]]



___

%%
tags:  #programación #pagfundamentospython #python 

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%