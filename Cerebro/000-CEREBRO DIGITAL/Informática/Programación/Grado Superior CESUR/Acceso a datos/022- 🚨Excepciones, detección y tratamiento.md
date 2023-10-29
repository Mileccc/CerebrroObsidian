---
ID: 22
nombre: Excepciones, detección y tratamiento
tags:
  - pagacceso_a_datos
---
___
## 🛠️ Manejo de Excepciones en Java 🚨
[![](https://mermaid.ink/img/pako:eNp1Uztv2zAQ_isEpwRwDcnvaEtsB3ABA0UeS-HlQtLJpRSpUlRgxzDQsYORDlkKd3C6dSkKNEvR1T-o_gmlZEuujXQRdHffd9-9OKFMc0EDGqLiIUQDRYjR2h4crBZfnv78-kT6oMStJlyQ7oiJiKFWIiZCkddwB2S1mH87PExZhDjKww_SU9ZonjCGy2dFYIe1WswWGzAhHTFEhWvYNruzckAvjLSxoBiCA8iXKymkH-fkHJWFEcYp5MKMX7XBshsn-vi5EO3G1iTMJgbIyfJrjAzyyInU75OMt-fJshQys4_kNFGpNoQolNVZaVtyITp7KkSPr0Bxrfahebi9fOZ4rckbHVthUJvtOL-T_vK3tBhJN701Mya5wsPPQmE7mg4OhXF1OdwFRjr-37hcH5tKTlGBlOPdkru3giXr3fQUF5FQPO1WFPE7tGDImYvY7Q43nRQi8w-krVWMXBjYnECmtn8KZ_oqcb3fpzkkkONIusXs3EJHMAkGciWZNffy2VxalMiB_zvtTY-0RENhQkDuLn6SEgbU3ohQDGjgfjmYdwM6UFOHg8Tq87FiNHAHI0o0iThY0UG4NhDSYAgyLrxdjlabwikys79-V9nzKtEI1FutwzybM2kwoSMa-J5XrjYqfsWvtype1a_US3RMg2az3Kz4jVaz6j5HtXp1WqL3WQKv3GrUvFqt0fKb9ap31GxM_wKzq1M5?type=png)](https://mermaid.live/edit#pako:eNp1Uztv2zAQ_isEpwRwDcnvaEtsB3ABA0UeS-HlQtLJpRSpUlRgxzDQsYORDlkKd3C6dSkKNEvR1T-o_gmlZEuujXQRdHffd9-9OKFMc0EDGqLiIUQDRYjR2h4crBZfnv78-kT6oMStJlyQ7oiJiKFWIiZCkddwB2S1mH87PExZhDjKww_SU9ZonjCGy2dFYIe1WswWGzAhHTFEhWvYNruzckAvjLSxoBiCA8iXKymkH-fkHJWFEcYp5MKMX7XBshsn-vi5EO3G1iTMJgbIyfJrjAzyyInU75OMt-fJshQys4_kNFGpNoQolNVZaVtyITp7KkSPr0Bxrfahebi9fOZ4rckbHVthUJvtOL-T_vK3tBhJN701Mya5wsPPQmE7mg4OhXF1OdwFRjr-37hcH5tKTlGBlOPdkru3giXr3fQUF5FQPO1WFPE7tGDImYvY7Q43nRQi8w-krVWMXBjYnECmtn8KZ_oqcb3fpzkkkONIusXs3EJHMAkGciWZNffy2VxalMiB_zvtTY-0RENhQkDuLn6SEgbU3ohQDGjgfjmYdwM6UFOHg8Tq87FiNHAHI0o0iThY0UG4NhDSYAgyLrxdjlabwikys79-V9nzKtEI1FutwzybM2kwoSMa-J5XrjYqfsWvtype1a_US3RMg2az3Kz4jVaz6j5HtXp1WqL3WQKv3GrUvFqt0fKb9ap31GxM_wKzq1M5)

### 🎯 Introducción a Excepciones 🌟

Una excepción es un evento disruptivo que ocurre durante la ejecución de un programa, interrumpiendo el flujo normal de las instrucciones. Por ejemplo, un intento de división por cero generará una excepción. Es crucial manejar estas excepciones para evitar que el programa se detenga o funcione incorrectamente.

### 📚 Sintaxis de Try-Catch 📘

Para manejar excepciones en Java, se utiliza la construcción `try-catch`. La estructura básica es la siguiente:

```java
try {
  // Código que puede generar una excepción
} catch (tipo_Excepcion nombre_variable) {
  // Código que se ejecuta si se produce la excepción
}
```

#### 🌈 Funcionamiento del Bloque Try-Catch 🌠

- **Bloque Try**: Contiene el código que podría generar una excepción.
- **Bloque Catch**: Se ejecuta si se produce una excepción en el bloque `try`.

> **Nota**: El bloque `try` se abandona en el momento en que se produce una excepción, por lo que cualquier código posterior no se ejecutará.

### 🎭 Múltiples Bloques Catch 🎲

Un bloque `try` puede tener múltiples bloques `catch` para manejar diferentes tipos de excepciones.

```java
try {
  // Código que puede generar una excepción
} catch (nombre_Excepcion e) {
  // Código para manejar la excepción
} catch (nombre_Excepcion e1) {
  // Código para manejar otro tipo de excepción
}
```

### 🌈 Bloque Finally 🌠

El bloque `finally` se ejecuta independientemente de si se produce una excepción o no. Es útil para evitar la repetición de código en los bloques `try` o `catch`.

```java
try {
  // Código que puede generar una excepción
} catch (nombre_Excepcion e) {
  // Código para manejar la excepción
} finally {
  // Código que se ejecuta siempre
}
```

### Tipos de excepciones

![[000-CEREBRO DIGITAL/Informática/Programación/Grado Superior CESUR/Acceso a datos/ANEXOS/R.jpg|1400]]

![[Pasted image 20231014162747.png|900]]

### 🚀 Consideraciones Finales 🌟

- Siempre maneje excepciones para asegurar la robustez de su aplicación.
- Puede declarar el tipo de excepción que el bloque `catch` manejará mediante un objeto cuya clase es la clase de la excepción o una de sus superclases.
- El bloque `finally` es opcional pero útil para evitar la duplicación de código.

Espero que esta estructuración del texto te ayude a comprender mejor el manejo de excepciones en Java.

___
%%
tags: #java  #pagacceso_a_datos  #Java #Excepciones #TryCatch #BloqueTry #BloqueCatch #MúltiplesCatch #BloqueFinally #ConsideracionesFinales #RobustezAplicación #ManejoExcepciones #SintaxisTryCatch #FlujoNormalInstrucciones #EventoDisruptivo #CódigoEjecución #TipoExcepción #SuperclasesExcepción #DuplicaciónCódigo
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%