---
ID: 26
nombre: Ejemplo Practico DocumentBuilderFactory
tags:
  - pagacceso_a_datos
---
___
## 📝 Ejemplo Práctico: Importar Fichero XML en una Aplicación 📝

### 🎯 Objetivo 🎯

En la aplicación en desarrollo, se busca importar un fichero XML que se genera cuando una persona entra al almacén.

### 📄 Estructura del Fichero XML 📄

El fichero XML tiene la siguiente estructura:

```xml
<?xml version="1.0"?>
<empresa>
  <empleado id="1">
    <nombre>Paco Gomez</nombre>
    <username>pacogomez</username>
    <password>123456</password>
  </empleado>
</empresa>
```

### 🛠️ Proceso de Importación 🛠️

Para leer e importar el fichero, se sigue el siguiente proceso:

#### 1️⃣ Utilizar la Clase `DocumentBuilder` 🛠️

Se utiliza la clase `DocumentBuilder` del paquete `javax.xml.parsers.DocumentBuilder` para parsear documentos XML de forma sencilla.

```java
// Inicializar el objeto File con la ruta al archivo XML
File archivo = new File("/ruta/almacen.xml");

// Crear una nueva instancia de DocumentBuilderFactory
DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();

// Crear una nueva instancia de DocumentBuilder
DocumentBuilder documentBuilder = dbf.newDocumentBuilder();

// Parsear el archivo XML y normalizarlo
Document document = documentBuilder.parse(archivo);
document.getDocumentElement().normalize();

// Imprimir el elemento raíz del documento XML
System.out.println("Elemento raiz:" + document.getDocumentElement().getNodeName());
```

#### 2️⃣ Obtener Lista de Empleados 📋

Se obtiene una lista de empleados a partir del elemento "empleado".

```java
// Obtener una NodeList de todos los elementos 'empleado' en el documento XML
NodeList listaEmpleados = document.getElementsByTagName("empleado");
```

#### 3️⃣ Recorrer y Extraer Datos de la Lista 🔄

Se recorren los datos de la lista de empleados para extraer la información relevante.

```java
try {
  // Recorrer la NodeList para obtener cada nodo 'empleado'
  for (int temp = 0; temp < listaEmpleados.getLength(); temp++) {
    Node nodo = listaEmpleados.item(temp);
    
    // Imprimir el nombre del nodo actual
    System.out.println("Elemento:" + nodo.getNodeName());
    
    // Verificar si el nodo es un elemento
    if (nodo.getNodeType() == Node.ELEMENT_NODE) {
      Element element = (Element) nodo;
      
      // Imprimir el atributo 'id' del elemento 'empleado'
      System.out.println("id: " + element.getAttribute("id"));
      
      // Imprimir el contenido de texto del elemento 'nombre'
      System.out.println("Nombre: " + element.getElementsByTagName("nombre").item(0).getTextContent());
      
      // Imprimir el contenido de texto del elemento 'username'
      System.out.println("username: " + element.getElementsByTagName("username").item(0).getTextContent());
      
      // Imprimir el contenido de texto del elemento 'password'
      System.out.println("password: " + element.getElementsByTagName("password").item(0).getTextContent());
    }
  }
} catch (Exception e) {
  // Imprimir cualquier excepción que ocurra
  e.printStackTrace();
}
```

Con estos pasos, se logra importar y procesar el fichero XML en la aplicación.

___
%%
tags: #java  #pagacceso_a_datos  
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%