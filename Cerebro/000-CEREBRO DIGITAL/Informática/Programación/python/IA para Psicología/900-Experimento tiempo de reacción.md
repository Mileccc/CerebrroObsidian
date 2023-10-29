---
ID:: 015
tags:: #pagiapsicologia #python  #pagpython #matplotlib #docx #clases #poo #super #tiempo_de_reacción
nombre:: "Experimento tiempo de reacción"
---
___
# Experimento tiempo de reacción

___

##### Aplicación de POO: Experimento de Tiempo de Reacción

En esta clase vamos a utilizar un diseño de POO para crear una batería de experimentos:

- Tiempo de Reacción
- Cuestionario

Para eso, tendremos una clase Sujeto que contendrá un id de sujeto, una clase abstracta **Experimento** de la cual heredarán las de **Tiempo de Reacción** y **Cuestionario**, y una clase para generar un **Reporte** de los resultados automáticamente.

Empezamos creando una clase para definir el _sujeto_ del experimento.

![[Pasted image 20230815073710.png]]
Veamos como funciona nuestra clase.

![[Pasted image 20230815073911.png]]

![[Pasted image 20230815074020.png]]

Una vez que ya contamos con sujeto. Definimos una clase para la realización del experimento.

La clase tendrá tres métodos:

> - **instrucción**: dará una pauta sobre como realizar el experimento.
> - **corregir_datos**: toma los datos crudos y calcula un resultado
> - **tomar_experimento:** realizará el experimento.

![[Pasted image 20230815074217.png]]

![[Pasted image 20230815074305.png]]

![[Pasted image 20230815074322.png]]
___
### Tiempo de Reacción

---

Para tomar el experimento se utilizarán dos modulos/librerias: **time** y **random**.

> - **time**, nos va a ayudar a calcular el tiempo durante nuestro experimento.
> - **random**, nos va a permitir generar números aleatorios.

___
### Ejercicio:

Crear una función _tomar_experimento_ que ejecute una prueba de tiempo de reacción. Para esto, recibe como argumento "rango_pausa", que es el rango de segundos máximo que puede demorar entre un estímulo y el siguiente.

Usando:

- La función **time.time()** para devolver el tiempo actual en segundos
- La función **random.random()** para generar un número aleatorio entre 0 y 1 y variar el tiempo de pausa
- La función **time.sleep(s)** para hacer una pausa de _s_ segundos
- Y la función **input()** que aguarda una entrada del usuario, bloqueando la ejecución hasta que ingresa la tecla _ENTER_.

---

Pista en pseudocódigo:
```
Dado un entero "n_trials"

Hacer "n_trials" veces:
  Tomar un tiempo 0
  Aguardar input
  Tomar un tiempo 1
  Calcular diferencia entre tiempos
  Agregar diferencia a la lista
  Hacer una pausa random de tiempo
```
---

Tipo de celda no admitido. Haz doble clic para inspeccionar/editar el contenido.

![[Pasted image 20230815074605.png]]

![[Pasted image 20230815074617.png]]

![[Pasted image 20230815074629.png]]

___
### Utilizando nuestra clase

![[Pasted image 20230815074805.png]]

![[Pasted image 20230815074818.png]]

![[Pasted image 20230815074828.png]]

![[Pasted image 20230815074838.png]]

¿Que datos contiene?

![[Pasted image 20230815074903.png]]

![[Pasted image 20230815074916.png]]

___
### Cuestionario

Generamos un cuestionario de ejemplo. Cada pregunta debe estar separada en un renglón (es decir por un caracter de _newline_, generalmente '\n')

![[Pasted image 20230815075033.png]]

![[Pasted image 20230815075058.png]]

Usamos la clase anterior para tomar el cuestionario

![[Pasted image 20230815075240.png]]

![[Pasted image 20230815075249.png]]

![[Pasted image 20230815075302.png]]

### Generando Reporte

---

Una vez realizado el ejercicio vamos a generar una clase para realizar el reporte del experimento.

La clase Reporte va a generar un documento que contendrá:

- Un método para analizar los datos resultado del experimento;
- Un método para crear gráficos a partir de los resultados.
- Un método para para generar el informe final

---

Para los gráficos vamos a usar matplotlib, que tiene métodos como "plot" donde recibe listas de números y genera un objeto "Figura". En este tema de visualización se ahonda en el curso de Análisis de Datos. La función **sns.set()** simplemente aplica un estilo.

![[Pasted image 20230815075425.png]]

![[000-CEREBRO DIGITAL/Informática/Programación/python/IA para Psicología/ANEXOS/Sin título.png]]

![[Pasted image 20230815075450.png]]

![[Pasted image 20230815075533.png]]


![[Pasted image 20230815075626.png]]

![[Pasted image 20230815075635.png]]


![[Pasted image 20230815075645.png]]


___

%%
tags: #pagiapsicologia #python  #pagpython #matplotlib #docx #clases #poo #super #tiempo_de_reacción

Vínculos:    [[000-Menú IA Psicología 📃|Menú IA para Psicología📃]] , [[030-Diccionarios|Diccionarios]] , [[900-Algoritmos|Algoritmos]]
%%