---
ID: 20
nombre: Ficheros de objetos. Serialización
tags:
  - pagacceso_a_datos
---
___

[![](https://mermaid.ink/img/pako:eNqNU0tu2zAQvQrBVQIYhix_o12Q2oWBpA5qdFN4MyYnCVuJVMlhEMfwYXqGHiEXy0iW5RpNgm4IzvDxzbx55FYqp1FmsjBWF1CurBDeOTo7mxn1gN4FoVG49Q8kF7piid5Abp5BmZc_9vy8ggtxlUPAIFDMLaG_A8XBNKBVjMWwxwixYBJFc1tGWpJHKMQsMsRZRj8aqqCZuEb0ItqmolCuKHPenHIsIn1IMg3Km7V5n-hURqVwsVd4qDOv0AVaahA3YCPk4iv-iiYYcpm4JC4R-YoIB7J1K_ZbcAKtuCxzo6Dp7ta__FbEcVvkM1r0xxZ4bhT98Xj6pLBsLlcTDl8czVy0uj4gPmimz9LAA5lHqGgaMzbHwbxvwKJsG7j1huEl5JUHdSN_Gf_B-N-mqB14k-TK2WB0fadWthHXpjAEp63-r_Z_nVLRaNAuwH4uxO8grzJcKOB99NVedmSBvgCj-eFvK6aVpAdmWcmMtxr8z5Vc2R3jgC1ebqySGfmIHRlLDYSfDNx7KGR2B3los1PNL8O3SazDm_33qn9ZR5ZgvztXHNg4lNlWPsmslyTd_ijtpb3hJE36vXTYkRuZjcfdcdobTcZ9Xi4Gw_6uI59rgqQ7GQ2SwWA0TIbj5GKS9nevXFNSlQ?type=png)](https://mermaid.live/edit#pako:eNqNU0tu2zAQvQrBVQIYhix_o12Q2oWBpA5qdFN4MyYnCVuJVMlhEMfwYXqGHiEXy0iW5RpNgm4IzvDxzbx55FYqp1FmsjBWF1CurBDeOTo7mxn1gN4FoVG49Q8kF7piid5Abp5BmZc_9vy8ggtxlUPAIFDMLaG_A8XBNKBVjMWwxwixYBJFc1tGWpJHKMQsMsRZRj8aqqCZuEb0ItqmolCuKHPenHIsIn1IMg3Km7V5n-hURqVwsVd4qDOv0AVaahA3YCPk4iv-iiYYcpm4JC4R-YoIB7J1K_ZbcAKtuCxzo6Dp7ta__FbEcVvkM1r0xxZ4bhT98Xj6pLBsLlcTDl8czVy0uj4gPmimz9LAA5lHqGgaMzbHwbxvwKJsG7j1huEl5JUHdSN_Gf_B-N-mqB14k-TK2WB0fadWthHXpjAEp63-r_Z_nVLRaNAuwH4uxO8grzJcKOB99NVedmSBvgCj-eFvK6aVpAdmWcmMtxr8z5Vc2R3jgC1ebqySGfmIHRlLDYSfDNx7KGR2B3los1PNL8O3SazDm_33qn9ZR5ZgvztXHNg4lNlWPsmslyTd_ijtpb3hJE36vXTYkRuZjcfdcdobTcZ9Xi4Gw_6uI59rgqQ7GQ2SwWA0TIbj5GKS9nevXFNSlQ)
### 🛠️ Clases e Interfaces Esenciales 🧰

La administración de ficheros de objetos en programación se logra principalmente a través de las clases `ObjectInputStream` y `ObjectOutputStream`. Estas implementan las interfaces `ObjectInput` y `ObjectOutput`, que son subinterfaces de `DataInput` y `DataOutput`.

#### 📄 ObjectInputStream

- Encargada de la lectura de objetos desde un archivo.
- ***Funciones vitales***: Leer un objeto completo de un archivo sin necesidad de descomponerlo en atributos.

#### 🖋️ ObjectOutputStream

- Facilita la escritura de objetos en un archivo.
- ***Funciones vitales***: Permite escribir un objeto completo de una sola vez, sin tener que guardar sus atributos de forma individual.

### 📚 Serialización de Objetos 📘

La serialización de objetos es un mecanismo que permite guardar un objeto completo en un archivo. Este proceso facilita la escritura y posterior lectura del objeto _como un flujo de bytes_, sin tener que descomponer sus atributos individualmente. Es posible serializar tanto clases estándar como clases definidas por el usuario.

- ***Implementación Manual***: Para serializar una clase definida por el usuario, es necesario que esta implemente la interfaz `Serializable`. 
    - *Requisito*: Todos los atributos de la clase deben ser serializables.

### 🚀 Uso en Aplicaciones Prácticas 🌟
 
Es común utilizar la serialización en aplicaciones como la generación de facturas, donde se emplean objetos `BigDecimal` para los precios y objetos `Calendar` para las fechas. Si el objeto leído no es del tipo esperado, se podría lanzar una excepción `ClassNotFoundException`, la cual debe ser manejada adecuadamente.

### 📊 Comparativa de Clases y Funciones 📈

| Clase                 | Operación Principal             |
|-----------------------|---------------------------------|
| ``ObjectInputStream`` | Lectura de objetos              |
| ``ObjectOutputStream``| Escritura de objetos            |

### 🚨 Consideraciones y Limitaciones 🛑

Es esencial manejar excepciones como `ClassNotFoundException` para asegurar la robustez de la aplicación. La serialización es una técnica potente pero también requiere una implementación cuidadosa para evitar problemas relacionados con la compatibilidad y la seguridad.

***Nota***: Las clases de serialización ofrecen un abanico de funciones más allá de simples lecturas y escrituras, proporcionando una manera eficiente de manejar objetos.

Espero que esta información sea de utilidad para entender la gestión de ficheros de objetos y la serialización en programación.

___
%%
tags: #pagacceso_a_datos  #GestiónDeFicheros #Objetos #Serialización #Programación #ObjectInputStream #ObjectOutputStream #ObjectInput #ObjectOutput #DataInput #DataOutput #FuncionesVitales #ImplementaciónManual #Serializable #AplicacionesPrácticas #Excepciones #ClassNotFoundException #ComparativaDeClases #Consideraciones #Limitaciones #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%