---
ID: 95
"tags:": 
"nombre:": Recursividad e iteratividad
---
___
# Recursividad e iteratividad
___
## 1- Factoriales
![](https://youtu.be/qnWuJnBuUIg?si=H2vwcjmY_LXKZOJr&t=27)
___
El factorial de un número natural es la multiplicación de todos los números anteriores hasta llegar al 1. Por ejemplo el factorial de 5 es igual a  
5 * 4 * 3 * 2 * 1 , es decir , 120.
Igual que con la serie de Fibonacci, hay dos formas de resolver este problema: una con un loop for y la otra utilizando funciones recursivas.
Recuerden que cada función recursiva tiene que tener una condición terminal. En el caso de Fibonacci, la condición terminal es que fibo(1) = 1.
En el caso de factorial, la condición terminal será factorial(1)=1
Escriba ahora las dos versiones posibles de la función factorial(x)

**Solución Recursiva: **
```python
def factorial(num):
	if num == 0:
		return 1
    if num == 1:
        return 1
    else:
        return num*factorial(num-1)
  
factorial(5)
```
$Consola$
![[Pasted image 20230831134623.png]]
![[Pasted image 20230831134308.png]]

**Solución Iterativa**
```python
total=1
num=5
for n in range(num-1):
    total = total*(n+2)
    print(f"Vuelta {n+1}: {total}\n")
```
$Consola$
![[Pasted image 20230831134741.png]]
![[Pasted image 20230831135444.png]]


**Solución Iterativa con función**
```python
def factorial2(n):
    resultado = 1
    for i in range(1,n+1):
        resultado *= i
    return resultado
  
factorial2(5)
```
$Consola$
![[Pasted image 20230831134741.png]]
![[Pasted image 20230831141237.png]]

**Solución con while**
```python
def factorial(n):
    resultado=1
    while n>1:
        resultado*=n
        n=n-1
    return resultado
resultado
```
$$Consola$$
![[Pasted image 20230901095044.png]]

___
# Recursividad con Python: Ventajas y Desventajas
![](https://www.youtube.com/watch?v=Oy9vWWss1n4&list=PLat2DtY8K7YWkS1nAOBTqe4XmGzNiY2ce)

___
# Búsqueda Binaria con Python: Programación Iterativa y Recursiva
![](https://www.youtube.com/watch?v=Ds61hiuBcOk&list=PLat2DtY8K7YWkS1nAOBTqe4XmGzNiY2ce&index=2)

___



























___

%%
tags:  #programación #pagfundamentospython #python  #recursiva #recursivo #recursividad #iterativo #iteratividad #factorial

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%