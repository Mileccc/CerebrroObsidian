---
ID:: 110
-nombre:: "Logaritmos"
-tags:: #matemáticas #álgebra #pagalgebra  

---
___
# Logaritmos
___
## 1- Introducción a los logaritmos
___
### Introducción a logaritmos
![](https://www.youtube.com/watch?v=LAkneQR6ig0&t=423s)

___
#### ¿Qué es un logaritmo?
Los **logaritmos** son otra manera de pensar en exponentes.

Por ejemplo, sabemos que $2^4$ es igual a $16$. Esto se expresa con la ecuación exponencial $2^4 = 16$.

Ahora supongamos que nos preguntan: "¿2 a que potencia es igual a $16$?" La respuesta sería: 4. Esto se expresa con la ecuación logarítmica $\log_2(16) = 4$ (y se lee como "log base dos de dieciséis es cuatro").

$2^4 = 16 \quad \Longleftrightarrow \quad \log_2(16) = 4$

Ambas ecuaciones describen la misma relación entre los números $2$, $4$, y $16$; donde $2$ es la **base** y $4$ es el **exponente**.

La diferencia es que la forma exponencial aísla la potencia $16$, y la forma logarítmica aísla el exponente $4$.

He aquí más ejemplos de ecuaciones logarítmicas y exponenciales equivalentes.

![[Pasted image 20230823104912.png]]

___

#### Definición de un logaritmo

Al generalizar los ejemplos anteriores obtenemos la definición formal de un logaritmo:

$\log_b(a) = c \quad \Longleftrightarrow \quad b^c = a$

Ambas ecuaciones describen la misma relación entre $a$, $b$ y $c$:

- $b$ es la **base**,
- $c$ es el **exponente**, y
- $a$ es el **valor de entrada**.

**Una observación útil**

Al volver a escribir una ecuación exponencial en forma de logaritmo, o una ecuación de logaritmo en forma exponencial, es útil recordar que la **base del logaritmo es la misma que la base del exponente**.

___
#### Evaluar logaritmos

¡Excelente! Ahora que ya entendemos la relación entre exponentes y logaritmos, veamos si podemos evaluar logaritmos.

Por ejemplo, evaluemos $\log_4(64)$.

Empecemos por igualar esa expresión a $x$:

$\log_4(64) = x$

Al escribir esto como una ecuación exponencial, obtenemos:

$4^x = 64$

¿$4$ elevado a qué potencia es igual a $64$? Pues bien, $4^3 = 64$, así que $\log_4(64) = 3$.

Con la práctica podrás condensar algunos de estos pasos, y evaluar $\log_4(64)$ simplemente preguntando "¿$4$ elevado a qué potencia es $64$?"

___
#### Restricciones en las variables

$\log_b(a)$ está definido cuando la base $b$ es positiva y diferente de $1$, y el argumento o valor de entrada $a$ es positivo. Estas restricciones son resultado de la conexión entre logaritmos y exponentes:

|Restricción|Razonamiento|
|---|---|
|$b > 0$|En una función exponencial, la base $b$ debe ser positiva por definición.|
|$a > 0$|$\log_b(a) = c$ significa que $b^c = a$. Como un número positivo elevado a cualquier potencia es positivo, es decir, $b^c > 0$, tenemos que $a > 0$.|
|$b \neq 1$|Supongamos por un momento que $b$ pudiera ser $1$. Consideremos ahora la ecuación $\log_1(3) = x$. La forma exponencial equivalente sería $1^x = 3$. Pero esto nunca puede ser verdadero, ya que $1$ elevado a cualquier potencia es siempre $1$. Así, tenemos que $b \neq 1$.|

Recuerda que estas restricciones aseguran que los logaritmos sean definidos y tengan sentido en el contexto de las matemáticas.

___
#### Logaritmos especiales

Aunque la base de un logaritmo puede ser una variedad de valores, hay dos bases que se utilizan más frecuentemente que las demás. Específicamente, la mayoría de las calculadoras tienen botones para estos dos tipos de logaritmos. Veamos cuáles son.

##### El logaritmo común

El logaritmo común es un logaritmo cuya base es $10$ ("logaritmo base 10"). Al escribir estos logaritmos matemáticamente, omitimos la base y se entiende que es $10$.

$\log_{10}(x) = \log(x)$

##### El logaritmo natural

El logaritmo natural es un logaritmo cuya base es $e$ ("logaritmo base $e$"). En lugar de escribir la base $e$, indicamos este logaritmo como $\ln(x)$, donde $\ln$ significa "logaritmo natural".

$\log_e(x) = \ln(x)$

Esta tabla resume lo que necesitamos saber acerca de estos dos logaritmos especiales:

|Nombre|Base|Notación usual|Notación especial|
|---|---|---|---|
|Logaritmo común|$10$|$\log_{10}(x)$|$\log(x)$|
|Logaritmo natural|$e$|$\log_e(x)$|$\ln(x)$|

Aunque la notación es diferente, ¡la idea para evaluar un logaritmo es exactamente la misma!

___

#### ¿Para qué estudiamos logaritmos?

Como acabas de aprender, los logaritmos revierten los exponentes. Por esta razón, son muy útiles para resolver ecuaciones exponenciales.

Por ejemplo, el resultado de $2^x = 5$ puede expresarse mediante un logaritmo: $x = \log_2(5)$. En las siguientes lecciones, aprenderás a evaluar esta expresión logarítmica.

Las expresiones y funciones logarítmicas también resultan ser muy interesantes por sí mismas y son muy comunes en el mundo que nos rodea. Por ejemplo, muchos fenómenos físicos se miden con escalas logarítmicas.

Estudiamos logaritmos para comprender mejor las relaciones entre los exponentes y las bases, para resolver ecuaciones exponenciales de manera más eficiente y para explorar fenómenos y funciones que siguen patrones logarítmicos en diversas disciplinas.

___
- **Ejercicio 1:**
![[Pasted image 20230823110249.png]]
___
- **Ejercicio 2:**
![[Pasted image 20230823110348.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230823110429.png]]

___
- **Ejercicio 4:**
![[Pasted image 20230823110506.png]]

___

### Evaluar logaritmos (avanzado)
![](https://www.youtube.com/watch?v=A8mv6Da0QiE)

___
- **Ejercicio 1:**
![[Pasted image 20230823111058.png]]


___
- **Ejercicio 2:**
![[Pasted image 20230823111234.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230823111436.png]]

___
- **Ejercicio 4:**
![[Pasted image 20230823111559.png]]

___
### La relación entre exponentes y logaritmos
![](https://www.youtube.com/watch?v=JMXcseQrslQ&t=190s)

___
### La relación entre exponentes y logaritmos: gráficas
![](https://www.youtube.com/watch?v=0gREhJtFJBw&t=328s)

___
### La relación entre exponentes y logaritmos: tablas
![](https://www.youtube.com/watch?v=6XdngsTuPWc&t=583s)


___
- **Ejercicio 1:**
![[Pasted image 20230823200930.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230823202246.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230823203026.png]]

___
- **Ejercicio 4:**
![[Pasted image 20230823203238.png]]

#logaritmo #exponentes #inversa #
___
## 2- La constante e y el logaritmo natural
___
### La constante 𝑒 y el interés compuesto
![](https://www.youtube.com/watch?v=21e-nYdnt3E&t=1s)

___
### 𝑒 como un límite
![](https://www.youtube.com/watch?v=ejd50AATm20&t=331s)

___
## Evaluar el logaritmo natural con una calculadora
![](https://www.youtube.com/watch?v=rVvgGAqa1k8&t=219s)

___

#prestamo #e #euler #interes #interes_compuesto #limite #logaritmo_natural #ln
___
## 3- Propiedades de los logaritmos
___
### Introducción a propiedades de logaritmos (1 de 2)
![](https://www.youtube.com/watch?v=3O60Y37u9aY)

___
### Introducción a propiedades de logaritmos (2 de 2)
![](https://www.youtube.com/watch?v=34o4PnpR_PM&t=606s)

___
### Introducción a propiedades de logaritmos

![[Pasted image 20230824160241.png]]


(Estas propiedades se aplican para cualesquiera valores de $M$, $N$ y $b$ para los cuales cada logaritmo esté definido, es decir para $M$, $N > 0$ y $0 < b \neq 1$.)

___
#### La regla del producto

La regla del **producto** establece que:

$\color{yellow}\log_b(MN) = \log_b(M) + \log_b(N)$

Esta propiedad indica que el logaritmo de un producto es igual a la suma de los logaritmos de sus factores.

**Ejemplo numérico:** Supongamos que tenemos $M = 5$ y $N = 10$. Aplicando la regla del producto:

$\color{yellow}\log_b(5 \cdot 10) = \log_b(5) + \log_b(10)$

Ahora, podemos usar esta propiedad para reescribir expresiones logarítmicas. Por ejemplo:

$\color{yellow}\log_b(20) = \log_b(4 \cdot 5) = \log_b(4) + \log_b(5)$

Esto nos permite simplificar la evaluación de logaritmos de productos en términos de logaritmos individuales de sus factores.

___
#### La regla del cociente
La regla del **cociente** establece que:

$\color{cyan}\log_b\left(\frac{M}{N}\right) = \log_b(M) - \log_b(N)$

Esta propiedad indica que el logaritmo de un cociente es igual a la diferencia de los logaritmos del dividendo y del divisor.

**Ejemplo numérico:** Supongamos que tenemos $M = 15$ y $N = 3$. Aplicando la regla del cociente:

$\color{cyan}\log_b\left(\frac{15}{3}\right) = \log_b(15) - \log_b(3)$

Ahora, podemos usar esta propiedad para reescribir expresiones logarítmicas. Por ejemplo:

$\color{cyan}\log_b\left(\frac{8}{2}\right) = \log_b(8) - \log_b(2)$

Esto nos permite simplificar la evaluación de logaritmos de cocientes en términos de logaritmos individuales del dividendo y el divisor.

**Ejemplo de expansión utilizando la regla del cociente:**
Del mismo modo, para el logaritmo $\log_7\left(\frac{a}{3}\right)$, podemos aplicar la regla del cociente:

$\color{cyan}\log_7\left(\frac{a}{3}\right) = \log_7(a) - \log_7(3)$

Estas expansiones nos permiten expresar logaritmos de productos y cocientes como diferencias de logaritmos individuales.

___
#### La regla de la potencia

La regla de la **potencia** establece que:

$\color{orange}\log_b(M^p) = p \cdot \log_b(M)$

Esta propiedad indica que el logaritmo de una potencia es igual al exponente multiplicado por el logaritmo de la base de la potencia.

**Ejemplo numérico:** Supongamos que tenemos $M = 4$ y $p = 3$. Aplicando la regla de la potencia:

$\color{orange}\log_b(4^3) = 3 \cdot \log_b(4)$

Ahora, podemos usar esta propiedad para reescribir expresiones logarítmicas. Por ejemplo:

$\color{orange}\log_b(8^2) = 2 \cdot \log_b(8)$

Esto nos permite simplificar la evaluación de logaritmos de potencias en términos de logaritmos individuales de la base.

**Ejemplo de expansión utilizando la regla de la potencia:**

Dado el logaritmo $\log_2(x^3)$, podemos expandirlo utilizando la regla de la potencia:

$\color{orange}\log_2(x^3) = 3 \cdot \log_2(x)$

Del mismo modo, para condensar expresiones logarítmicas utilizando la regla de la potencia, convertimos multiplicadores en potencias. Por ejemplo:

$\color{orange}4 \cdot \log_5(2) = \log_5(2^4) = \log_5(16)$

Esta propiedad nos permite expresar logaritmos de potencias como productos de logaritmos individuales o viceversa.

___
- **Ejercicio 1:**
![[Pasted image 20230824162340.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230824162634.png]]

___
### Usar la regla del producto en logaritmos
![](https://www.youtube.com/watch?v=cEAVi0SkNH0&t=305s)

___
### Usar la regla de potencias en logaritmos
![](https://www.youtube.com/watch?v=Ts58xBps9cQ&t=291s)

___
- **Ejercicio 1:**
![[Pasted image 20230824163550.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230824163634.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230824163718.png]]

___
- **Ejercicio 4:**
![[Pasted image 20230824163814.png]]

___
### Usar las propiedades de logaritmos: varios pasos
![](https://www.youtube.com/watch?v=LtOcpwdupss&t=133s)

___
### Prueba de la regla del producto en logaritmos
![](https://www.youtube.com/watch?v=UL85_Zujwec&t=431s)

___
### Prueba de las reglas del cociente y de la potencia en logaritmos
![](https://www.youtube.com/watch?v=BiDTrXSGQKQ&t=481s)

___
### Justificar las propiedades de los logaritmos
En esta lección, exploraremos tres propiedades esenciales de los logaritmos: la regla del producto, la regla del cociente y la regla de la potencia. Antes de comenzar, recordemos un hecho útil que será de gran ayuda en nuestro recorrido:

$\color{yellow}\log_b(bc) = c$

En otras palabras, un logaritmo en base $b$ ¡desafía el efecto de la potencia en base $b$!

#### Demostración de la regla del producto
Demostraremos un caso específico de la regla del producto, tomando el caso en el que $M = 4$, $N = 8$ y $b = 2$.

Al sustituir estos valores en $\log_2(MN)$, tenemos:

$\color{cyan}\log_2(4 \cdot 8) = \log_2(2^2 \cdot 2^3) = 2 + 3 = \log_2(2^2) + \log_2(2^3)$

Ya que $\color{cyan}2 = \log_2(4)$ y $\color{cyan}3 = \log_2(8)$.

Así, hemos demostrado que $\color{cyan}\log_2(4 \cdot 8) = \log_2(4) + \log_2(8)$.

Aunque esta demostración verifica un caso específico, podemos usar la misma lógica para demostrar la regla del producto en general.

Notamos que expresar $4$ y $8$ como potencias de $2$ fue clave en la demostración. Por lo tanto, en general, queremos que $M$, $N$, y $b$ sigan ciertas relaciones. Propongamos $M = b^x$ y $N = b^y$ para algún exponentes reales $x$ e $y$ (¿Por qué podemos hacer esto?). Entonces, por definición, también es cierto que $\log_b(M) = x$ y $\log_b(N) = y$.

Ahora, con estas nuevas definiciones, tenemos:

$\color{cyan}\log_b(MN) = \log_b(b^x \cdot b^y)$ (Sustitución) $\color{cyan}= \log_b(b^{x+y})$ (Propiedades de exponentes) $\color{cyan}= x + y$ (Propiedades de logaritmos y exponentes)

Por lo tanto, hemos demostrado que $\color{cyan}\log_b(MN) = \log_b(M) + \log_b(N)$ en general utilizando esta lógica.

___
#### Demostración de la regla del coeficiente
La regla del **cociente** establece que:

$\color{pink}\log_b\left(\frac{M}{N}\right) = \log_b(M) - \log_b(N)$

Para demostrar esta propiedad, podemos seguir un método similar al que hemos utilizado antes.

Nuevamente, si definimos $\color{pink}M = b^x$ y $\color{pink}N = b^y$, entonces tenemos que $\color{pink}\log_b(M) = x$ y $\log_b(N) = y$.

Ahora podemos demostrar la regla del cociente de la siguiente manera:

$\color{pink}\log_b\left(\frac{M}{N}\right) = \log_b\left(\frac{b^x}{b^y}\right)$ (Sustitución) $\color{pink}= \log_b(b^{x - y})$ (Propiedades de exponentes)$\color{pink}= x - y$ (Propiedades de logaritmos y exponentes)

Por lo tanto, hemos demostrado que $\color{pink}\log_b\left(\frac{M}{N}\right) = \log_b(M) - \log_b(N)$ utilizando este método de demostración.

Recuerda que esta propiedad es muy útil cuando trabajamos con logaritmos de cocientes, ya que nos permite expresar el logaritmo de un cociente como la diferencia de dos logaritmos individuales.

___
#### Demostración de la regla de la potencia
La regla de la **potencia** establece que:

$\color{lime}\log_b(M^p) = p \cdot \log_b(M)$

Para demostrar esta propiedad, podemos usar un enfoque similar al que hemos utilizado antes.

Tomemos $\color{lime}M = b^x$, lo que nos lleva a $\color{lime}\log_b(M) = x$.

Ahora podemos demostrar la regla de la potencia de la siguiente manera:

$\color{lime}\log_b(M^p) = \log_b((b^x)^p)$ (Sustitución) $\color{lime}= \log_b(b^{xp})$ (Propiedades de exponentes)$\color{lime}= xp$ (Propiedades de logaritmos y exponentes)

También sabemos que $\color{lime}\log_b(bc) = c$ (Sustitución).

Por lo tanto, hemos demostrado que $\color{lime}\log_b(M^p) = p \cdot \log_b(M)$ utilizando este método de demostración.

Alternativamente, también podemos justificar esta propiedad utilizando la regla del producto. Por ejemplo, sabemos que $\color{lime}\log_b(M^p) = \log_b(M \cdot M \cdot ... \cdot M)$, donde $\color{lime}M$ se multiplica por sí mismo $\color{lime}p$ veces. Ahora podemos utilizar la regla del producto, con la definición de multiplicación como una suma repetida, para completar la demostración:

$\color{lime}\log_b(M^p) = \log_b(M \cdot M \cdot ... \cdot M)$ (Definición de exponentes) $\color{lime}= \log_b(M) + \log_b(M) + ... + \log_b(M)$ (Regla del producto) $\color{lime}= p \cdot \log_b(M)$ (Suma repetida es multiplicación)

Estos métodos demuestran la propiedad de la regla de la potencia y cómo podemos utilizarla en la manipulación de expresiones logarítmicas.


#propiedades_logaritmos #demostración #logaritmo_producto #logaritmo_cociente #logaritmo_potencia 
___
## 4- La regla de cambio de base de logaritmos
___
### Evaluar logaritmos: regla de cambio de base
![](https://www.youtube.com/watch?v=A91qvN1ZKas&t=456s)

___
### Introducción a la regla de cambio de base
Supongamos que queremos encontrar el valor de la expresión $\log_2(50)$. Dado que $50$ no es una potencia exacta de $2$, evaluar esta expresión sin una calculadora puede ser complicado.

La mayoría de las calculadoras pueden calcular logaritmos en base $10$ y base $e$. Por lo tanto, para encontrar el valor de $\log_2(50)$, primero debemos cambiar la base del logaritmo a una de las bases que la calculadora puede manejar. Podemos usar la propiedad de cambio de base de los logaritmos para hacer esto. 

#### La regla de cambio de base

Podemos cambiar la base de cualquier logaritmo con la siguiente regla:

![[Pasted image 20230827153155.png]]

**Observaciones:**

- Al utilizar la regla de cambio de base de logaritmos, tienes la libertad de elegir cualquier base $x$ para el cambio de base.
- Es importante recordar que, para que esta propiedad funcione, los valores de entrada de los logaritmos deben ser positivos, y las bases de los logaritmos deben ser positivas y diferentes de $1$.

**Ejemplo: Evaluación de $\log_2(50)$**

Si deseas encontrar el valor del logaritmo, es recomendable cambiar la base a $10$ o $e$, ya que la mayoría de las calculadoras pueden calcular estos logaritmos.

Entonces, cambiemos la base de $\log_2(50)$ a $\log_{10}$. Para hacer esto, aplicamos la regla de cambio de base, con $b=2$, $a=50$, y $x=10$:

$\color{cyan}\log_2(50) = \frac{\log_{10}(50)}{\log_{10}(2)}$ (Regla de cambio de base)

$\color{cyan}\log_2(50) = \log(50) / \log(2)$ (Pues $\log_{10}(x) = \log(x)$)

Ahora podemos encontrar el valor con una calculadora:

$\color{cyan}\log(50) / \log(2) \approx 5.644$

Este es el valor aproximado de $\log_2(50)$.

#### Justificar la regla de cambio de base
En este punto, es posible que te estés preguntando: "Está bien, pero ¿por qué funciona esta regla?"

$\log_b(a) = \frac{\log_x(a)}{\log_x(b)}$

Vamos a abordar esto con un ejemplo concreto. Usando el ejemplo anterior, queremos mostrar que $\log_2(50) = \frac{\log(50)}{\log(2)}$.

Empecemos usando $n$ para denotar $\log_2(50)$. En otras palabras, tenemos $\log_2(50) = n$. Según la definición de logaritmos, $2^n = 50$.

Ahora aplicamos una serie de operaciones a ambos lados de la ecuación para mantener la igualdad:

$2^n = 50$

$\log(2^n) = \log(50)$

$n \log(2) = \log(50)$ (Regla de la potencia)

$n = \frac{\log(50)}{\log(2)}$ (Divide ambos lados entre $\log(2)$)

Dado que $n$ fue definido como $\log_2(50)$, tenemos que $\log_2(50) = \frac{\log_x(50)}{\log_x(2)}$, ¡como queríamos!

Con la misma lógica, podemos demostrar la regla de cambio de base. Simplemente reemplaza $2$ por $b$ y $50$ por $a$, elige cualquier nueva base $x$, ¡y ahí tienes tu demostración!

___
- **Ejercicio 1:**
![[Pasted image 20230827154351.png|900]]

___
- **Ejercicio 2:**
![[Pasted image 20230827154603.png|900]]

___
- **Ejercicio 3:**
![[Pasted image 20230827154732.png|900]]

___
- **Ejercicio 4:**
![[Pasted image 20230827154912.png|900]]

___
### Usar la regla de cambio de base de logaritmos
![](https://www.youtube.com/watch?v=nmlo0RYbopw&t=515s)


___
- **Ejercicio 1:**
![[Pasted image 20230827155652.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230827155853.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230827160059.png]]

___
- **Ejercicio 4:**
![[Pasted image 20230827160239.png]]

___
### Prueba de la regla de cambio de base
![](https://www.youtube.com/watch?v=Of-ZztirRnw&t=301s)

___
### Revisión de propiedades de logaritmos
___
#### ¿Cuáles son las propiedades de los logaritmos?

![[Pasted image 20230827160624.png]]


#logaritmo_regla_cambio #regla_cambio #cambio_de_base #propiedades_logaritmos #regla_cambio_de_base

___
## 5- Resolver ecuaciones exponenciales con logaritmos
___
### Resolver ecuaciones exponenciales con logaritmos: base 10
![](https://www.youtube.com/watch?v=QuC0dja3Z_Q&t=266s)

___
### Resolver ecuaciones exponenciales con logaritmos

#### Resolver ecuaciones exponenciales de la forma

$\color{cyan}a \cdot b^x = d$

Resolvamos $\color{cyan}5 \cdot 2^x = 240$.

Para resolver en función de $x$, primero debemos aislar la parte con el exponente. Para hacerlo, dividimos ambos lados por $5$. No multiplicamos el $5$ por el $2^x$ ya que este no es el orden correcto de las operaciones.

$\color{cyan}5 \cdot 2^x = 240$

$\color{cyan}2^x = 48$

Luego, resolvemos para $x$ convirtiendo la ecuación a una forma logarítmica.

$\color{cyan}2^x = 48$

$\color{cyan}x = \log_2(48)$

¡Y así de simple hemos resuelto la ecuación! La solución exacta es $\color{cyan}x = \log_2(48)$.

Dado que $48$ no es una potencia exacta de $2$, debemos usar la regla de cambio de base y nuestra calculadora para evaluar el logaritmo. Esto se muestra a continuación.

$\color{cyan}x = \log_2(48) = \frac{\log(48)}{\log(2)}$ (Regla de cambio de base)

$\color{cyan}x \approx 5.585$ (Evaluación con calculadora)

La solución aproximada, redondeada a la milésima más cercana, es $\color{cyan}x \approx 5.585$.


___
- **Ejercicio 1:**
![[Pasted image 20230827162613.png]]

___
- **Ejercicio 2:**
![[Pasted image 20230827162957.png]]

___
- **Ejercicio 3:**
![[Pasted image 20230827163254.png]]

___
#### Resolver ecuaciones exponenciales de la forma

$\color{yellow}a \cdot b^{cx} = d$

Veamos otro ejemplo. Resolvamos $\color{yellow}6 \cdot 10^{2x} = 48$, donde el $10$ está elevado a $2x$ y es representado como $10^{2x}$.

Nuevamente, comenzamos aislando el exponente dividiendo ambos lados entre $6$.

$\color{yellow}6 \cdot 10^{2x} = 48$

$\color{yellow}10^{2x} = 8$

A continuación, aislamos el exponente convirtiendo la ecuación a forma logarítmica.

$\color{yellow}\log_{10}(8) = 2x$

Finalmente, para despejar $x$, dividimos ambos lados por $2$:

$\color{yellow}x = \frac{\log_{10}(8)}{2}$

Esta es la respuesta exacta. Para aproximar la respuesta a la milésima más cercana, podemos ingresar esto en una calculadora. Observa que no hay necesidad de cambiar la base, ya que la base es $10$.

$\color{yellow}x = \frac{\log_{10}(8)}{2} \approx 0.452$

Evaluado con una calculadora, $x$ es aproximadamente $0.452$.



___
- **Ejercicio 4:**
![[Pasted image 20230827163956.png]]

___
- **Ejercicio 5:**
![[Pasted image 20230827164541.png]]

___
- **Ejercicio 6:**
![[Pasted image 20230827165002.png]]

___
- **Ejercicio 7:**
![[Pasted image 20230827165708.png]]
___
- **Ejercicio 8:**
![[Pasted image 20230827170443.png]]

___
- **Ejercicio 9:**
![[Pasted image 20230827170909.png]]

___
- **Ejercicio 10:**
![[Pasted image 20230827171217.png]]

___
- **Ejercicio 11:**
![[Pasted image 20230827171620.png]]

___
### Resolver ecuaciones exponenciales con logaritmos: base 2
![](https://www.youtube.com/watch?v=6P0hTK8EQ_A&t=478s)

___

___
- **Ejercicio 1:
![[Pasted image 20230828100633.png]]

___
- **Ejercicio 2:
![[Pasted image 20230828101125.png]]

___
- **Ejercicio 3:
![[Pasted image 20230828101836.png]]

___
- **Ejercicio 4:
![[Pasted image 20230828102348.png]]


#ecuaciones_exponenciales #cambio_de_base
___

## 6- Resolver modelos exponenciales
___
### Problemas verbales sobre modelos exponenciales: disolución de un medicamento
![](https://www.youtube.com/watch?v=zC9uAoVS2tE&t=1s)

___
### Problemas verbales sobre modelos exponenciales: crecimiento bacterial
![](https://www.youtube.com/watch?v=2vodlQd_Vbc)


___
- **Ejercicio 1:
![[Pasted image 20230828103844.png]]

___
- **Ejercicio 2:
![[Pasted image 20230828104613.png]]

___
- **Ejercicio 3:
![[Pasted image 20230828105151.png]]

___
- **Ejercicio 4:
![[Pasted image 20230828110527.png]]

___

%%
Vínculos:
[[000-Menú Algebra📃| Menú álgebra]] 

tags:
#matemáticas #álgebra #pagalgebra  
%%