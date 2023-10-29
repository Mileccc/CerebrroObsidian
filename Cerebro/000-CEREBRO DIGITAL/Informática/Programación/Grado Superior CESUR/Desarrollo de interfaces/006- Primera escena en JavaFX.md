---
ID: 6
nombre: Primera escena en JavaFX
tags:
  - pagdesarrollo_de_interfaces
---
___
##### Ejemplo uso de Application, Scene y Stage 

```java
import javafx.application.Application;
import javafx.stage.Stage;
import javafx.scene.shape.Circle;
import javafx.scene.Group;
import javafx.scene.Scene;
  
public class Main extends Application {
	@Override
	public void start(Stage primaryStage) throws Exception {
		//Se crea la escena
		Circle circ = new Circle(40, 40, 30);
		Group root = new Group(circ);
		Scene scene = new Scene(root, 400, 300);
		  
		//Se añade la escena al escenario
		primaryStage.setTitle("Mi primera aplicación");
		primaryStage.setScene(scene);
		primaryStage.show();
	  
	}
	  
	public static void main(String[] args) {
	launch(args);
	  
	}
  
}
```
$$CONSOLA$$
![[Pasted image 20231009201915.png|700]]






___
%%
tags: #código #programación  #pagdesarrollo_de_interfaces 
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%