---
ID: 19
nombre: Ficheros binarios
tags:
  - pagacceso_a_datos
---
___
[![](https://mermaid.ink/img/pako:eNqNUstu2zAQ_JUFTwkgGHpZVnRLm0cLJEgBoz0UumzIbbKISAokFcQ1_DE99tBTP8E_VkqqHRS95ELszi5nhrvcCmkViUZoNkpj3xoAZ204Obli-UjOenjHBh1bf3o6FgE-kHOomUxAD5eejGTsyM9FgCvu6KPph7AOjlDDZkLuhnCEDp0At_ufwSoLiuBcSvK2gTXJYaZ8bbvryaHk_W8DnxzHYo9dAzckw-AwCjwM6BTOPPeb8OrlAgP-62VE3uzlC7r9L3y7D_LS8RRHEoUhDq93rDnws_3r6WZMI4c15OON99Z4VhPriBykPns73pwVdJw0gf9vLteoEfT-hwfUfceTqJ4fEXUxutBouB86dLMZkQhNTiOruO_tSNOK8EiaWtHEUKF7akVrdrEPh2DXGyNFE9xAiRj6yEAXjA9x9aL5hp0_opeKg3VHkKb0dv5V0-dKRI_mq7X6wBZT0WzFi2iyNF0UVZ7l2bLO0yLLl4nYiGa1WqzyrKpXRTzOymWxS8T3iSBd1FWZlmVV1XmdFmVxtvsDeOntjw?type=png)](https://mermaid.live/edit#pako:eNqNUstu2zAQ_JUFTwkgGHpZVnRLm0cLJEgBoz0UumzIbbKISAokFcQ1_DE99tBTP8E_VkqqHRS95ELszi5nhrvcCmkViUZoNkpj3xoAZ204Obli-UjOenjHBh1bf3o6FgE-kHOomUxAD5eejGTsyM9FgCvu6KPph7AOjlDDZkLuhnCEDp0At_ufwSoLiuBcSvK2gTXJYaZ8bbvryaHk_W8DnxzHYo9dAzckw-AwCjwM6BTOPPeb8OrlAgP-62VE3uzlC7r9L3y7D_LS8RRHEoUhDq93rDnws_3r6WZMI4c15OON99Z4VhPriBykPns73pwVdJw0gf9vLteoEfT-hwfUfceTqJ4fEXUxutBouB86dLMZkQhNTiOruO_tSNOK8EiaWtHEUKF7akVrdrEPh2DXGyNFE9xAiRj6yEAXjA9x9aL5hp0_opeKg3VHkKb0dv5V0-dKRI_mq7X6wBZT0WzFi2iyNF0UVZ7l2bLO0yLLl4nYiGa1WqzyrKpXRTzOymWxS8T3iSBd1FWZlmVV1XmdFmVxtvsDeOntjw)
### 🧰 Herramientas Esenciales 🛠️

En la gestión de ficheros binarios, hay varias clases clave que simplifican el proceso:

1. ``FileInputStream``: Encargada de leer bytes de manera secuencial en un fichero.
   - Método de Acceso: Secuencial
   - Operación Principal: Lectura de bytes

2. ``FileOutputStream``: Especializada en la escritura de bytes de manera secuencial.
   - Método de Acceso: Secuencial
   - Operación Principal: Escritura de bytes

3. ``DataInputStream`` y ``DataOutputStream``: Estas clases van más allá y permiten la lectura y escritura de datos primitivos, como enteros y flotantes.
   - Método de Acceso: Varía
   - Operación Principal: Lectura y escritura de datos primitivos

#### 📊 Comparación de Clases 

| Clase                 | Método de Acceso | Operación Principal             |
|-----------------------|------------------|---------------------------------|
| ``FileInputStream``   | Secuencial       | Lectura de bytes                |
| ``FileOutputStream``  | Secuencial       | Escritura de bytes              |
| ``DataInputStream``   | Varía            | Lectura de datos primitivos     |
| ``DataOutputStream``  | Varía            | Escritura de datos primitivos   |

### 🎓 Funcionalidades y Uso 📘

#### 📖 FileInputStream

- Su función primordial es la lectura de bytes de un fichero de forma secuencial.
- ***Uso típico***: Ideal para escenarios donde se necesita leer información binaria de un fichero.

#### 📝 FileOutputStream

- Su especialidad es escribir bytes en un fichero, también de forma secuencial.
- ***Uso típico***: Usado cuando se desea guardar información binaria.

#### 🖊️ DataInputStream y DataOutputStream

- Estas clases permiten una gran cantidad de operaciones, incluidas la lectura y escritura de datos primitivos como enteros y flotantes.
- ***Uso típico***: Útiles en escenarios donde se necesita más que solo bytes, como el manejo de tipos de datos primitivos.

### 🎭 Limitaciones y Consideraciones 🚨

Es crucial entender que aunque estas clases son potentes para el manejo de ficheros binarios, su uso es principalmente secuencial. Esto podría ser una restricción en contextos que requieren más flexibilidad en el acceso a los datos.

***Nota***: Aunque cuentan con métodos como ``read()`` y ``write()``, estas clases ofrecen una gama más amplia de métodos para manipular datos de manera eficiente.

___
%%
tags: #pagacceso_a_datos  #FicherosBinarios #Programación #FileInputStream #FileOutputStream #DataInputStream #DataOutputStream #MétodoDeAcceso #OperaciónPrincipal #Funcionalidades #Uso #Limitaciones #Consideraciones #ManejoDeFicheros #Bytes #DatosPrimitivos #Lectura #Escritura #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%