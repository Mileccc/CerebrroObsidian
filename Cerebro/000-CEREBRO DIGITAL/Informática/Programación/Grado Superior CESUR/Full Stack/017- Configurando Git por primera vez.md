---
ID: 17
nombre: Configurando Git por primera vez
tags:
  - pagfull_stack
---
___
Antes de comenzar a usar Git necesitamos indicar quienes somos, ya que cada interacción que realicemos con Git almacenará quien ha realizado dicha interacción además de otros muchos otros valores.

Para realizar esa configuración necesitamos usar dos comandos sustituyendo los valores con los propios de cada cual:


| Comando                                              | Acción                             |
|------------------------------------------------------|------------------------------------|
| `Git config --global user.name "Paco Gomez"`         | Configura el nombre del usuario    |
| `Git config --global user.email paco@repositoriocompartido.es` | Configura el email del usuario     |

Para comprobar la configuración que tenemos podemos usar el siguiente comando:


| Comando                 | Acción                                                |
|-------------------------|-------------------------------------------------------|
| `Git config --list`     | Muestra un listado de todos los parámetros de configuración |

___
%%
tags: #pagfull_stack #Git #Configuración #Comandos #Usuario #Email #Interacción #ListadoDeParámetros
Vínculos:  [[000-Menú Full Stack 📃|Menú Full Stack 📃]]
%%