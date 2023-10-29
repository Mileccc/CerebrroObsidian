---
ID: 65
"-tags:": "#programación #pagfundamentospython #python  #continue #break #pass #control_de_flujo"
"nombre:": Diferencia entre print y return
---
___
# Diferencia entre print y return

![](https://youtu.be/qnWuJnBuUIg?si=PiB0qmOJL-AbQjCx&t=620)

___

La diferencia entre `print` y `return` en Python es fundamental y se relaciona con cómo se manejan y utilizan los valores en funciones y en la salida del programa.

La función `print` se utiliza para mostrar información en la consola o en la salida estándar. Puedes pasar varios argumentos separados por comas a `print`, y la función los imprimirá en la consola, convirtiendo los valores en cadenas de texto si es necesario. Por ejemplo:

```python
x = 5
print("El valor de x es:", x)
```

Esto mostraría en la consola: "El valor de x es: 5". `print` no afecta el flujo de control del programa y no tiene impacto en los cálculos o en la lógica del código.

En contraste, la declaración `return` se utiliza en el contexto de una función para devolver un valor al llamador de la función. Cuando una función se llama y encuentra una declaración `return`, la función se detiene en ese punto y el valor especificado después de `return` se pasa de vuelta al punto de llamada. Esto permite que el resultado de una función se utilice en cálculos posteriores o en la lógica del programa. Por ejemplo:

```python
def suma(a, b):
    resultado = a + b
    return resultado

resultado_suma = suma(3, 4)
print("El resultado de la suma es:", resultado_suma)
```

En este caso, la función `suma` devuelve el valor de la suma de `a` y `b`, que luego se asigna a la variable `resultado_suma` y se imprime.

En resumen:

- `print` se utiliza para mostrar información en la consola.
- `return` se utiliza para devolver un valor de una función al punto de llamada.
___

%%
tags:  #programación #pagfundamentospython #python  

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%