---
ID: 
tags:
  - pagkotlin
nombre: Tutorial Android Studio
---
___
# Tutorial Android Studio
___
![](https://www.youtube.com/watch?v=vJapzH_46a8&list=PL8ie04dqq7_OcBYDpvHrcSFVoggLi3cm_)

___

Aquí está un curso escrito basado en la transcripción del video de Kotlin en Android Studio:

# Curso de Kotlin desde Cero

Bienvenidos a este curso completo de Kotlin desde cero. En las próximas lecciones aprenderemos:

- Fundamentos de programación 
- Sintaxis de Kotlin
- Variables y tipos de datos
- Operadores y expresiones 
- Sentencias de control de flujo
- Funciones
- Clases y objetos

Empezaremos con lo más básico para que puedas comprender los conceptos centrales de la programación. Luego aplicaremos esos conocimientos para construir programas reales en Kotlin. ¡Vamos a ello!

## Lección 1: Conceptos Básicos

Antes de escribir código, debemos entender algunas ideas fundamentales:

- Un **programa** es un conjunto de instrucciones que le dice a la computadora qué tareas realizar. 

- El **código fuente** contiene las instrucciones escritas en un lenguaje de programación como Kotlin.

- Para ejecutar el código, un **compilador** convierte el código fuente a código de máquina que entiende el procesador.

- Los **lenguajes de programación** nos permiten escribir el código fuente en una forma legible por humanos.

- **Kotlin** es un lenguaje moderno, conciso y seguro para crear aplicaciones Android.

Con estos conceptos claros, estamos listos para empezar a escribir código en Kotlin.

## Lección 2: Hola Mundo

Tradicionalmente, el primer programa que escribe un desarrollador es uno que imprime "Hola Mundo" en la pantalla. En Kotlin se ve así:

```kotlin
fun main() {
  println("Hola Mundo") 
}
```

Analicemos este programa:

- `main()` es una función especial requerida para ejecutar el código.

- `println()` es una función que imprime el texto entre comillas. 

- Las líneas terminan en `;` en Kotlin.

Ahora intenta modificar el programa para imprimir un mensaje personalizado.

## Lección 3: Variables

Las variables nos permiten almacenar información para usar luego en el programa. En Kotlin declaramos una variable con la palabra clave `var`:

```kotlin
var nombre = "Juan"
```

Esto crea una variable llamada `nombre` y le asigna el valor `"Juan"`.

Kotlin es un lenguaje tipado, por lo que debemos declarar el tipo de datos de cada variable:

```kotlin
var edad: Int = 25
```

Aquí `edad` es una variable de tipo `Int` (número entero) con valor 25.

Intenta crear algunas variables para almacenar información como tu nombre, apellido y edad.

## Lección 4: Tipos de Datos

Kotlin soporta los siguientes tipos de datos:

- `Int`: Números enteros
- `Double`: Números con punto flotante 
- `String`: Cadenas de texto
- `Boolean`: Valores verdadero/falso
- `Char`: Caracteres simples

Podemos usar estos tipos así:

```kotlin
var entero: Int = 5
var decimal: Double = 5.99
var texto: String = "Hola" 
var verdad: Boolean = true
var letra: Char = 'a'
```

Asegúrate de elegir siempre el tipo de dato más apropiado para la información que vas a almacenar.

## Lección 5: Operadores

Kotlin soporta los típicos operadores aritméticos y lógicos:

- Suma: `a + b`
- Resta: `a - b`
- Multiplicación: `a * b`
- División: `a / b`
- Módulo: `a % b`
- Igualdad: `a == b`  
- Negación: `!verdad`

Podemos usar operadores en expresiones así:

```kotlin
var resultado = 5 + 3 // 8
var esPar = numero % 2 == 0
```

Intenta crear variables y expresiones usando diferentes operadores en Kotlin.

## Lección 6: Expresiones

Las expresiones son fragmentos de código que realizan un cálculo y devuelven un valor. 

Por ejemplo, `1 + 2` es una expresión que devuelve el valor `3`.

Podemos asignar el resultado de una expresión a una variable:

```kotlin
var resultado = 1 + 2 // resultado = 3
```

O pasar expresiones directamente como argumentos a una función:

```kotlin  
println(1 + 2) // Imprime 3
```

Intenta crear algunas expresiones en Kotlin usando variables y operadores.

## Lección 7: Sentencias de Control de Flujo

Las sentencias de control de flujo nos permiten ejecutar diferentes códigos dependiendo de ciertas condiciones. Las más comunes son:

### if
Ejecuta un código si una condición es verdadera:

```kotlin
var edad = 20
if (edad >= 18) {
  println("Eres mayor de edad") 
}
```

### else
Ejecuta un código si la condición del if es falsa:

```kotlin
if (edad < 18) {
  println("Eres menor de edad")
} else {
  println("Eres mayor de edad")
}
```

### when
Compara una expresión contra múltiples valores:

```kotlin
when (VARIABLE) {
  1 -> println("Uno") 
  2 -> println("Dos")
  else -> println("Otro número")
}
```

Prueba usar if, else y when para controlar el flujo de tus programas.

## Lección 8: Funciones

Las funciones nos permiten encapsular código para ejecutarlo múltiples veces. Se declaran así:

```kotlin
fun saludar() {
  println("Hola!")
}
```

Y se invocan escribiendo el nombre seguido de paréntesis:

```kotlin
saludar() // Imprime "Hola!"
```

Las funciones pueden recibir parámetros:

```kotlin
fun saludar(nombre: String) {
  println("Hola $nombre!") 
}

saludar("Ana") // Imprime "Hola Ana!"
```

Y devolver valores:

```kotlin
fun sumar(a: Int, b: Int): Int {
  return a + b
}

var resultado = sumar(2, 3) // resultado = 5
```

Intenta crear algunas funciones útiles en tus programas.

## Lección 9: Clases y Objetos

Las clases nos permiten modelar objetos del mundo real como coches, personas, productos, etc.

Se declaran así:

```kotlin
class Persona(var nombre: String, var edad: Int) {

}
```  

Luego creamos objetos a partir de la clase con la palabra `object`:

```kotlin
var juan = Persona("Juan", 20)
```

Las clases pueden tener funciones llamadas métodos:

```kotlin
class Persona(var nombre: String, var edad: Int) {

  fun cumpleanos() {
    edad++ 
  }

}
```

Y propiedades para almacenar datos:

```kotlin
class Producto(var nombre: String, var precio: Double, var inventario: Int) {

}
```

Prueba modelando algunas clases relevantes para tu problema y creando objetos a partir de ellas.




___
%%
tags:  #pagkotlin

Vínculos:   [[000-Menú Kotlin 📃|Menú Kotlin 📃]]
%%