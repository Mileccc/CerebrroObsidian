---
ID:: 030
-nombre:: "Transformaciones, congruencia y semejanza"
-tags:: #matemáticas #geometría #paggeometria #paggeometria_analitica #eje_de_simetria #transformación #traslación #rotación #reflexión #escalado #homotecia #congruencia #semejanza
---


___
## Eje de simetría
Es una línea imaginaria que divide una figura en dos partes idénticas, reflejando una mitad en la otra. Cualquier punto de la figura que esté en un lado del eje tiene un punto simétrico en el otro lado, a la misma distancia del eje.
![[Pasted image 20230801092030.png|700]]




___
## Transformaciones
Transformaciones que cambian la posición y la forma de figuras geométricas en el plano o en el espacio.
### Transformaciones Rígidas
#### Traslación
Una traslación es un tipo de transformación que toma cada punto en una figura y lo desplaza la misma distancia en la misma dirección.
![](https://cdn.kastatic.org/ka-perseus-graphie/168f0d1a34b21809970f4a5ed627bee29a04a26f.svg)

#### Rotación
En la siguiente figura, una copia del trapecio gira alrededor del punto.

![Un trapecio dentro de un círculo. El trapecio gira alrededor del centro del círculo. Dos lados del trapecio son paralelos. Los otros dos lados del trapecio son congruentes.](https://cdn.kastatic.org/ka-perseus-images/8e275ec8b813162427cf94d29ad22e7b3775a61d.gif)

En geometría, las rotaciones giran cosas cíclicamente alrededor de un punto central dado. Observa que se mantiene la distancia de cada punto rotado alrededor del centro. Solo cambia su posición relativa.
##### El ángulo de rotación

Toda rotación está definida por dos parámetros importantes: el centro de la rotación (ya vimos eso), y **el ángulo de rotación**. El ángulo determina cuánto rotamos el plano alrededor del centro.

![El punto A gira alrededor del punto P en sentido contrario a las manecillas del reloj para formar A prima.](https://cdn.kastatic.org/ka-perseus-graphie/59fa7ed805eee4006e96a2b14ee0dd9b41fb5fde.svg)

El punto A gira alrededor del punto P en sentido contrario a las manecillas del reloj para formar A prima.

Por ejemplo podemos decir que A se obtiene al rotar A alrededor de P, pero eso no es suficientemente preciso.

Para definir la medida de la rotación nos fijamos en el ángulo creado entre los segmentos PA y PA′
![[Pasted image 20230801095415.png|300]]

El segmento PA gira alrededor del punto P 45º en sentido contrario a las manecillas del reloj para formar el segmento primo PA'.

De esta manera podemos decir que A′ es el resultado de rotar A por 45° alrededor de P.

##### Rotaciones en sentido y en contra de las manecillas del reloj

Así numeramos los cuadrantes del plano coordenado.

![[Pasted image 20230801100007.png]]

Los números de cuadrantes aumentan al moverse en sentido contrario a las manecillas del reloj. Medimos los ángulos siempre así para ser consistentes.


#### Reflexión
Una reflexión es un tipo de transformación que toma cada punto de una figura y la refleja a lo largo de una recta.

![](https://cdn.kastatic.org/ka-perseus-graphie/95bace51b2382a1e2ca60b66c186ccce01d819fa.svg)

### Transformaciones No Rígidas
#### Escalado o Homotecia
Aumento o disminución proporcional del tamaño de una figura.
![[Pasted image 20230801092943.png|400]]
Ejemplo:
https://es.khanacademy.org/math/geometry/hs-geo-transformations/hs-geo-dilations/v/dilating-shapes-shrinking
___
## Congruencia
Si podemos asignar una figura a otra utilizando transformaciones rígidas, son congruentes. Todavía son congruentes si necesitamos utilizar más de una transformación para mapearla. No es así si usamos una transformación que cambia el tamaño de la forma.
![[congruencia.png|400]]

### ¿Cuáles son los criterios de congruencia de triángulos?


- **Lado-lado-lado (LLL)**
Cuando los tres pares de lados correspondientes son congruentes, los triángulos son congruentes.
![Dos triángulos con tres lados congruentes.](https://cdn.kastatic.org/ka-perseus-graphie/334d0d09c1c96458d6753f83737d193ee642cca6.svg)

- **Lado-ángulo-lado (LAL)**
Cuando dos pares de lados correspondientes y los ángulos correspondientes entre ellos son congruentes, los triángulos son congruentes.
![Dos triángulos con dos lados congruentes y un ángulo congruente en medio de ellos.](https://cdn.kastatic.org/ka-perseus-graphie/dc426194c549e5e62120296c6a7dcb9342309dcd.svg)

- **Ángulo-lado-ángulo (ALA)**
Cuando dos pares de ángulos correspondientes y los lados correspondientes entre ellos son congruentes, los triángulos son congruentes.
![Dos triángulos con dos ángulos congruentes y un lado congruente en el centro de ellos.](https://cdn.kastatic.org/ka-perseus-graphie/531834dbe17d1fd1e9d341d30cf579e16c385f68.svg)


- **Ángulo-ángulo-lado (AAL)**
Cuando dos pares de ángulos correspondientes y un par de lados correspondientes (no entre los ángulos) son congruentes, los triángulos son congruentes.
![Dos triángulos con un lado congruente, un ángulo congruente y un segundo ángulo congruente.](https://cdn.kastatic.org/ka-perseus-graphie/1ffd26013d34a0eeea132a00f7ff3aebcdf4eb33.svg)

- **Hipotenusa-cateto (HC)**
Cuando las hipotenusas y un par de lados correspondientes de _triángulos rectángulos_ son congruentes, los triángulos son congruentes.
![Dos triángulos rectángulos con catetos e hipotenusas congruentes.](https://cdn.kastatic.org/ka-perseus-graphie/21f3bea44ef19777d964c34786742fd397df5686.svg)

### ¿Por qué lado-lado-ángulo no es un criterio de congruencia de triángulos?

Cuando dos pares de lados correspondientes y un par de ángulos correspondientes (no entre los lados) son congruentes, los triángulos _pueden ser_ congruentes, pero no siempre.

Con este criterio generalmente _no hay suficiente información_ cuando los ángulos correspondientes son opuestos al menor de los dos lados conocidos en el triángulo. Tenemos que evitarlo especialmente cuándo la figura puede no estar a escala.

![Dos triángulos donde un lado es congruente, otro lado es congruente, luego un ángulo no incluido es congruente.](https://cdn.kastatic.org/ka-perseus-graphie/eddc305f0c87819d6215caab68af60dd634e7a45.svg)

### ¿Podemos estar seguros de que dos triángulos _no_ son congruentes?

Un triángulo solo tiene 3 lados y 3 ángulos. Si conocemos 4 medidas laterales distintas o 4 medidas angulares distintas, entonces sabemos que los dos triángulos _no_ pueden ser congruentes. A veces conocemos las medidas a partir del diagrama. Otras veces utilizamos herramientas como el teorema de Pitágoras o la suma de ángulos internos del triángulo para obtener las medidas que faltan.
___


## Semejanza
Dos formas son similares si podemos cambiar una forma por la otra usando transformaciones rígidas (como el movimiento o la rotación) y dilataciones (haciéndola más grande o más pequeña). Otros tipos de transformaciones pueden cambiar los ángulos o las proporciones de las longitudes en una figura. Si necesitamos esos tipos de transformaciones, las formas no son similares.
![[semejanzatriangulovertice_20140326192751.gif]]

![[045-Triángulos Pitágoras ,congruencia y semejanza#Postulados de Semejanza]]
___
### Ejercicios semejanza
![](https://www.youtube.com/watch?v=fwQUL8GvblY)

![](https://www.youtube.com/watch?v=7K9ztcwm4GM&t=19s)
___
%%
Vínculos:
[[000-Menú Geometría Analítica📃|Menú Geometría Analítica]] , [[045-Triángulos Pitágoras ,congruencia y semejanza|Triángulos Pitágoras y semejanza]]

tags:
#matemáticas #geometría #paggeometria #paggeometria_analitica #eje_de_simetria #transformación #traslación #rotación #reflexión #escalado #homotecia #congruencia #semejanza
%%