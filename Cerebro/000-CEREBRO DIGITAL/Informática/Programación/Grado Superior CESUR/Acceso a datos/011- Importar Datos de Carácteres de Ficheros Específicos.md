---
ID: 11
nombre: Importar Datos de Caracteres de Ficheros Específicos
tags:
  - pagacceso_a_datos
---
___
### EJEMPLO PRÁCTICO 
En el _editor de texto_ que estamos realizando tenemos implementada una utilidad que importa ficheros en modo bytes, de forma rápida y sencilla para un tipo de ficheros específicos muy pequeños. Pero para _ficheros únicamente de texto_ y más grandes, ficheros con extensión ``.txt``, necesitamos implementar una funcionalidad que nos permita realizar incluso correcciones futuras.

¿Cómo realizaríamos este proceso?

1. Necesitaremos crear un _nuevo método_ dentro de nuestra clase de ``utilidades`` que tenga la siguiente interfaz:

```java
public void importarTXT(String ficheroActual,String ficheroRPC)
```

2. En este método incluiremos el siguiente código:

```java
public void importarTXT(String ficheroActual, String ficheroRPC) throws IOException {
  FileReader in = null;
  FileWriter out = null;
  
  try { // crea flujos de entrada y salida
    in = new FileReader("archivooriginal.txt");
    out = new FileWriter("archivocopiado.txt");
    int c; // guarda cada byte en una variable tipo int
    while ((c = in.read()) != -1) { // lee un byte en c
      out.write(c); // escribe el caracter
    }
  } finally { // Cierra los flujos
    if (in != null) in.close();
    if (out != null) out.close();
  }
}

```

___
%%
tags: #pagacceso_a_datos  #EditorDeTexto #ImportarFicheros #Texto #Metodo #Utilidades #FileReader #FileWriter #IOException #FlujosDeEntrada  #java #FlujosDeSalida #CerrarFlujos
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%