---
ID: 100
tags: 
nombre: Ficheros
---
___
# Ficheros
___
### 1- Clase que contendrá las utilidades de los ficheros

```java
package manejo_ficheros;
import java.io.File;
  
public class UtilidadesF {

}
```


### 2- Creamos método listar contenido fichero
Lista el contenido de los ficheros de la posición del path actual

```java
package manejo_ficheros;
import java.io.File;
  
public class UtilidadesF {
	public void directorioActual() {
		File directorio = new File("."); // directorio actual
		String[] lista = directorio.list();
		for (int i = 0; i < lista.length; i++) {
		System.out.println(lista[i]);
		}
	}
}
```

---
### 3- Crear Clase para editar/acceder a ficheros 
Contendrá el método main

```java
import gestionF.UtilidadesF; 
public class editorFicheros {
	static UtilidadesF utilF=new UtilidadesF();
	
	public static void main(String[] args) {
		// listamos el directorio actual 
		utilF.directorioActual(); 
	}
}
```















___
%%
tags: #java #pagjava 

Vínculos:  [[000-Menú Java 📃|Java]]   
%%