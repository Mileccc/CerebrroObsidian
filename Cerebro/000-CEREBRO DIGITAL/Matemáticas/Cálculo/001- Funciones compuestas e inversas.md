---
"ID:": 
"-nombre:": Funciones compuestas e inversas
"-tags:": "#matemáticas #pagcálculo"
---
___
# Funciones compuestas e inversas
___
## 1- Composición de funciones
___
### 1.1- Introducción a la composición de funciones
![](https://www.youtube.com/watch?v=Nc7dtwfgqtM&t=1s)

___
### 1.2- Introducción a la composición de funciones
Cam es un agricultor. Cada año siembra semillas de maíz. La siguiente función indica la cantidad de maíz, $C$ en kilogramos (kg), que él espera cosechar en $a$ acres de terreno.

$$\color{yellow}C(a)=7500a−1500$$

Por ejemplo, si Cam siembra dos acres, él espera cosechar

$$\color{yellow}C(2) = 7500(2) - 1500 = 13,500\:kg\:de\:maíz.$$

Pero a Cam le interesa más saber cuánto dinero ganará al vender su maíz. Así que utiliza la siguiente función para predecir la cantidad de dinero, $M$ en pesos, que él obtendrá al vender $C$ kilogramos de maíz.

$$\color{yellow}M(c) = 0.9c - 50$$
Entonces, si Cam cosecha 13,500 kg de maíz, él espera obtener 
$$\color{yellow}M(13,500) = 0.9(13,500) - 50 = $12,100$$

Observa que Cam utiliza dos funciones separadas para obtener ganancias esperadas a partir de acres cosechados. La primera función, $C(a)$, convierte de acres a cantidad de maíz, mientras que la segunda, $M(c)$, convierte de maíz a cantidad de dinero.

![[Pasted image 20230910170540.png]]

¿No sería genial si Cam pudiera escribir una función que convierta de acres sembrados directamente a ganancias esperadas?

![[Pasted image 20230910171021.png]]

***Crear una nueva función***
De hecho, ¡sí podemos obtener la función que convierte de acres sembrados directamente a ganancias esperadas! Para determinar esta función, pensemos en la pregunta más general: ¿cuánto dinero puede Cam esperar ganar si siembra maíz en $a$ acres de terreno?

Pues bien, si Cam siembra maíz en $a$ acres, él espera cosechar $C(a)$ kilogramos de maíz. Y si cosecha $C(a)$ kilogramos de maíz, espera ganar $M(C(a))$ pesos.

![[Pasted image 20230910171129.png]]

Entonces, para determinar la regla general que convierta $a$ acres directamente a ganancias esperadas, podemos determinar la expresión $M(C(a))$.

¿Pero cómo hacer esto? Observemos que en la expresión $M(C(a))$, el valor de entrada de la función $M$ es $C(a)$. Así que para evaluar esta expresión, podemos sustituir $C(a)$ como valor de entrada $c$ en la función $M$.

$$M({\color{orange}c})=0.9{\color{orange}c}-50$$
$$M({\color{orange}C(a)})=0.9({\color{orange}C(a)})-50$$
$$=0.9({\color{orange}7500a-1500})-50$$
$$=6750a-1350-50$$
$$=6750a-1400$$
De esta manera, la función $M(C(a)) = 6750a - 1400$ convierte acres sembrados directamente a ganancias esperadas. Usemos esta nueva función para predecir la cantidad de dinero que Cam obtendría al sembrar maíz en dos acres.

$$M(C(2)) = 6750(2) - 1400=$12100$$
Cam puede esperar obtener $12,100 al sembrar maíz en dos acres de terreno, ¡lo que es consistente con el primer resultado!

***Definir funciones compuestas***
Hemos obtenido lo que se conoce como una función compuesta. En lugar de sustituir acres sembrados en la función del maíz y después la cantidad de maíz cosechado en la función del dinero, obtuvimos una función que convierte acres sembrados directamente en ganancias esperadas.

Hicimos esto al sustituir $C(a)$ en la función $M$, es decir, al obtener $M(C(a))$. Llamemos $M \circ C$ a esta nueva función, que se lee como "M compuesta con C".

Ahora sabemos que $(M \circ C)(a) = M(C(a))$, y esta es, de hecho, ¡la definición formal de composición de funciones!

***Visualizar los dos métodos***
He aquí una ayuda visual para interpretar la definición anterior.

![[Pasted image 20230910172049.png]]

Al utilizar las funciones $C$ (la del maíz) y $M$ (la del dinero), la función $C$ convierte $2$ en $13,500$. Después, la función $M$ convierte $13,500$ en $12,100$ pesos.

Mediante la función compuesta, vemos que $(M \circ C)$ convierte $2$ directamente en $12,100$ pesos.

¡Ambas son equivalentes!

___
#### Ejercicios

___
- Ejercicio 1:
![[Pasted image 20230911100734.png]]

___
- Ejercicio 2:
![[Pasted image 20230911101114.png]]


___
- Ejercicio 3:
![[Pasted image 20230911101339.png]]

___
### 1.3- Composición de funciones
Dadas dos funciones, podemos combinarlas de tal manera que las salidas de una función se conviertan en las entradas de otra. Esta acción define una **función compuesta**. ¡Veamos qué significa esto!

***Evaluar funciones compuestas***
**Ejemplo**

$$si\:f(x)=3x-1\:y\:g(x)=x^3+2,\:entonces,\:¿qué\:es\:f(g(3))?
$$
**Solución**
Una forma de evaluar $f(g(3))$ es trabajar "de adentro hacia afuera". En otras palabras, evaluemos $g(3)$ primero, y después sustituyamos ese resultado en $f$ para encontrar nuestra respuesta.

Evaluemos g(3).

$$g(x)=x^3+2$$
$$g(3)=(3)^3+2$$
$$=29$$
Como $g(3)=29$, entonces $f(g(3))=f(29)$

Ahora evaluemos $f(29)$

$$f(x)=3x-1$$
$$f(29)=3(29)-1$$
$$=86$$
Así tenemos $f(g(3))=f(29)=86$

![[Pasted image 20230911102144.png]]

***Encontrar la función compuesta***
En el ejemplo anterior, la función $g$ convirtió $3$ a $29$, y la función $f$ convirtió $29$ a $86$. Encontremos la función que convierte $3$ directamente a $86$.

![[Pasted image 20230911102224.png]]

Para hacer esto, debemos componer las dos funciones y encontrar $f(g(x))$.

**Ejemplo**
Para calcular $f(g(x))$, primero sustituimos la función $g(x)$ en la función $f(x)$:

$f(g(x)) = 3(g(x)) - 1$

Dado que $g(x) = x^3 + 2$, sustituimos esta expresión en $f(g(x))$:

$f(g(x)) = 3(x^3 + 2) - 1$

Ahora, simplificamos la expresión:

$f(g(x)) = 3x^3 + 6 - 1$

$f(g(x)) = 3x^3 + 5$

Entonces, la función $f(g(x))$ es igual a $3x^3 + 5$.

$f(g(3)) = 3(3)^3 + 5$

$=86$

___
- **Ejercicio 1:**
![[Pasted image 20230911102914.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230911103106.png]]

***Funciones compuestas: una definición formal***
En el ejemplo anterior, encontramos y evaluamos una función compuesta. En general, para indicar la función $f$ compuesta con la función $g$, podemos escribir $f \circ g$, que se lee como "f compuesto con g". Esta composición se define con la siguiente regla:

(f∘g)(x)=f(g(x))

El siguiente diagrama muestra la relación entre $(f \circ g)(x)$ y $f(g(x))$:

![[Pasted image 20230911103330.png]]

**Ejemplo**
$g(x)=x+4$
$h(x)=x^2-2x$
Encuentra $(h \circ  g)(x)$ y $(h\circ g)(-2)$

**Solución**
$(h \circ  g)(x)=h(g(x))$
$=(g(x))^2-2(g(x))$
$=(x+4)^2-2(x+4)$
$=x^2+8x+16-2x-8$
$=x^2+6x+8$

Puesto que ahora tenemos la función h o g, podemos simplemente sustituir x por -2 para encontrar (h o g)(-2).

$(h\circ g)(-2)=h(g(-2))$
$=h(2)$
$=0$

El siguiente diagrama muestra como se relaciona $(h\circ g)(-2)$ con $h(g(-2))$

![[Pasted image 20230911104203.png]]

Aquí podemos ver que la función **g** convierte $-2$ a $2$, y la función **h** convierte $2$ a $0$, mientras que la función **h∘g** convierte $-2$ directamente a 0.

___
- **Ejercicio 1:**
![[Pasted image 20230911104919.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230911105349.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230911105528.png]]


___
- **Ejercicio 4:**
![[Pasted image 20230911105924.png]]

___
### 1.4- Evaluar funciones compuestas
![](https://www.youtube.com/watch?v=QudAUxQqgVQ)
___
#### Ejercicios: Evalúa funciones compuestas

___ 
- Ejercicio 1:
![[Pasted image 20230911110439.png]]

___ 
- Ejercicio 2:
![[Pasted image 20230911110618.png]]

___ 
- Ejercicio 3:
![[Pasted image 20230911110815.png]]

___ 
- Ejercicio 4:
![[Pasted image 20230911110926.png]]


___
### 1.5- Evaluar funciones compuestas: usar tablas
![](https://www.youtube.com/watch?v=IDkHmBJskdE&t=1s)

___
### 1.6- Evaluar funciones compuestas: usar gráficas
![](https://www.youtube.com/watch?v=2lilU5xJM0I)

___
#### Ejercicios: Evalúa funciones compuestas: gráficas y tablas

___ 
- Ejercicio 1:
![[Pasted image 20230913073856.png]]


___ 
- Ejercicio 2:
![[Pasted image 20230913074022.png]]

___ 
- Ejercicio 3:
![[Pasted image 20230913074131.png]]

___ 
- Ejercicio 4:
![[Pasted image 20230913074232.png]]

___
### 1.7- Encontrar funciones compuestas
![](https://www.youtube.com/watch?v=ACuwlPCyxsE)

___
#### Ejercicios: Encuentra funciones compuestas

___ 
- Ejercicio 1:
![[Pasted image 20230913074735.png]]

___ 
- Ejercicio 2:
![[Pasted image 20230913074850.png]]

___ 
- Ejercicio 3:
![[Pasted image 20230913075027.png]]


___ 
- Ejercicio 4:
![[Pasted image 20230913075210.png]]

___
### 1.8- Evaluar funciones compuestas (avanzado)
![](https://www.youtube.com/watch?v=eE2ZUBWcVF8)

___
## 2- Modelar con composición de funciones
___
### 2.1- Modelar con composición de funciones
![](https://www.youtube.com/watch?v=GGIDDBJtk4s)

___
### 2.2- Modelar con funciones compuestas: paracaidismo
![](https://www.youtube.com/watch?v=5cOKj15G1ew&t=1s)

___
### 2.3- Componer funciones de manera significativa
![](https://www.youtube.com/watch?v=Dsi8tFaVEpU&t=1s)

___
#### Ejercicios: Modela con funciones compuestas

___
- **Ejercicio 1:**
![[Pasted image 20230913081532.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230913083416.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230913083906.png]]

___
- **Ejercicio 4:**
![[Pasted image 20230913084221.png]]


___
## 3- Funciones invertibles
___
### 3.1-  Determinar si una función es invertible
![](https://www.youtube.com/watch?v=Z7u6dtANuEk&t=1s)

___
### 3.2- Introducción a las funciones invertibles
**Funciones inversas**, en el sentido más amplio, son funciones que hacen lo "contrario" de cada una. Por ejemplo, si $f$ convierte $a$ en $b$, entonces la inversa debe convertir $b$ en $a$.

![[Pasted image 20230914183128.png]]

##### ¿Todas las funciones tienen una función inversa?

Considera la función finita $h$ definida en la siguiente tabla:

![[Pasted image 20230914183217.png]]

Podemos crear un diagrama de mapeo para la función h.

![[Pasted image 20230914183258.png]]

Ahora vamos a invertir el mapeo para encontrar la función inversa, $h^{-1}$.

![[Pasted image 20230914183331.png]]

Observa que $h^{-1}$ mapea el valor 2 a dos diferentes valores: 1 y 3. Esto significa que $h^{-1}$ no es una función.

Puesto que la inversa de $h$ no es una función, decimos que $h$ es ``no invertible``.

En general, una función es invertible solo cuando cada valor de entrada tiene un valor de salida único. Es decir, cada valor de salida corresponde a exactamente un valor de entrada. De esa manera, cuando el mapeo se invierte, también es una función.

He aquí un ejemplo de una función invertible $g$. Observa que la inversa es efectivamente una función.

![[Pasted image 20230914183532.png]]

##### Ejercicios: Comprueba tu comprensión


___
- **Ejercicio 1:**
![[Pasted image 20230914184119.png]]


___
- **Ejercicio 2:**
![[Pasted image 20230914184218.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230914184444.png]]

___
##### Funciones invertibles y sus gráficas
![[Pasted image 20230914184550.png]]

Considera la gráfica de la función $y = x^2$.

Sabemos que una función es invertible si cada valor de entrada tiene un valor de salida único. En otras palabras, si cada valor de salida corresponde a exactamente un valor de entrada.

Pero este no es el caso de $y = x^2$.

Considera el valor 4, por ejemplo. Observa que al trazar la línea recta $y = 4$, puedes ver que hay dos valores de entrada, 2 y -2, asociados al valor de salida 4. Esto significa que la función $y = x^2$ no es invertible, ya que no cumple con la propiedad de que cada valor de entrada tenga un valor de salida único.

![[Pasted image 20230914184802.png]]

De hecho, si deslizas la línea hacia arriba y hacia abajo, verás que la mayoría de los valores de salida están asociados con dos valores de entrada. Así que la función $y = x^2$ es una función no invertible.

En contraste, considera la función $y = x^3$.

![[Pasted image 20230914184848.png]]

Si tomamos una línea recta horizontal y la deslizamos hacia arriba y hacia abajo, ¡siempre interseca a la función en un solo punto! Esto significa que cada valor de salida corresponde a exactamente un valor de entrada. En otras palabras, cada valor de entrada tiene un valor de salida único. La función $y=x^3$ es invertible. Este razonamiento describe lo que se conoce como la prueba de la línea horizontal: en general, una función $f$ es invertible si pasa la prueba de la línea horizontal.

#### Ejercicios: Comprueba tu comprensión

___
- **Ejercicio 1:**
![[Pasted image 20230914185420.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230914185525.png]]

___
#### Ejercicios: Determina si una función es invertible

___
- **Ejercicio 1:**
![[Pasted image 20230914185816.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230914190030.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230914190203.png]]


___
- **Ejercicio 4:**
![[Pasted image 20230914190309.png]]

___
### 3.3-  Restringir el dominio de funciones para hacerlas invertibles
![](https://www.youtube.com/watch?v=h3mO9mJOmWg)

___
#### Ejercicios: Restringe el dominio de funciones para hacerlas invertibles

___
- **Ejercicio 1:**
![[Pasted image 20230914191230.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230914191841.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230914192135.png]]

___
- **Ejercicio 4:**
![[Pasted image 20230914192419.png]]

___
## 4- Funciones inversas en gráficas y tablas
___
### 4.1- Leer valores inversos de una gráfica
![](https://www.youtube.com/watch?v=ZHfIVPEhKjU)

___
### 4.2- Leer valores inversos de una tabla
![](https://www.youtube.com/watch?v=mvGmhdpmM_4)

___
#### Ejercicios: Funciones inversas: gráficas y tablas

___
- **Ejercicio 1:**
![[Pasted image 20230915195211.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230915195331.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230915195826.png]]

___
- **Ejercicio 4:**
![[Pasted image 20230915195927.png]]

___
## 5- Comprobar funciones inversas por composición
___
### 5.1- Verificar funciones inversas a partir de tablas
![](https://www.youtube.com/watch?v=7Tv8QSSp32I)

___
### 5.2- Usar valores específicos para poner a prueba los inversos
![](https://www.youtube.com/watch?v=OmbAcPvEocY&t=1s)

___
### 5.3- Comprobar funciones inversas por composición
![](https://www.youtube.com/watch?v=ZZdFAMbiFog)

___
### 5.4- Comprobar funciones inversas por composición: no inversas
![](https://www.youtube.com/watch?v=O-jlS2MqJzI)

___
### 5.5 Comprobar funciones inversas por composición


**Funciones inversas**, en el sentido más amplio, son funciones que hacen lo "contrario" de cada una. Por ejemplo, si una función convierte a en b, entonces su inversa debe convertir b en a.

Tomemos las funciones _**f(x)**_ y _**g(x)**_ como ejemplo: $f(x)=\frac{x+1}{3}$ y $g(x)=3x-1$.

Observa que _**f(5)**_ $= \frac{5+1}{3} = 2$ y _**g(2)**_ $= 3 \cdot 2 - 1 = 5$.

![[Pasted image 20230915202047.png]]

Aquí vemos que al aplicar _**f**_ seguida de _**g**_, obtenemos nuevamente el valor de entrada original. Escrito como una composición, esto es $g(f(5))=5$. Pero, para que dos funciones sean inversas, debemos comprobar que esto ocurre para todo valor de entrada posible, independientemente del orden en que _**f**_ y _**g**_ se apliquen. Esto da lugar a la regla de composición de inversas.

#### La regla de composición de inversas

Estas son las condiciones para que dos funciones _**f**_ y _**g**_ sean inversas:

1. $f(g(x))=x$ para todo _**x**_ en el dominio de _**g**_.
2. $g(f(x))=x$ para todo _**x**_ en el dominio de _**f**_.

Esto es porque si _**f**_ y _**g**_ son inversas, componer _**f**_ y _**g**_ (en cualquier orden) crea una función que para cualquier valor de entrada regresa el mismo valor. A esta función la llamamos "la función identidad".

___
- **Ejercicio 1:**
![[Pasted image 20230915202923.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230915203246.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230915203633.png]]


___
#### Ejercicios: Comprueba funciones inversas

___
- **Ejercicio 1:**
![[Pasted image 20230916072813.png]]


___
- **Ejercicio 2:**
![[Pasted image 20230916074750.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230916075509.png]]

___
- **Ejercicio 4:**
![[Pasted image 20230916075656.png]]

___
%%
Vínculos:
[[000-Menú de Cálculo📃|Menú de Cálculo📃]]

Tags:
#matemáticas #pagcálculo 
%%