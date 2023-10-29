---
ID: 3
nombre: Class Stage
tags:
  - pagdesarrollo_de_interfaces
---
___
La clase `Stage` en JavaFX es el contenedor de nivel superior y puede ser construida por la plataforma o por la aplicación. Debe ser manejada en el Hilo de Aplicación de JavaFX. Puede tener diferentes estilos y propietarios, lo que afecta su comportamiento y apariencia. También puede tener modalidades que bloquean eventos de entrada en otras ventanas. La modalidad debe configurarse antes de mostrar el `Stage`.

### Métodos más importantes Class Stage
1. `initStyle(StageStyle style)`: Establece el estilo del `Stage`, como DECORATED, UNDECORATED, TRANSPARENT, o UTILITY.

2. `setResizable(boolean value)`: Permite habilitar o deshabilitar la capacidad de cambiar el tamaño del `Stage` por parte del usuario.

3. `setTitle(String title)`: Establece el título del `Stage`.

4. `show()`: Muestra el `Stage` en pantalla.

5. `hide()`: Oculta el `Stage`.

6. `close()`: Cierra el `Stage`.

7. `setIconified(boolean value)`: Minimiza o restaura el `Stage` según el valor especificado.

8. `initOwner(Window owner)`: Establece la ventana propietaria (owner) del `Stage`.

9. `initModality(Modality modality)`: Establece la modalidad del `Stage`, como NONE, WINDOW_MODAL o APPLICATION_MODAL.

10. `setFullScreen(boolean value)`: Permite cambiar el `Stage` al modo de pantalla completa.

11. `setScene(Scene scene)`: Establece la escena que se mostrará en el `Stage`.

12. `setOnCloseRequest(EventHandler<WindowEvent> eventHandler)`: Establece un manejador de eventos para el evento de cierre del `Stage`.

### Paquetes y Clases más importantes Class Stage

1. `javafx.stage.Modality`: Este paquete enumera las modalidades posibles para una ventana, como `NONE`, `WINDOW_MODAL` y `APPLICATION_MODAL`.

2. `javafx.stage.StageStyle`: Aquí encontrarás las diferentes opciones de estilo para una ventana, como `DECORATED`, `UNDECORATED`, `TRANSPARENT`, y `UTILITY`.

3. `javafx.stage.Screen`: Contiene clases para trabajar con pantallas, lo que es útil para tareas como obtener información sobre la pantalla actual o configurar una ventana en una pantalla específica.


___
%%
tags: #pagdesarrollo_de_interfaces  #JavaFX #Stage #Métodos #initStyle #setResizable #setTitle #show #hide #close #setIconified #initOwner #initModality #setFullScreen #setScene #setOnCloseRequest #Paquetes #javafx  #HiloDeAplicación #Modalidad #Estilo #Pantalla 
Vínculos: [[000-Menú Desarrollo de interfaces 📃|Menú Desarrollo de interfaces 📃]]
%%