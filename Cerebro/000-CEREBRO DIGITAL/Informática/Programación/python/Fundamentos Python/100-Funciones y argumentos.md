---
ID:: 100
tags:: #programación #pagfundamentospython #python  #argumentos #args #kwargs #default #funciones
nombre:: "Funciones y argumentos"
---
___
# Funciones y argumentos
___
## Funciones
![](https://youtu.be/EVZ7HRUBDc4?t=3071)
___

Las funciones nos permiten estandarizar y reutilizar un proceso en múltiples ocasiones.

Como patrón de diseño, las funciones tienen que ser lo más atómicas posibles, es decir, resolver un problema lo más pequeño posible y bien definido.

Los nombres también son importantes, el nombre de la función tiene que reflejar lo mejor posible lo que hace.

Las funciones se definen de la siguiente manera:

![[Pasted image 20230815185231.png]]


Las variables definidas en el contexto de una función son locales, es decir, sólo viven dentro de esa función. Por otra parte, si desde una función se llama a una variable que no está definida en la función tratará de buscarla afuera. En general, es buena práctica usar sólo variables definidas dentro de la función o argumentos.

Los argumentos son variables que le pasamos a la función para que _haga algo_.

Las funciones emplean dos términos reservados:

- def: que indica el comienzo de la definición de la función
    
- return: establece la variable o variables que devuelve la función
    

En este punto vale la pena mencionar que en Python los nombres (de variables, funciones, etc.) se almacenan y ordenan en NameSpaces. En este punto, la información definida dentro de la función no es compartida con el exterior de la función (salvo algunas excepciones que no vienen al caso), por lo tanto, para compartirla, la función debe enviar desde el NameSpace local (el de la función) al NameSpace global (donde está el resto del programa). Para ello, el término return indica qué se devolverá al ambiente global. Para que efectivamente esa/s variable/s que la función devuelve se guarden en una variable en el ambiente global debemos asignar el resultado a una variable. Esto va a quedar más claro con el código.

Por último, vale la pena mencionar que _print_ sólo nos muestra el contenido de una variable pero no envía la información desde la función hacia afuera.
![[Pasted image 20230815185503.png]]
![[Pasted image 20230815185513.png]]


![[Pasted image 20230815185527.png]]
![[Pasted image 20230815185536.png]]


![[Pasted image 20230815185544.png]]
![[Pasted image 20230815185554.png]]

- **Ejemplo:**
![[Pasted image 20230815191439.png]]
$$Resultado$$
![[Pasted image 20230815191527.png]]

- **Ejemplo 2**:
```python
'''
Escribir una función que tome una lista con distintos elementos (de cualquier tipo) y
devuelva una lista sólo con los últimos tres números que aparecen.
'''

def ultimos_tres_numeros(lista):
    numeros = [x for x in lista if isinstance(x, (int, float)) and not isinstance(x, bool)][-3:]
    return numeros

# Ejemplo de uso
mi_lista = [1, "a", 2.5, "b", True, 10, "c"]
ultimos_tres_numeros_elementos = ultimos_tres_numeros(mi_lista)
print(ultimos_tres_numeros_elementos)
```

___

## Argumentos
___
### Argumentos por default
En las funciones existen argumentos se pueden pasar por posición o por su nombre. Algunos de los argumentos tienen un valor por default.
```python
def unir_lista(lista, conector=' '):
    """Esta funcion recibe dos argumentos, una lista y un conector
    y devuelve la lista unida usando el conector."""
    unida = conector.join([str(e) for e in lista])
    return unida
```

```python
unir_lista(['unir',3,'cosas'])
```
$$Resultado$$
![[Pasted image 20230817123913.png]]

```python
unir_lista(['probando', 'unir', 'lista', 123], conector = ',')
```
$$Resultado$$
![[Pasted image 20230817124101.png]]

Lo que no podemos hacer es pasar el argumento nombrado antes de el o los posicionales

```python
unir_lista(conector = ',',['probando', 'unir', 'lista', 123])
```
$$Resultado$$
![[Pasted image 20230817124233.png]]


Cuando se usan los argumentos por su nombre, pueden pasarse en cualquier orden
```python
unir_lista(conector = ',',lista = ['probando', 'unir', 'lista', 123])
```
$$Resultado$$
![[Pasted image 20230817124429.png]]

### args y Kwargs o funciones estrellas
Existen distintos tipos de argumentos, principalmente los llamados "args" y "kwargs", o argumentos y "keyword arguments" es decir argumentos nombrados.

---

También podemos tener un numero variable de argumentos, usando el símbolo , por convención al parámetro se le llama __'args'__

---
##### args
Internamente, los elementos de _args_ se tratan como una tupla
[[025-Tuplas|Tuplas]]

```python
def suma_todos(*args):
    print(type(args))
    return sum(args)
```

```python
suma_todos(9,1,4,2)
```
$$Resultado$$
![[Pasted image 20230817124854.png]]

##### Kwargs
En cambio los elementos de **kwargs** se tratan como un diccionario
[[030-Diccionarios|Diccionarios]]

```python
def consulta(**kwargs):
    print(type(kwargs))
    texto = f"Su consulta es {kwargs['fecha']} a las {kwargs['hora']}"
    return texto
```

```python
consulta(fecha='hoy',hora='4PM')
```
$$Resultado$$
![[Pasted image 20230817125045.png]]

___


Finalmente, podemos juntar todo lo visto en una misma función, es decir, tener argumentos sin nombre sin valor default, argumentos con valores default, args y kwargs. Esto es especialmente útil cuando necesitamos enviar args o kwargs a otras funciones usadas dentro de una función.

```python
valor_consulta = {"consulta":10, "arreglos_caries":20, "flúor":15}
```

```python
costos = list(valor_consulta.values())
costos
```
$$Resultado$$
![[Pasted image 20230817125229.png]]

```python
def emitir_factura(nombre, dni, tipo="DNI", *args, **kwargs):
    factura = ""
    factura += f"Gracias por su visita Nombre:{nombre} \n"
    factura += f"{tipo} {dni} \n"
    costo = suma_todos(*args) # hago unpacking de args
    factura += f"El costo es {costo} \n"
    factura += consulta(**kwargs) # hago unpacking de kwargs
    return factura
```

```python
factura = emitir_factura("Obi Wan", 370310455, "DNI", *costos, fecha="hoy", hora="5PM")
```
$$Resultado$$
![[Pasted image 20230817125332.png]]

```python
print(factura)
```
$$Resultado$$
![[Pasted image 20230817125418.png]]

Los args se pueden pasar como _*args_ o directamente los valores _sueltos_ en la llamada a la función , y luego la función se encargaría de empacarlos y desempacarlos.
```python
factura = emitir_factura("Obi Wan", 370310455, "DNI", 10 , 20, 15 , fecha="hoy", hora="5PM")
```

___

%%
tags:  #programación #pagfundamentospython #python   #argumentos #args #kwargs #default #funciones

Vínculos:    [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%