---
ID:: 070
tags::  #pagprogramacion #sql #pagsql #normalización #primera_forma_normal #segunda_forma_normal
nombre:: "Normalización"
---

___
# Normalización
![](https://youtu.be/md5qdEsRkXo?t=2079)

___
## Introducción a la normalización

Entender y cementar todos los conocimientos y prácticas relacionados a la normalización de una base de datos escapa al alcance del curso.

De todas formas ésta pretende ser una breve introducción al tema para entender las buenas prácticas y las convenciones que hacen a la correcta administración de las bases de datos y las tablas que viven en ella.

En términos concretos la normalización se entiende como una técnica de organización de datos en una base que consiste en descomponer las tablas para eliminar la redundancia. Es un proceso de múltiples pasos para llevar la data a una forma tabular, eliminando duplicación en las tablas relacionales.

Si no prestamos atención a la normalización podemos caer rápidamente en una situación en la que la base se vuelve lenta, poco performante y es vulnerable a la inconsistencia de los datos.

La normalización es un proceso en constante desarrollo a la que se suman nuevas prácticas constantemente. Por tanto, nos vamos a enfocar en las llamadas "primeras dos formas de normalización".

### 1NF - First Normal Form o Primera forma normal:

Para 'cumplir' con la primera forma normal se deben:

- Remover grupos repetidos de las tablas y registros con multiples valores.
- Crear tablas separadas por cada grupo de data relacionada
- Identificar los distintos grupos de datos relacionados mediante primary keys.

Ejemplo:

![1nf](https://drive.google.com/uc?id=1M8jL2lreS0zSSSyK-5dGhaEITA3qi2aB) ![1nf2](https://drive.google.com/uc?id=19WTmJXm4CUKZa7SkClPlVvJc0Z7A-YYX)

### 2NF - Second Normal Form o Segunda forma normal:

Para acatar con la segunda forma normal debemos:

- Cumplir con la primera forma
- Asegurarnos que no exista dependencia parcial

Ejemplo:

![2nf1](https://drive.google.com/uc?id=1N4-aDF9me83Khum2HkBsUFd62oseZiaT) ![2nf2](https://drive.google.com/uc?id=1xwiORvH2-9Oz1Uw-xt-sL_Jd4hWetyQo)

___
%%
tags: #pagprogramacion #sql #pagsql #normalización #primera_forma_normal #segunda_forma_normal

Vínculos:  [[000-Menú SQL 📃|Menú SQL]]   
%%