---
ID: 6
nombre: Flujos de Bytes en Programación
tags:
  - pagacceso_a_datos
---
___
[![](https://mermaid.ink/img/pako:eNp1k0tu2zAQhq9CcGUDgitbttxoWScuEqBIULebwJuxOE6Z8qHyEdQ1fJgeIKscwRfrSJYfcOqNQM3MP_z5cbjmpRXIC66lERqquWHMWRs6namKz9YzgezTKqBnaNiDs08ONJRy-2a63bqWsc6tCc6KWDZRBuxM2JYxdl-hI6k12CSRZCCArZgHJQXsy64hkHohDThp_S7anSjwJHtw0pSyArXzcwcv0NnryEcVwyw4BH3Yk7GpVHiSOVTfx3Cp_DTVnvG7t2R0Gk3tH7Qk8_agmlChY3bxjMHSyRRb1gSOPSfW-OBiGaw7Y1EDm2EZkfqCOnFRb1QnqbNoLXxGH5oYsftKGuftke0EnSMPzcYts2-wUEB76wocBPkCtbDlSKuzW9o3-g-q9zguUr1A744O637F7Sv4E9S3evv3CU1bQ5BKFX0zWRcm5ubDjOFSljX9o2MS0vwptn2rgtSWebtwSOB2hHjCNToNUtCMr2vNnIcfqHHOC1oKcD_nfG42VAcx2NnKlLygy8KEx0pAwGsJ9czzYgnKH6I3QtJtHoLY_H7ZvaTmQSW8AvNord53o19erPlvXozSXvbxKk2z8SjL80G_n_AVL_pp1suy8TCnD2XzwWiT8D9Ng34vTceD_CpPh-MsS4dZvvkHwZk2Ow?type=png)](https://mermaid.live/edit#pako:eNp1k0tu2zAQhq9CcGUDgitbttxoWScuEqBIULebwJuxOE6Z8qHyEdQ1fJgeIKscwRfrSJYfcOqNQM3MP_z5cbjmpRXIC66lERqquWHMWRs6namKz9YzgezTKqBnaNiDs08ONJRy-2a63bqWsc6tCc6KWDZRBuxM2JYxdl-hI6k12CSRZCCArZgHJQXsy64hkHohDThp_S7anSjwJHtw0pSyArXzcwcv0NnryEcVwyw4BH3Yk7GpVHiSOVTfx3Cp_DTVnvG7t2R0Gk3tH7Qk8_agmlChY3bxjMHSyRRb1gSOPSfW-OBiGaw7Y1EDm2EZkfqCOnFRb1QnqbNoLXxGH5oYsftKGuftke0EnSMPzcYts2-wUEB76wocBPkCtbDlSKuzW9o3-g-q9zguUr1A744O637F7Sv4E9S3evv3CU1bQ5BKFX0zWRcm5ubDjOFSljX9o2MS0vwptn2rgtSWebtwSOB2hHjCNToNUtCMr2vNnIcfqHHOC1oKcD_nfG42VAcx2NnKlLygy8KEx0pAwGsJ9czzYgnKH6I3QtJtHoLY_H7ZvaTmQSW8AvNord53o19erPlvXozSXvbxKk2z8SjL80G_n_AVL_pp1suy8TCnD2XzwWiT8D9Ng34vTceD_CpPh-MsS4dZvvkHwZk2Ow)
### 📚 Introducción a Flujos de Bytes

Los flujos de bytes son esenciales cuando se trata de operaciones de entrada y salida basadas en datos binarios. Estos flujos trabajan con bytes de 8 bits y son particularmente útiles para la lectura y escritura de este tipo de datos.

### 🛠️ Clases Principales en Java

En Java, las clases `InputStream` y `OutputStream` actúan como clases padre para otros tipos más específicos de flujos de bytes. Algunas de las clases hijas notables son `FileInputStream` y `FileOutputStream`, que son especialmente útiles para trabajar con archivos en disco.

### 📝 Uso y Funcionamiento

Para empezar a trabajar con flujos de bytes, es necesario crear un objeto del flujo utilizando su constructor. Por ejemplo, para leer un archivo localizado en una ruta específica, se podría usar el siguiente código en Java:

```java
in = new FileInputStream(String path);
```

#### 🔄 Operación Secuencial

La lectura o escritura de datos es generalmente secuencial y se hace utilizando un bucle. La función `read()` se utiliza para leer el contenido byte a byte. Esta función devuelve un entero, que representa el byte leído del archivo. El proceso continúa hasta que se devuelve un -1, indicando que se ha alcanzado el final del archivo.

```java
while ((b = in.read()) != -1) {
  // Código aquí
}
```

### ⚙️ Gestión de Recursos

Es crucial cerrar los flujos una vez que se ha terminado con ellos para evitar el desperdicio de recursos. Esto se hace generalmente en el bloque `finally` en Java, asegurándose de que los flujos fueron efectivamente creados antes de intentar cerrarlos.

### 📈 Tabla Comparativa de Clases de Flujos de Bytes

| Clase         | Descripción                           | Uso común             |
|---------------|---------------------------------------|-----------------------|
| `InputStream` | Clase padre para flujos de entrada     | Lectura de datos      |
| `OutputStream`| Clase padre para flujos de salida      | Escritura de datos    |
| `FileInputStream` | Específica para archivos en disco  | Lectura desde archivos |
| `FileOutputStream`| Específica para archivos en disco  | Escritura a archivos   |
### Jerarquías

![[Pasted image 20231012125751.png|900]]
![[Pasted image 20231012125833.png|900]]


Al dominar estos conceptos y técnicas básicas, los desarrolladores pueden realizar operaciones de E/S de manera eficiente, manteniendo un control óptimo sobre los recursos del sistema.


___
%%
tags: #pagacceso_a_datos  #FlujosDeBytes #Programación #EntradaSalida #DatosBinarios #Java #InputStream #OutputStream #FileInputStream #FileOutputStream #OperaciónSecuencial #GestiónDeRecursos #TablaComparativa #Eficiencia #ControlDeRecursos #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%