---
ID: 122
"tags:": 
"nombre:": Encapsulamiento
---
___
# Encapsulamiento
___
![](https://www.youtube.com/watch?v=5kMOFIOWKvs)

Crear
```python

class Cuenta:
	def __init__(self, nombre, direccion):
		self.nombre = nombre
		self.direccion = direccion
		self.__balance = 0.00 #Atributo privado(encapsulado)
```

Consultar un atributo privado saltándose el encapsulamiento
```python
print(cuenta._Cuenta__balance)
```

Utilizar atributos privados en métodos
```python
def retirar(self, monto)
	self.__balance -= monto
```

___

%%
tags:  #programación #pagfundamentospython #python  

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%