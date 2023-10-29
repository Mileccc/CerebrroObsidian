---
ID: 13
nombre: Acceso Aleatorio en Java
tags:
  - pagacceso_a_datos
---
___
***Abrir un archivo solo para lectura:***

```java
RandomAccessFile f1 = new RandomAccessFile("archivo.txt", "r");
```

***Abrir un archivo para lectura y escritura:***

```java
RandomAccessFile f2 = new RandomAccessFile("archivo.txt", "rw");
```

### 🌠 Recomendaciones

Es vital elegir la forma de acceso más apropiada según el tipo de operación que vayamos a realizar en el archivo. Utilizar el método incorrecto podría llevar a ineficiencias, especialmente cuando se trata de archivos grandes. 

Al conocer los pros y contras de cada método y cómo implementarlos en Java, estamos armados con las herramientas necesarias para manipular archivos de forma eficiente.


___
%%
tags: #pagacceso_a_datos  #AccesoAFicheros #Java #AccesoSecuencial #AccesoAleatorio #FileReader #FileWriter #FileInputStream #FileOutputStream #RandomAccessFile #Eficiencia #DatosBinarios #DatosDeTexto #Lectura #Escritura #Recomendaciones #ClasesJava #Interfaces #DataInput #DataOutput #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]] , accesoexadecimal
%%