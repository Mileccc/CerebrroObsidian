---
ID: 8
nombre: Importar Datos de Ficheros Específicos
tags:
  - pagacceso_a_datos
---
___
### EJEMPLO PRÁCTICO 
En el editor de texto que estamos realizando y dentro de las utilidades a incorporar necesitamos tener un método que nos permita _importar datos de ficheros_ específicos con extensión ``.rpc`` que provienen de una exportación de una máquina de producción _a nuestro fichero actualmente_ activo. ¿Cómo realizaríamos este proceso?

1. Necesitaremos crear un nuevo método dentro de nuestra clase de ``utilidades`` que tenga la siguiente interfaz:

```java
public void importarRPC(String ficheroActual,String ficheroRPC)
```

2. En este método incluiremos el siguiente código:

```java
public void importarRPC(String ficheroActual, String ficheroRPC) throws IOException {
  FileInputStream in = null;
  FileOutputStream out = null;
  try {
    in = new FileInputStream(ficheroRPC);
    out = new FileOutputStream(ficheroActual);
    int b;
    while ((b = in.read()) != -1) {
      out.write(b);
    }
  } finally {
    if (in != null) in.close();
    if (out != null) out.close();
  }
}
```

___
%%
tags: #pagacceso_a_datos  #EjemploPráctico #EditorDeTexto #ImportarDatos #Ficheros #ExtensiónRPC #MáquinaDeProducción #FicheroActivo #Método #ClaseDeUtilidades #FileInputStream #FileOutputStream #IOException #CódigoJava #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%