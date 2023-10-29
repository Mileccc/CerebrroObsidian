---
ID:: 065
-nombre:: "Serie definida recursivamente"
-tags:: #matemáticas #álgebra #pagalgebra #recursividad #series #fibonacci #coeficientes_binomiales #razón  

---
___

# Serie definida recursivamente

Una serie definida recursivamente es una secuencia de números en la que cada término se calcula utilizando una fórmula que involucra términos anteriores de la misma serie. En otras palabras, cada término de la serie depende de los términos anteriores en la secuencia, y esta dependencia se establece mediante una relación recursiva o una regla de recurrencia.

Las series definidas recursivamente son un concepto interesante en matemáticas y se pueden encontrar en diversas áreas, como teoría de números, análisis matemático y combinatoria. Estas series a menudo se utilizan para modelar situaciones en las que cada paso o término depende del paso o término anterior, lo que puede reflejar ciertos procesos naturales o estructuras matemáticas.

## Serie de Fibonacci
Un ejemplo simple de una serie definida recursivamente es la _serie de Fibonacci_. En esta serie, los dos primeros términos son 0 y 1, y a partir del tercer término, cada término es la suma de los dos términos anteriores. Matemáticamente, esto se puede definir como:

F₀ = 0, 
F₁ = 1, 
Fₙ = Fₙ₋₁ + Fₙ₋₂ para n ≥ 2.


Esta definición indica que el tercer término (F₂) es la suma de los dos términos anteriores (F₁ + F₀), el cuarto término (F₃) es la suma de los tercer y segundo términos (F₂ + F₁), y así sucesivamente.


## Coeficientes binomiales
Otro ejemplo es la serie de recurrencia para calcular los números combinatorios, también conocidos como _coeficientes binomiales_. Estos números se utilizan en combinatoria para contar las formas en que se pueden seleccionar elementos de un conjunto. La fórmula de Pascal establece una relación recursiva entre los números combinatorios:

C(n, k) = C(n-1, k-1) + C(n-1, k),

donde C(n, k) representa el número combinatorio de "n" elementos tomados "k" a la vez.

Las series definidas recursivamente a menudo requieren un término inicial o un conjunto de términos iniciales para comenzar la secuencia. Estos términos iniciales se conocen como condiciones iniciales y son fundamentales para la generación de la serie.


### Ejemplo de serie recursiva

La expresión :$$a_{i}=a_{i−j}⋅  \frac{9}{10}$$​Define una serie recursiva en la que cada término _a_i_ se calcula multiplicando el término anterior a_i−j​ por 9/10. La variable j es una constante que determina cuántos términos anteriores se retrocede en cada paso de la serie para calcular el nuevo término.

Aquí hay una explicación más detallada de cómo funciona esta serie recursiva:

1. **Inicialización**: Para comenzar la serie, necesitas tener valores iniciales para algunos términos. Por ejemplo, podrías tener a_0, a_1, a_2​, etc., dependiendo de cuántos términos iniciales proporciones.
    
2. **Cálculo recursivo**: Una vez que tengas los términos iniciales, puedes usar la fórmula $$a_{i}=a_{i−j}⋅  \frac{9}{10}$$para calcular los términos subsiguientes. En esta fórmula, i representa el índice del término que estás calculando y i−j representa el índice del término anterior del cual estás obteniendo el valor.
    
3. **Razón de multiplicación**: La razón de 9/10 indica que cada término se multiplica por 0.9 en comparación con el término anterior. Esto significa que cada término es el 90% del término anterior.
    
4. **Retroceso**: La variable j determina cuántos términos retrocedes para obtener el término anterior. Por ejemplo, si j=1, estarás retrocediendo un término para obtener el valor anterior. Si j=2, estarás retrocediendo dos términos, y así sucesivamente.


___
%%
Vínculos:
[[000-Menú Algebra📃| Menú álgebra]] 

tags:
#matemáticas #álgebra #pagalgebra #recursividad #series #fibonacci #coeficientes_binomiales #razón  
%%