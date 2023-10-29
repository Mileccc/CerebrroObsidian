---
ID: 160
"tags:": 
nombre: Decoradores
---
___
# Decoradores
___
## 1- Conceptos iniciales

![](https://www.youtube.com/watch?v=DQXm6bIZgvk&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=74&ab_channel=pildorasinformaticas)

Este es un curso de programación en Python que explica el concepto y la estructura de las funciones decoradoras.

[00:05](https://www.youtube.com/watch?v=DQXm6bIZgvk&t=5) Los decoradores son funciones que agregan funcionalidades a funciones existentes.
- Los decoradores son como añadir cosas a los muebles o carteles a una pared.
- Los decoradores en Python agregan funcionalidades a las funciones
- La estructura de una función decoradora consta de tres funciones: a, b y c.

[01:51](https://www.youtube.com/watch?v=DQXm6bIZgvk&t=111) Decoradores de funciones en Python
- Los decoradores de funciones se utilizan para agregar funcionalidad adicional a una función.
- Los decoradores se definen mediante el símbolo @ y pueden aceptar parámetros.
- Los decoradores se pueden anidar, con una función decoradora llamando a otra.
- Los decoradores de funciones se utilizan ampliamente en la programación de Python.

[03:31](https://www.youtube.com/watch?v=DQXm6bIZgvk&t=211) Cree funciones de decorador para agregar funcionalidad a múltiples funciones.
- Cree una función decoradora para agregar funcionalidad.
- Cree una función normal llamada suma para imprimir la suma de dos valores numéricos.
- Crea una función normal llamada resta para imprimir la resta de dos valores numéricos.
- Llame a las funciones de suma y resta.
- Si el programa tiene múltiples funciones, crear funciones decoradoras puede simplificar agregar funcionalidades a todas ellas.

[05:22](https://www.youtube.com/watch?v=DQXm6bIZgvk&t=322) Agregue una función de decoración a las funciones existentes para imprimir mensajes informativos antes y después del cálculo.
- La función de decoración debería tomar otra función como parámetro.
- La función de decoración debe imprimir un mensaje antes y después de llamar a la función proporcionada.

[07:09](https://www.youtube.com/watch?v=DQXm6bIZgvk&t=429) Programación de funcionalidades adicionales con comentarios y decoradores.
- Agregar los comentarios necesarios para comprender cada parte del código.
- Implementando la primera funcionalidad de imprimir un mensaje.
- Incluir un cálculo y mostrarlo correctamente
- Llamar a la función decoradora y agregar otro aviso.
- Agregar acciones adicionales para decorar la funcionalidad.
- Devolviendo la función decoradora

[09:08](https://www.youtube.com/watch?v=DQXm6bIZgvk&t=548) La función se puede decorar para agregar acciones adicionales.
- Decorar la función implica especificar una función decoradora.
- La función decoradora agrega acciones adicionales a la función que se está decorando.

[11:07](https://www.youtube.com/watch?v=DQXm6bIZgvk&t=667) Funciones de decoración con decoradores.
- Las funciones de decoración permiten agregarles funcionalidades adicionales.
- Los decoradores se escriben delante de la función a decorar.

[12:49](https://www.youtube.com/watch?v=DQXm6bIZgvk&t=769) Las funciones de decoración se pueden utilizar para conectar y cerrar una base de datos.
- Las funciones de decoración pueden abrir una conexión a una base de datos.
- Las funciones de decoración pueden cerrar una conexión a una base de datos

### Ejemplo

```python
def conectar_base_datos(func):
    def wrapper():
        print("Conectando a la base de datos...")
        # Código para conectarse a la base de datos
        func()
        print("Cerrando la conexión a la base de datos...")
        # Código para cerrar la conexión a la base de datos
    return wrapper

@conectar_base_datos
def realizar_operacion():
    print("Realizando operación en la base de datos")

realizar_operacion()
```
$$CONSOLA$$
``Conectando a la base de datos... ``
``Realizando operación en la base de datos ``
``Cerrando la conexión a la base de datos...``

## 2- Creación de funciones decoradoras que aceptan parámetros
![](https://www.youtube.com/watch?v=_IwlE3Z7U04&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=74&ab_channel=pildorasinformaticas)

![](https://www.youtube.com/watch?v=KOw0tpcspH4&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=75&ab_channel=pildorasinformaticas)

El video se centra en los siguientes puntos clave:

1. Creación de funciones decoradoras que aceptan parámetros en Python.
2. Uso de la sintaxis `*args` para manejar un número indeterminado de argumentos en una función decoradora.
3. Uso de la sintaxis `**kwargs` para manejar argumentos clave-valor en una función decoradora.

Ejemplos en Python que reflejan el conocimiento enseñado en la transcripción:

1. Función decoradora con `*args`:

```python
def decorador_completo(func):
    def wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        print(f"Resultado: {result}")
        return result
    return wrapper

@decorador_completo
def operacion_personalizada(a, b, operador="+"):
    if operador == "+":
        return a + b
    elif operador == "-":
        return a - b
    else:
        return "Operador no válido"

# Llamando a la función decorada con argumentos y argumentos clave-valor
resultado1 = operacion_personalizada(7, 5, operador="+")
resultado2 = operacion_personalizada(12, 10, operador="-")

```
$$CONSOLA$$
``Resultado: 12 ``
``Resultado: 2``

___

%%
tags:  #programación #pagfundamentospython #python  

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%