---
ID:: 120
tags::  #programación #pagfundamentospython #python  #init #constructor #self #objeto #clase #def #monkey_patching #duck_typing #métodos_especiales #métodos_estaticos #clase_punto #clase_linea #protegido #no_publico #privado #protected #protegido #protección_de_acceso #herencia #padre #hijo 
nombre:: "Programación orientada a objetos"
---
___
# Programación orientada a objetos
![](https://www.youtube.com/watch?v=1PfQLOCpp_Y)

En el paradigma de programación orientada a objetos los programas se estructuran organizando el código en entidades llamadas objetos. Estos nos permiten encapsular data, funciones y variables dentro de una misma clase. Veamos de qué se trata.

___

## Terminología de clases y objetos

---

1. Una **clase** es un prototipo de objeto, que engloba atributos que poseen todos los objetos de esa clase. Los atributos pueden ser datos como variables de clase y de instancia, y métodos (funciones). Se acceden con un punto.
    
2. Una **instancia** es un objeto en particular que pertenece a una clase.
    
3. Los **atributos** son variables asociadas a los objetos. Los atributos pueden ser de clase (toman el mismo valor para toda la clase) o de instancia (toman un valor diferente para cada instancia). Lo más común de utilizar son los atributos de instancia que reflejan estados de los objetos. Los atributos de clase se utilizan para que todos los objetos compartan por ejemplo, las mismas configuraciones o la misma conexión a una base de datos.
    
4. La **herencia** es la transferencia de atributos de una clase a otra clase
    
5. Un **método** es una función contenida dentro de un objeto.
    
6. Un **objeto** es una instancia única de una estructura definida por su clase. Posee atributos,  variables de clase, de instancia y métodos.
    
7. El **polimorfismo** nos permite utilizar una misma función para distintos tipos de datos o clases.
    
8. La **delegación** es el concepto con el cual podemos delegar tareas de una clase sobre algún método de otra clase.
    

---

## Creando la primera clase

```python
import math
```

```python
#La sintáxis es:
class Ejemplo:
    pass

# Instancio la clase
x = Ejemplo()

print(type(x))
```
$$Consola$$
![[Pasted image 20230820224154.png]]

Por convención, las clases se nombran empleando "upper camel case". Es decir, con mayúscula para cada término que sea parte del nombre.

---

Una librería famosa en Python por sus clases es "requests". Esta ĺibrería se usa para acceder a información web por HTTP. Algunas de sus clases son:

- Session
- Request
- ConnectionError
- ConnectTimeout

Las últimas dos clases son para especificar errores, noten que se repiten las mayúsculas.

---

Podemos pensar a una clase como un molde, el cual usamos para generar objetos o instancias que tienen ciertos atributos o métodos (funciones) que deseamos mantener.

Aquellos atributos y métodos que queremos que los objetos conserven son definidos como parte del constructor. El constructor en Python es el método reservado **__init__()**. Este método se llama cuando se instancia la clase y en ese momento se inicializan los atributos de la clase, para lo cual podemos pasar parámetros.

Además, vamos a emplear el término reservado **self** para indicar aquellos atributos y métodos que van a ser propios de la instancia. Veámoslo con un ejemplo.

---

## Init (constructor) y Self 
### Ejemplo Clase Persona
```python
class Persona():
    def __init__(self, nombre, apellido, edad, contacto):
        # Este método puede tomar parámetros que asignamos a los atributos, que luego podemos acceder
        self.edad = edad # este es un atributo
        self.contacto = contacto # este es otro atributo
        self.nombre = nombre
        self.apellido = apellido
        
    def nombre_completo(self):
        # este método muestra el nombre completo a partir del nombre y apellido
        nombre_completo = ', '.join([self.apellido,self.nombre])
        return nombre_completo

    def saludar(self):
        print(f'Hola mi nombre es {self.nombre_completo()}',
              f'y te dejo mi mail por si necesitás algo: {self.contacto}')
```

```python
instancia_ejemplo = Persona('Matías Andrés','Ripley', 24, 'mati@rip.com')
instancia_ejemplo.saludar()
```
$$Consola$$
![[Pasted image 20230820224745.png]]

### Ejercicio Menú pasándole una lista 
Ahora veamos una clase menú que administra los platos y los precios


```python
class Menu():
    def __init__(self, items):
        self.items = items

    def precio(self, lista_items):
        precio = 0
        for nombre_item in lista_items:
            precio = precio + self.items[nombre_item]
        return precio

    def tamaño(self):
        return len(self.items)
```



```python
mi_menu = Menu({'latte':25, 'medialuna':15})
```

¿Cuánto salen un latte y dos madialunas? ¿Cuántos ítems tenemos?


```python
mi_menu.precio(['latte','medialuna','medialuna'])
```
$$Consola$$
![[Pasted image 20230820225135.png|300]]





```python
mi_menu.tamaño()
```
$$Consola$$
![[Pasted image 20230820225204.png|170]]

___
### Ejercicio Menú pasándole una lista de diccionarios 

![](https://youtu.be/1PfQLOCpp_Y?t=615)

Ejercicio: Vamos a mejorar la clase anterior... En lugar de que el método precio reciba una lista de strings, hagamos que reciba una lista de diccionarios cada uno con dos claves nombre y cantidad que querríamos ordenar ¿Cuántos cuestan 10 lattes y 30 medialunas?

```python
class Menu():
	def __init__(self, items):
		self.items = items

	def precio(self, lista_items):
		precio_total = 0
		for items_pedido in lista_items:
			nombre_producto = item_pedido["nombre"]
			precio_producto = self.items[nombre_producto]
			cantidad = item_pedido["cantidad"]
			precio_total = precio_total + precio_producto * cantidad
		return precio_total

	def tamaño(self):
		return len(self.items)
```

```python
mi_menu = Menu({"latte":25, "medialuna":15})
```


```python
mi_menu.precio([{"nombre":"latte",     "cantidad":10},
			    {"nombre":"medialuna", "cantidad":30}])
```
$$Consola$$
![[Pasted image 20230820232219.png]]

___
### Ejercicio Curso , Variables de clase

![](https://youtu.be/1PfQLOCpp_Y?t=788)

Los atributos también son conocidos como variables de instancia, en contraposición a las variables de clase. Las variables de instancia toman un valor específico a una instancia en particular (por eso se emplea el término **self**), por su parte, las variables de clase tienen un valor común para todas las instancias de una clase. Por convención las variables de clase se definen antes del constructor y no llevan **self** en su definición pero sí cuando se la quiere llamar.

#### Clase curso
```python
class Curso:
    max_alumnos = 35 # definimos variable de clase
  
    def __init__(self, nombre, duracion, alumnos = None, costo=10):
        self.nombre = nombre
        self.duracion = duracion
        if alumnos is None:
            self.alumnos = []
        else:
            self.alumnos = alumnos
        self.costo = costo # costo tiene un valor por default
        """¿Por qué ese if? Las variables por default sólo se evalúan a la hora de ejecutar la sentencia def.
        En nuestro caso necesitamos que self.alumnos sea una lista y las listas son objetos mutables.
        Esto quiere decir que podemos modificarla sin volver a asignarla. Si en vez de 'alumnos = None' usáramos
        alumnos = [], entonces con cada nueva instancia del objeto estaríamos compartiendo los alumnos.
        Para evitar eso, en general la forma pythónica de hacerlo es usando None por default y asignando el valor
        deseado dentro de la función y no en el 'def' """

    def inscribir_alumno(self, nombre):
        self.alumnos.append(nombre) # para poder llamar a alumnos tengo que usar self.
        print(f'Se agregó al alumno/a {nombre}')

    def tomar_lista(self):
        for a in self.alumnos:
            print(f'Alumno: {a}')

    def resumen(self):
        print(f'Curso {self.nombre}, {self.duracion} clases pensadas para {len(self.alumnos)} alumnos\n'
              f'Por el muy módico precio de {self.costo} rupias.',
              # llamo variable de clase:
              f'La ocupación actual es del {round(len(self.alumnos)/self.max_alumnos,2)*100}%')
```


```python
curso_python = Curso('Python', 6)
```


```python
curso_python.alumnos
```
$$Consola$$
![[Pasted image 20230822182127.png]]

```python
# Llamamos metodos de la instancia
curso_python.inscribir_alumno('Diotimia')
curso_python.inscribir_alumno('Aritófanes')
```
$$Consola$$
![[Pasted image 20230822182215.png]]

```python
curso_python.tomar_lista()
```
$$Consola$$
![[Pasted image 20230822182328.png]]



```python
curso_python.resumen()
```
$$Consola$$
![[Pasted image 20230822182351.png]]

```python
curso_ml = Curso('Machine Learning', 8)
```

```python
curso_ml.alumnos # vean que el curso está vacío!
```
$$Consola$$
![[Pasted image 20230822182509.png]]


```python
curso_ml = Curso('Machine Learning', 8)
curso_ml.inscribir_alumno('Agatón')
curso_ml.inscribir_alumno('Erixímaco')
curso_ml.inscribir_alumno('Sócrates')
```
$$Consola$$
![[Pasted image 20230822182547.png]]


```python
curso_ml.resumen()
```
$$Consola$$
![[Pasted image 20230822182624.png]]

```python
curso_ml.alumnos
```
![[Pasted image 20230822182706.png]]


### Ejercicio :

1- Defina una clase Punto que tome como parámetros x e y (las coordenadas) y constante que se puede instanciar correctamente.

2- En Python existen los llamados _**métodos mágicos**_ (magic methods) o dunder (Double Underscores). Estos métodos se caracterizan, justamente, por comenzar y terminar con " __ " . Uno de los más comunes es el que permite darle estilo a la función **print**. Para que nuestro objeto entonces tenga un lindo print tenemos que definir una función  " __str__ " que sólo toma "self" como parámetro y que torne un string. Eso que retorna es el string que queremos que muestra cuando hagamos "print" del objeto. Dicho esto, te invitamos a que lo intentes de la siguiente manera:

a. Definí una función "__str__" que sólo toma self como parámetro.

b. La función debe retornar el string que quieres mostrar, recuerda que puedes usar los valores de "x" y de "y"


```python
class Punto:
    def __init__(self,x,y):
        self.x = x
        self.y = y
```

```python
print(Punto(3,7))
```
$$Consola$$
![[Pasted image 20230822184943.png]]

```python
class Punto:
    def __init__(self,x,y):
        self.x = x
        self.y = y

    def __str__(self):
        return f"({self.x},{self.y})"
```

```python
print(Punto(3,7))
```
$$Consola$$
![[Pasted image 20230822185212.png]]

___
## Herencia
![](https://youtu.be/1PfQLOCpp_Y?t=1275)

La herencia se emplea cuando queremos que una clase tome los atributos y características de otra clase. En este caso, la clase derivada (Alumno) **hereda** atributos y métodos de la clase base (Persona). Para acceder a los métodos de la clase previa vamos a emplear el método reservado **super()**. Con este método podemos invocar el constructor y así acceder a los atributos de esa clase.

### Clase Padre
```
Usamos la Clase Persona que creamos antes como padre de Alumno
```

### Clase hija
```python
# Clase derivada
class Alumno(Persona):
	#Con curso:Curso estamos especificando que queremos recibir un objeto de la clase Curso, no un string o cualquier otro tipo
    def __init__(self, curso: Curso, *args):
        """
        Alumno pertence a un Curso (una instancia de la clase Curso) y, además, tiene otros atributos que pasaremos
        a la clase previa
        """
        self.curso = curso
        super().__init__(*args) # inicializamos la clase 'Padre'. La llamamos usando super() y ejecutamos el constructor
        # Nótese también que desempacamos args
  
    def saludar(self): # Sobrecarga de métodos, ver abajo
        super().saludar() # ejecutamos el método de Persona .saludar() y agregamos más cosas a este método
        print('Estoy cursando:')
        self.curso.resumen()

    def estudiar(self, dato): # También podemos definir nuevos métodos
        self.conocimiento = dato
        
    def __str__(self):
        #Devuelve un string representativo del alumno
        return f'Alumno {self.nombre_completo()}'
```

La clase Persona cuenta con un método saludar() y para Alumno también definimos un método saludar(). Cuando instanciemos un Alumno y ejecutemos el método saludar() lo que va a ejecutarse es el método saludar() de Alumno, no de Persona. Esto no quita que el método saludar() de Alumno llame al de Persona. Además, vale la pena mencionar que los dos tienen los mismos parámetros (ninguno en este caso). Este patrón de diseño es lo que se llama sobrecarga de métodos o overriding.

```python
scott = Alumno(curso_python, 'Scott', 'Henderson', 49, 'sh@mail.com')
scott.saludar()
```
$$Consola$$
![[Pasted image 20230822191159.png]]

```python
scott.estudiar('Se puede heredar de otra clase y extender sus métodos')
```

```python
scott.conocimiento
```
$$Consola$$
![[Pasted image 20230822191310.png]]

Listar todos los métodos y atributos la instancia scott
```python
print(dir(scott))
```
![[Pasted image 20230822193305.png]]


___
## Protección de acceso
![](https://youtu.be/1PfQLOCpp_Y?t=1883)

___
Podemos cambiar el acceso (publico, no publico, protegido) de los métodos y variables.

---

Dos formas distintas de encapsulamiento:

- `_nopublico`
- `__protegido`

Los atributos o método no públicos pueden ser accedidos desde el objeto y llevan el prefijo "_". La utilidad de este es indicarle al usuario que es una variable o método privado, de uso interno en el código de la clase y que no está pensando que sea usado desde afuera, por el usuario.

Por otra parte, en el caso de usar como prefijo "$\_\_$" (doble "\_") directamente vamos a ocultar la variable o método de la lista de sugerencias para el usuario y tampoco va a poder invocarlo desde el objeto. Por este motivo, decimos que el atributo o método está protegido.

##### Clase auto con atributos privados y método protected

```python
class Auto():
  
    def __init__(self, color, marca, velocidad_maxima):
        self.color = color
        self.marca = marca
        self.__velocidad_maxima = 200
        self.velocidad = 0
        self.__contador = 0 # kilometros recorridos
    def avanzar(self, horas=1, velocidad=10):
        if self._chequear_velocidad(velocidad):
            self.velocidad = velocidad
            print(f'avanzando durante {horas} horas')
            self.__contador += horas*self.velocidad
        else:
            print(f"Tu auto no puede llegar a tanta velocidad, el máximo es {self.__velocidad_maxima}")
    def _chequear_velocidad(self, velocidad):
        es_valida = False
        if velocidad < self.__velocidad_maxima:
            es_valida = True
            if self.velocidad < velocidad:
                print("Vas a acelerar!")
            else:
                print("Vas a desaceler!")
        else:
            print("Tu motor no permite ir tan rápido")
            es_valida = False
        return es_valida
    def status(self):
        print(f"Vas a una velocidad de {self.velocidad} y llevás {self.__contador} km. recorridos")
```

##### Creamos una instancia de auto
```python
superauto = Auto('rojo','Ferraudi', 200)
```


##### Accedemos a un método de la instancia creada que contiene un método protected y un atributo privado
```python
superauto.avanzar(10)
```
$$Consola$$
![[Pasted image 20230824122202.png]]


##### Accedemos a otro método del objeto que también accede a un atributo privado
```python
superauto.status()
```
$$Consola$$
![[Pasted image 20230824122252.png]]

##### No podemos acceder a un atributo privado (protegido) directamente
```python
superauto.__contador
```
$$Consola$$
![[Pasted image 20230824122343.png]]

##### Pero si podemos acceder a un método protected ( no publico)
```python
superauto._chequear_velocidad(10)
```
$$Consola$$
![[Pasted image 20230824122426.png]]

___
### Ejercicio Clase  Punto  y Linea

A continuación se define una clase Linea. Esta clase toma como parámetros dos objetos Punto() (instancias de la clase que definieron antes).

1- Agregar un método 'largo' que permita calcular el largo de la línea. Para ello vale la pena recordar que ésta se puede calcular como la hipotenusa del triángulo rectángulo que se forma con los dos puntos.

$$ a = \sqrt{b^2 + c^2} $$

2- Agregar un método 'pendiente' que permita calcular la pendiente de la línea. Recordar que ésta se puede calcular como el cociente entre las diferencias de 'y' y de 'x'.
$$m = (y_2 - y_1)/(x_2 - x_1)$$


1. Creamos la clase **Punto**
```python
import numpy as np

class Punto:
    def __init__(self,x,y):
        self.x = x
        self.y = y
```

2. Creamos la clase **Linea** con sus métodos _largo_ y _pendiente_
```python
class Linea():
    def __init__(self, p1:Punto, p2:Punto):
        self.p1 = p1
        self.p2 = p2
  
    def largo(self):
        largo = ((self.p1.x-self.p2.x)**2+(self.p1.y-self.p2.y)**2)**0.5
        return largo 
        
    def pendiente(self):
        pendiente = (self.p1.y-self.p2.y)/(self.p1.x-self.p2.x)
        return pendiente
```

3. Creamos 2 instancias de **Punto**
```python
p1 = Punto(4,1)
p2 = Punto(7,5)
```

4. Creamos una instancia de **Linea**
```python
l = Linea(p1,p2)
```

5. Llamamos al método largo de la instancia l
```python
l.largo()
```
$$Consola$$
![[Pasted image 20230824125334.png]]

6. Llamamos al método pendiente de la instancia l
```python
l.pendiente()
```
$$Consola$$
![[Pasted image 20230824130056.png]]

___
## Métodos especiales
___
![](https://youtu.be/1PfQLOCpp_Y?si=eYGxGWmX92DjGGC5&t=2576)

___
Las clases en Python cuentan con múltiples métodos especiales, los cuales se encuentran entre dobles guiones bajos ().

Los métodos especiales más utilizados son **__init__(), __str__() y __del__()** .

__init__ sirve para inicializar la clase y __del__ sirve para eliminar completamente el objeto del compilador.

Veamos un ejemplo de uso de __str__. Una vez que definimos este método, responde a la sintaxis reservada de Python str().

```python
# Clase derivada
class Alumno(Persona):
    def __init__(self, curso: Curso, *args):
        """
        Alumno pertence a un Curso (una instancia de la clase Curso) y, además, tiene otros atributos que pasaremos
        a la clase previa
        """
        self.curso = curso
        super().__init__(*args) # inicializamos la clase 'madre'. La llamamos usando super() y ejecutamos el constructor
        # Nótese también que desempacamos args
    def saludar(self): # Sobrecarga de métodos, ver abajo
        super().saludar() # ejecutamos el método de Persona .saludar() y agregamos más cosas a este método
        print('Estoy cursando:')
        self.curso.resumen()
    def estudiar(self, dato): # También podemos definir nuevos métodos
        self.conocimiento = dato
    def __str__(self):
        #Devuelve un string representativo del alumno
        return f'Alumno {self.nombre_completo()}'
```

```python
un_alumno = Alumno(curso_python, 'Scott', 'Henderson', 49, 'sh@mail.com')
```

```python
str(un_alumno)
```
$$Consola$$
![[Pasted image 20230824132115.png]]
___
## Métodos Estáticos
¿Qué pasa si no queremos instanciar los objetos a la hora de usarlos? En algunos diseños, tiene sentido utilizar las clases como simples repositorios de métodos. Por ejemplo, si necesito resolver varias operaciones geométricas puedo crear una clase Geometria que contenga todos los métodos necesarios.

Para crear este tipo de métodos en una clase utilizamos el decorador _@staticmethod_.

```python
import math

class Geomtria():
    """Resuelve operaciones geométricas"""
    
    @staticmethod
    def pendiente(x1,y1,x2,y2):
        return ((y2 - y1)/(x2-x1))
        
    @staticmethod
    def area_circulo(radio):
        return math.pi * (radio**2)
```

```python
Geomtria.area_circulo(3)
```
$$Consola$$
![[Pasted image 20230824132306.png]]

___
## Duck typing y monkey patching
Dos características de la programación orientada a objetos con Python son el duck tiping y el monkey patching. Este tipo de flexibilidad es el que le permitió a Python crecer tanto en su adopción porque reducen la cantidad de palabras que es necesario escribir para desarrollar código, lo cual ahorra tiempo y también disminuyen la complejidad.
___
### Duck typing
```python
class ElHobbit:
    def __init__(self,nombre):
        self.nombre = nombre

    def __len__(self):
        return 95022

    def saludar(self):
        return f'Hola soy {self.nombre}'

el_hobbit = ElHobbit('Frodo')
```

```python
len(el_hobbit)
```
$$Consola$$
![[Pasted image 20230824132522.png]]

```python
mi_str = "Hello World"
mi_list = [34, 54, 65, 78]
mi_dict = {"a": 123, "b": 456, "c": 789}
```

_If it walks like a duck, and it quacks like a duck, then it must be a duck.”_

Duck typing significa que a diferencia de otros lenguajes, las funciones especiales no están definidas para una lista específica de clases y tipos, si no que se pueden usar para cualquier objeto que las implemente. Esto no es así para la mayoría de los lenguajes.

```python
len(mi_str)
len(mi_list)
len(mi_dict)
len(el_hobbit)
```
$$Consola$$
![[Pasted image 20230824132734.png]]

```python
mi_int = 7
mi_float = 42.3
```

```python
len(mi_int)
len(mi_float)
```
$$Consola$$
![[Pasted image 20230824132833.png]]

___
### Monkey Patching
Guerrilla, gorilla, ¿monkey?... Este término viene de uno anterior, "guerrilla patching", que hace referencia a emparchar el código rápido y cuando es necesario.

Se refiere a la posibilidad en Python de sobrescribir clases después de haberlas instanciado y por qué no también la funcionalidad de los módulos.

```python
el_hobbit.saludar()
```
$$Consola$$
![[Pasted image 20230824133020.png]]

```python
def saludo_largo(self):
    return f'Hola mi nombre es {self.nombre}'
```

```python
ElHobbit.saludar = saludo_largo
```

```python
el_hobbit.saludar()
```
$$Consola$$
![[Pasted image 20230824133105.png]]

Esto es especialmente útil cuando queremos sobre-escribir ligeramente módulos hechos por terceros (¡o por nosotros mismos en otro momento!)

```python
import math
```

```python
math.pi
```
$$Consola$$
![[Pasted image 20230824133213.png]]


```python
math.pi = 2
```

```python
math.pi
```
$$Consola$$
![[Pasted image 20230824133307.png]]

Los cambios se sobre-escriben si REINICIAMOS EL KERNEL y volvemos a importar el módulo

```python
import math
math.pi
```
$$Consola$$
![[Pasted image 20230824133213.png]]

___

%%
tags:  #programación #pagfundamentospython #python   #init #constructor #self #objeto #clase #def #monkey_patching #duck_typing #métodos_especiales #métodos_estaticos #clase_punto #clase_linea #protegido #no_publico #privado #protected #protegido #protección_de_acceso #herencia #padre #hijo 

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%