---
ID: 121
"tags:": "#programación #pagfundamentospython #python  #pagpython #str"
"nombre:": Repaso POO
---
___
# Repaso POO
___
## Programación orientada a objetos

En este ejercicio vamos a programar un carrito de compras.

Para esto vamos a escribir dos clases: Carrito e Item.

El **ítem** va a tener como propiedades un _nombre_, un _precio_ y una _url_ de la imagen que lo representa. Por default, la url se inicializa en blanco.

El **Carrito** tiene como propiedad una _lista de diccionarios_, la variable _lineas.

Los carritos se inicializan vacíos y luego se agregan líneas utilizando el método _agregar_línea()_. Cada línea es un diccionario con dos claves: _"ítem"_ que contiene un objeto de tipo ítem y _"cantidad"_ según la cantidad que queremos agregar al carrito.

Por último los carritos tienen un método _calcular_total()_ que devuelve la suma de los precios de los ítems, multiplicados por las cantidades que hay en cada línea.

### Crear clase Item

```python
class Item():
    def __init__(self,nombre, precio,url=""):
        self.nombre=nombre
        self.precio=precio
        self.url=url
  
    def __str__(self):
        return f"Soy un/a {self.nombre}"

	def __repr__(self): #__repr__ es parecido a al toString pero para que colab devuelva el texto al poner solo en nombre de la instancia en una celda en colab
        return f"{self.nombre.title()}"
```

#### Creamos 2 instancias de ítems
```python
banana = Item("banana",49.5)
yoghurt = Item("yoghurt",32.5)
```

### Creamos la clase Carrito
```python
class Carrito():
    def __init__(self):
        self.lista_de_compras=[]
    def agregar_linea(self,linea:dict):
	    assert "item" in linea.keys(), "No tiene item!"
	    assert "cantidad" in linea.keys(), "No tiene cantidad!"
        self.lista_de_compras.append(linea)
  
    def calcular_total(self):
        return sum([n["Item"].precio * n["cantidad"] for n in self.lista_de_compras])

	def __getitem__(self, idx):
		return self.lista_de_compras[idx] #__getitem__se usa para que la instancia se considere como iterable
```

#### Instanciamos un carrito
```python
carrito = Carrito()
```


#### Agregamos 2 lineas al carrito
```python
carrito.agregar_linea({"Item":banana,"cantidad":3})
carrito.agregar_linea({"Item":yoghurt,"cantidad":5})
```

#### Calculamos el precio total del carrito
```python
carrito.calcular_total()
```
$$Consola$$
![[Pasted image 20230901111555.png]]


___

%%
tags:  #programación #pagfundamentospython #python  #pagpython #str #assert

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%