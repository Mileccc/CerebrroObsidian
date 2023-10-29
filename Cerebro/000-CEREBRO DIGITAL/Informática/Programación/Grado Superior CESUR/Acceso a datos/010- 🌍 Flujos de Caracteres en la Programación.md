---
ID: 10
nombre: Flujos de Caracteres en la Programación
tags:
  - pagacceso_a_datos
---
___
[![](https://mermaid.ink/img/pako:eNptU8tu2zAQ_JUFTwpgBLIV24lurZOgDWqgSBEUKHxZk5uELkWqFBnEMfIjveXYQ0_5BP9YV7Rk93URxOFwODu73AjpFIlSVNqqCuuFBfDOhSy7NHHlGlAEM_QoA3lqgCwYhI_e3XmsUOrtqz06as8AZO9t8E5FmVBA-J9AxwU4x8B71kEdWYlsIFhqi167pqfMnF1FG1yrIA8WbqxuLe9YRzODDYNruCKP_lvc_sTW5BU-YNYLZdeEivz-boBLbWgH7jmfvQ7_cHZgV99N0EY_7YrmCy9WVNUmuZttX5W-c_vDM0_oQdsmoJUae7g_0fmDmosCQ-Qhcl5e3usH9zeX1ZdRGurJMnBenaFrko6jU2zJ2RTC20gWG-7P9kUGLfGQ9we9bAMCTzL65hDyfPsjOOVAGtd0mWZvasNnl1ytQgXcVvI23YHmUCLWDLX7yViFllYs_0dzALbfOTN2ljiYZDuv-ndV6uxk3HJpYpPGqtd4R54nRPOIcGKs7V2zT3SOVtfRdD2hWy11GiVOrcszzV-gx-DEQFTkK9SKp33TKixEuKeKFqLkX4X-60Is7DPzMAb3aW2lKIOPNBCxVhjoXGM79aK8RdPs0Qulg_N7kNJyvntT6WkNRI32i3NVr8ZLUW7EoyjH-XFxepbnxXRcTCaj4XAg1qIc5sVxUUxPJvzh3clo_DwQT0lgeJzn09HkbDI-KU6L8Wk-ev4FPQg_Fg?type=png)](https://mermaid.live/edit#pako:eNptU8tu2zAQ_JUFTwpgBLIV24lurZOgDWqgSBEUKHxZk5uELkWqFBnEMfIjveXYQ0_5BP9YV7Rk93URxOFwODu73AjpFIlSVNqqCuuFBfDOhSy7NHHlGlAEM_QoA3lqgCwYhI_e3XmsUOrtqz06as8AZO9t8E5FmVBA-J9AxwU4x8B71kEdWYlsIFhqi167pqfMnF1FG1yrIA8WbqxuLe9YRzODDYNruCKP_lvc_sTW5BU-YNYLZdeEivz-boBLbWgH7jmfvQ7_cHZgV99N0EY_7YrmCy9WVNUmuZttX5W-c_vDM0_oQdsmoJUae7g_0fmDmosCQ-Qhcl5e3usH9zeX1ZdRGurJMnBenaFrko6jU2zJ2RTC20gWG-7P9kUGLfGQ9we9bAMCTzL65hDyfPsjOOVAGtd0mWZvasNnl1ytQgXcVvI23YHmUCLWDLX7yViFllYs_0dzALbfOTN2ljiYZDuv-ndV6uxk3HJpYpPGqtd4R54nRPOIcGKs7V2zT3SOVtfRdD2hWy11GiVOrcszzV-gx-DEQFTkK9SKp33TKixEuKeKFqLkX4X-60Is7DPzMAb3aW2lKIOPNBCxVhjoXGM79aK8RdPs0Qulg_N7kNJyvntT6WkNRI32i3NVr8ZLUW7EoyjH-XFxepbnxXRcTCaj4XAg1qIc5sVxUUxPJvzh3clo_DwQT0lgeJzn09HkbDI-KU6L8Wk-ev4FPQg_Fg)
### 🌈 Introducción a Flujos de Caracteres

Los flujos de caracteres son el tipo de flujos ideal para gestionar datos que no son puramente binarios. Esto se debe a su capacidad para utilizar el conjunto de caracteres Unicode, lo que los convierte en una opción apta para aplicaciones internacionales. 

### 🎓 Clases y Jerarquía en Java

En el lenguaje de programación Java, tenemos clases específicas para manejar flujos de caracteres. Estas son:

* `FileReader`: Para la lectura de archivos de texto.
* `FileWriter`: Para la escritura en archivos de texto.

Estas clases se derivan de las clases `Reader` y `Writer`, que son las clases base para los flujos de caracteres en Java.

#### Tabla de Clases para Flujos de Caracteres

| Clase        | Descripción                   | Deriva De  |
|--------------|-------------------------------|------------|
| `Reader`     | Clase base para leer caracteres| ---        |
| `Writer`     | Clase base para escribir caracteres| ---    |
| `FileReader` | Para leer archivos de texto   | `Reader`   |
| `FileWriter` | Para escribir en archivos de texto| `Writer`|

### 🛠️ Utilización y Ejemplo de Código

Para utilizar flujos de caracteres, el primer paso es crear una instancia de la clase que corresponda, ya sea `FileReader` o `FileWriter`. Este objeto se inicializa a través de su constructor, que puede recibir el nombre del archivo con el que se va a trabajar.

***Ejemplo en Java para leer un archivo:***
```java
FileReader reader = new FileReader("archivo.txt");
```

La lectura o escritura de datos se realiza generalmente de manera secuencial y a menudo se utiliza un bucle para iterar a través del archivo.

***Ejemplo de bucle para lectura:***
```java
int c;
while ((c = reader.read()) != -1) {
  // Código aquí
}
```

### Jerarquías

![[Pasted image 20231012134706.png|900]]
![[Pasted image 20231012134723.png|900]]

### 🌟 Recomendaciones y Buenas Prácticas

Es crucial liberar los recursos una vez que hayamos terminado de trabajar con los fluj os. En Java, esto se logra utilizando el método `close()`.

📌 ***Nota:*** Siempre es bueno asegurarse de que el objeto de flujo se haya creado correctamente antes de intentar cerrarlo.

### 🌐 Aplicabilidad Internacional

Una de las grandes ventajas de los flujos de caracteres es su capacidad para manejar el conjunto de caracteres Unicode. Esto los hace especialmente útiles para aplicaciones que requieren ser utilizadas en diferentes regiones y lenguajes.

Al comprender y utilizar correctamente los flujos de caracteres, los programadores tienen una herramienta poderosa para la manipulación eficiente de archivos de texto, especialmente en un contexto internacional.

___
%%
tags: #pagacceso_a_datos  #FlujosDeCaracteres #Java #FileReader #FileWriter #Reader #Writer #Unicode #Internacionalización #BuenasPrácticas #GestiónDeRecursos #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%