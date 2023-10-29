---
ID: 4
nombre: Ejemplo Listar Contenido del Directorio actual
tags:
  - pagacceso_a_datos
---
___
1. El primer paso será crear un ``nuevo proyecto`` con la siguiente estructura y ficheros.

![[Pasted image 20231012122612.png]]

2. ``UtilidadesF`` tendrá las propiedades y métodos para la gestión de ficheros. En concreto, implementamos un primer método para el listado del directorio actual.

```java
package gestionF; 
import java.io.File; 
public class UtilidadesF { 
	public void directorioActual() { 
		File directorio = new File("."); //directorio actual 
		String[] lista = directorio.list(); 
		for (int i = 0; i<lista.lenght; i++)
		{
			System.out.println(lista[i]);
		}
	}
}
```

3. La clase ``editorFicheros`` será la clase principal.

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
tags: #pagacceso_a_datos  #NuevoProyecto #EstructuraDeFicheros #UtilidadesF #GestiónDeFicheros #ListadoDeDirectorio #Java #ClasePrincipal #editorFicheros #Métodos #Importaciones #DirectorioActual #Clases #Propiedades #MétodosJava #Listado  #java
Vínculos:  [[000-Menú Acceso a datos 📃|Menú Acceso a datos 📃]]
%%