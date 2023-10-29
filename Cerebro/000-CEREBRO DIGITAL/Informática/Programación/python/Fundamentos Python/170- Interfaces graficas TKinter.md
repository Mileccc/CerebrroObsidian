---
ID: 170
tags: 
nombre: Interfaces graficas TKinter
---
___
# Interfaces graficas TKinter
___
## 1- Crear instancia de la ventana principal (TK())

![](https://www.youtube.com/watch?v=hTUJC8HsC2I&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=42&ab_channel=pildorasinformaticas)

El video explica las interfaces gráficas de usuario en Python. Con Tkinter se pueden construir GUIs de forma sencilla. Importa Tkinter y crea una ventana mediante un objeto root con la clase Tk unido a mainloop() para mantenerla ejecutándose.

Dentro de root se colocan frames y widgets como botones u opciones. Los métodos personalizan root: title() establece el título, geometry() fija el tamaño, resizable() controla su redimensión. Config() cambia propiedades y iconbitmap() añade un icono.

Se requiere tener previamente una imagen .ico para establecerla como ícono. Las ventanas deben estar a la espera de eventos del usuario en mainloop(). Tkinter proporciona métodos para construir elementos de forma sencilla.

1. Crear ventana básica importando Tkinter y usando root, Tk() y mainloop()
    
2. Añadir título y fondo verde usando root.title() y root.config(bg="green")
    
3. Establecer ícono usando root.iconbitmap("icono.ico")

***EJEMPLO***
```python
import tkinter as tk

# Crear una instancia de la ventana principal
root = tk.Tk()

# Configurar el título de la ventana
root.title("Mi Ventana")

# Configurar el color de fondo de la ventana
root.config(bg="green")

# Establecer el ícono de la ventana (asegúrate de tener un archivo "icono.ico" en la misma carpeta)
root.iconbitmap("icono.ico")

# Ejecutar el bucle principal para mantener la ventana abierta
root.mainloop()

```

___
## 2- Frames
![](https://www.youtube.com/watch?v=M80CzDC1Crc&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=43&ab_channel=pildorasinformaticas)

**Resumen**:  
En el video se explica cómo crear frames en una interfaz gráfica de Python usando la biblioteca Tkinter. Se comienza explicando la estructura básica de una interfaz con raíz y frames. Luego se muestra como crear un primer frame mediante la clase Frame y empaquetarlo dentro de la raíz con el método pack(). También se explica como configurar propiedades del frame como el color de fondo, tamaño, posición al redimensionar, tipo de borde y cursor del ratón. Todo ello utilizando el método config() del frame. Por último, se indica que estas configuraciones también se pueden aplicar a la raíz.

**Lista de puntos importantes:**

(00:33) - Explicación de widgets, raíz y frames  
(03:15) - Creación de un frame con la clase Frame  
(03:46) - Empaquetado del frame dentro de la raíz con frame.pack()  
(04:56) - Configuración del color de fondo del frame con frame.config(background="red")  
(06:11) - Configuración del tamaño del frame con frame.config(width=650, height=350)  
(07:18) - Configuración de la posición al redimensionar con frame.pack(side="right")  
(08:29) - Uso de answer para posicionar en varias direcciones  
(10:22) - Configuración para redimensionarse con la raíz utilizando fill="x"  
(13:01) - Configuración del grosor y tipo de borde del frame  
(14:20) - Configuración del cursor del ratón dentro del frame


```python
import tkinter as tk

# Crear la ventana principal
root = tk.Tk()
root.title("Ejemplo de Frames")

# Crear un frame
frame = tk.Frame(root, bg="red", width=650, height=350, borderwidth=2, relief="ridge", cursor="hand2")
frame.pack(side="right", fill="x")

# Crear otro frame
frame2 = tk.Frame(root, bg="blue", width=300, height=200, borderwidth=3, relief="sunken", cursor="pirate")
frame2.pack(side="left")

# Ejecutar el bucle principal
root.mainloop()

```
$$CONSOLA$$
![[Pasted image 20230926211504.png]]

___
## 3- Label
![](https://www.youtube.com/watch?v=Nf4-gvf-tNg&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=45&ab_channel=pildorasinformaticas)

El video explica cómo utilizar la clase Label de Tkinter para mostrar texto e imágenes estáticas en una interfaz gráfica en Python. Se muestra la sintaxis básica para crear un Label, las opciones más comunes como texto, imagen, color y fuente, y cómo posicionarlo con .pack() y .place(). Se explica que con .pack() el Label adapta el contenedor y con .place() se ubica por coordenadas. Se muestra un ejemplo para crear un Label con texto, cambiar su color y fuente, y otro ejemplo para mostrar una imagen PNG. 

Lista de puntos importantes:

- Clase Label para texto e imágenes estáticos (00:02)
- Opciones comunes de Label: texto, imagen, color, fuente, etc. (00:33)  
- Ubicación con .pack() y .place() (05:19)
- Ejemplo Label con texto, color y fuente (06:36)
- Mostrar imágenes PNG con la clase PhotoImage (09:29)

El video cubre los conceptos básicos para empezar a trabajar con Labels en Tkinter y muestra ejemplos prácticos. Los Labels permiten agregar elementos visuales estáticos en las interfaces gráficas.

- ***Ejemplo***

```python
import tkinter as tk
from tkinter import PhotoImage
  
# Crear una ventana principal
ventana = tk.Tk()
ventana.title("Ejemplo de Label en Tkinter")
  
# Crear un Frame con un tamaño de 650x400
frame = tk.Frame(ventana, width=650, height=400)
frame.pack()
  
# Crear un Label con texto, color y fuente
label_texto = tk.Label(frame, text="Hola, soy un Label", fg="blue", font=("Arial", 12))
  
# Ubicar el Label de texto en el Frame
label_texto.pack()
  
# Crear un Label para mostrar una imagen PNG
imagen = PhotoImage(file="Diablo_IV_icon.png")  # Asegúrate de tener un archivo imagen.png en la misma carpeta
label_imagen = tk.Label(frame, image=imagen)
  
# Ubicar el Label de la imagen en el Frame
label_imagen.pack()

  
# Ejecutar la aplicación
ventana.mainloop()
```
$$CONSOLA$$
![[Pasted image 20230928184514.png]]

___


El video explica cómo utilizar la clase Entry de Tkinter para crear cuadros de texto donde el usuario puede ingresar información en una interfaz gráfica en Python. Se muestra la sintaxis básica para crear un Entry, ubicarlo con .pack() y .place(), y agregarlo a un contenedor Frame. También se explica cómo alinear varios Entry y Labels con el método .grid() dividiendo la interfaz en filas y columnas. Se cubre cómo configurar un Entry para que muestre asteriscos en los campos password.

Lista de puntos importantes:

- Clase Entry para cuadros de texto (00:02)
- Ubicación con .pack() y .place() (02:14)  
- Alineación con .grid() en filas y columnas (06:23)
- Configurar Entry password con show="" (23:39)
- Opciones de Entry: color, alineación de texto, etc. (21:05)

El video muestra cómo agregar interacción en Tkinter permitiendo al usuario ingresar información en campos de texto.

```python
import tkinter as tk
  
# Crear una ventana principal
ventana = tk.Tk()
ventana.title("Ejemplo de Entry en Tkinter")
  
# Crear un contenedor Frame de tamaño 700x400
frame = tk.Frame(ventana, width=700, height=400, bg="red")
frame.pack(fill=tk.BOTH, expand=True)  # Rellenar y expandir el frame
  
# Crear Labels
label_nombre = tk.Label(frame, text="Nombre:")
label_apellido = tk.Label(frame, text="Apellido:")
label_password = tk.Label(frame, text="Password:")
  
# y Entry para alinear con .grid()
entry_nombre = tk.Entry(frame)
entry_apellido = tk.Entry(frame)
entry_password = tk.Entry(frame, show="*")
  
# Usar .grid() para alinear los elementos en filas y columnas dentro del Frame
label_nombre.grid(row=0, column=0, padx=10, pady=10)
label_apellido.grid(row=1, column=0, padx=10, pady=10)
label_password.grid(row=2, column=0, padx=10, pady=10)
entry_nombre.grid(row=0, column=1, padx=10, pady=10)
entry_apellido.grid(row=1, column=1, padx=10, pady=10)
entry_password.grid(row=2, column=1, padx=10, pady=10)
  
# Configurar la ventana para que se ajuste al tamaño del frame inicialmente
ventana.geometry(f"{frame.winfo_reqwidth()}x{frame.winfo_reqheight()}")
  
# Función para actualizar el tamaño del frame cuando cambia el tamaño de la ventana
def resize(event):
    frame.config(width=event.width, height=event.height)
  
# Enlazar la función resize con el evento de cambio de tamaño de la ventana
ventana.bind("<Configure>", resize)
  
# Ejecutar la aplicación
ventana.mainloop()
```
$$CONSOLA$$
![[Pasted image 20230928194042.png]]


___

## 4- Text y Button

![](https://www.youtube.com/watch?v=nZF9SwhmPRo&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=46&ab_channel=pildorasinformaticas)

___
El video explica cómo construir interfaces gráficas en Python utilizando los widgets `Text` y `Button`. Se muestra cómo agregar un área de texto grande con scroll, configurar su tamaño y scrollbar. También se explica cómo agregar botones que ejecuten código al presionarlos. Se da un ejemplo para introducir texto en un cuadro `Entry` al presionar el botón.

- Agregar widget `Text` y configurar tamaño (00:32)  
- Agregar scrollbar vertical al `Text` (06:48)
- Configurar scrollbar para que se adapte al `Text` (10:29)  
- Agregar botón con la clase `Button` (14:12)
- Ejecutar código al presionar el botón con `command` (15:26)
- Introducir texto en `Entry` con botón (16:29)

El video termina explicando que en la próxima clase se construirá una calculadora con lo aprendido.

```python
import tkinter as tk
  
# Crear una ventana principal
ventana = tk.Tk()
ventana.title("Interfaz Gráfica en Python")
  
# Crear un contenedor Frame de tamaño 700x400
frame = tk.Frame(ventana, width=700, height=400, bg="red")
frame.pack(fill=tk.BOTH, expand=True)  # Rellenar y expandir el frame
  
# Agregar un widget Text y configurar su tamaño
texto = tk.Text(frame, wrap=tk.WORD, width=40, height=10)
texto.grid(row=0, column=0, padx=10, pady=10)

  
# Agregar una scrollbar vertical al widget Text
scrollbar = tk.Scrollbar(frame, command=texto.yview)
scrollbar.grid(row=0, column=1, sticky="ns")
texto.config(yscrollcommand=scrollbar.set)
  
# Función para ejecutar al presionar el botón
def agregar_texto():
    texto.insert(tk.END, "Texto agregado desde el botón\n")
  
# Agregar un botón con la clase Button
boton = tk.Button(frame, text="Agregar Texto", command=agregar_texto)
boton.grid(row=1, column=0, padx=10, pady=10)
  
# Configurar la ventana para que se ajuste al tamaño del frame inicialmente
ventana.geometry("{}x{}".format(frame.winfo_reqwidth(), frame.winfo_reqheight()))
  
# Función para actualizar el tamaño del frame cuando cambia el tamaño de la ventana
def resize(event):
    frame.config(width=event.width, height=event.height)
  
# Enlazar la función resize con el evento de cambio de tamaño de la ventana
ventana.bind("<Configure>", resize)
  
# Ejecutar la aplicación
ventana.mainloop()
```
$$CONSOLA$$
![[Pasted image 20230928200321.png]]


___
## 5- Calculadora
![](https://www.youtube.com/watch?v=kbTl3DaFJUk&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=47&ab_channel=pildorasinformaticas)

![](https://www.youtube.com/watch?v=oIzt6ESA7nU&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=48&ab_channel=pildorasinformaticas)

![](https://www.youtube.com/watch?v=LnO35TiFuQY&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=49&ab_channel=pildorasinformaticas)


El video muestra cómo empezar a dar funcionalidad a una calculadora creada con Python/Tkinter. Se explica cómo almacenar la operación elegida por el usuario y resetear la pantalla al elegir una nueva. También cómo guardar los valores numéricos en variables para poder realizar operaciones con ellos. 


```python
from tkinter import *
  
raiz = Tk()
miFrame = Frame(raiz)
miFrame.pack()
  
operacion = ""
resultado = 0
reset_pantalla = False
  
# ENTRY
# ---------------------PANTALLA--------------------------------------------------
numeroPantalla = StringVar()
  
pantalla = Entry(miFrame, textvariable=numeroPantalla)
pantalla.grid(row=1, column=1, padx=10, pady=10, columnspan=4)
pantalla.config(background="black", fg="#03f943", justify="right")
  
  
# ----------------------pulsaciones teclado----------------------------------------
def numeroPulsado(num):
    global operacion
    global reset_pantalla
  
    if reset_pantalla != False:
        numeroPantalla.set(num)
        reset_pantalla = False
    else:
        numeroPantalla.set(numeroPantalla.get()+num)
  
  
# ----------------------Funcion suma-------------------------------------------------
def suma(num):
    global operacion
    global resultado
    global reset_pantalla
  
    resultado += int(num)
    operacion = "suma"
    reset_pantalla = True
  
    numeroPantalla.set(resultado)
  
# ---------------------Funcion resta----------------------------------------------------
num1 = 0
contador_resta = 0
  
def resta(num):
    global operacion
    global resultado
    global num1
    global contador_resta
    global reset_pantalla
  
    if contador_resta == 0:
        num1 = int(num)
        resultado = num1
    else:
        if contador_resta == 1:
            resultado = num1-int(num)
        else:
            resultado = int(resultado)-int(num)
        numeroPantalla.set(resultado)
        resultado = numeroPantalla.get()
  
    contador_resta = contador_resta+1
    operacion = "resta"
    reset_pantalla = True
  
  
# ---------------------Funcion multiplicacion-------------------------------------------------
contador_multi = 0
  
def multiplicar(num):
    global operacion
    global resultado
    global num1
    global contador_multi
    global reset_pantalla
  
    if contador_multi == 0:
        num1 = int(num)
        resultado = num1
    else:
        if contador_multi == 1:
            resultado = num1*int(num)
        else:
            resultado = int(resultado)*int(num)
        numeroPantalla.set(resultado)
        resultado = numeroPantalla.get()
  
    contador_multi = contador_multi+1
    operacion = "multiplicacion"
    reset_pantalla = True
  
# ---------------------Funcion division-----------------------------------------------------
  
contador_divi = 0
  
def divide(num):
  
    global operacion
    global resultado
    global num1
    global contador_divi
    global reset_pantalla
  
    if contador_divi == 0:
        num1 = float(num)
        resultado = num1
    else:
        if contador_divi == 1:
            resultado = num1/float(num)
        else:
            resultado = float(resultado)/float(num)
        numeroPantalla.set(resultado)
        resultado = numeroPantalla.get()
  
    contador_divi = contador_divi+1
    operacion = "division"
    reset_pantalla = True
  
# ---------------------Funcion resultado igual -----------------------------------------------
def el_resultado():
    global resultado
    global operacion
    global contador_resta
    global contador_multi
    global contador_divi
  
    if operacion == "suma":
        numeroPantalla.set(resultado+int(numeroPantalla.get()))
        resultado = 0
    elif operacion == "resta":
        numeroPantalla.set(int(resultado)-int(numeroPantalla.get()))
        resultado = 0
        contador_resta = 0
    elif operacion == "multiplicacion":
        numeroPantalla.set(int(resultado)*int(numeroPantalla.get()))
        resultado = 0
        contador_multi = 0
    elif operacion == "division":
        numeroPantalla.set(int(resultado)/int(numeroPantalla.get()))
        resultado = 0
        contador_divi = 0
  
# ---------------------FILA 1 -----------------------------------------------------
boton7 = Button(miFrame, text="7", width=3, command=lambda: numeroPulsado("7"))
boton7.grid(row=2, column=1)
boton8 = Button(miFrame, text="8", width=3, command=lambda: numeroPulsado("8"))
boton8.grid(row=2, column=2)
boton9 = Button(miFrame, text="9", width=3, command=lambda: numeroPulsado("9"))
boton9.grid(row=2, column=3)
botonMult = Button(miFrame, text="X", width=3,
                   command=lambda: multiplicar(numeroPantalla.get()))
botonMult.grid(row=2, column=4)

# ---------------------FILA 2 -----------------------------------------------------
boton4 = Button(miFrame, text="4", width=3, command=lambda: numeroPulsado("4"))
boton4.grid(row=3, column=1)
boton5 = Button(miFrame, text="5", width=3, command=lambda: numeroPulsado("5"))
boton5.grid(row=3, column=2)
boton6 = Button(miFrame, text="6", width=3, command=lambda: numeroPulsado("6"))
boton6.grid(row=3, column=3)
botonResta = Button(miFrame, text="-", width=3,
                    command=lambda: resta(numeroPantalla.get()))
botonResta.grid(row=3, column=4)

# ---------------------FILA 3 -----------------------------------------------------
boton1 = Button(miFrame, text="1", width=3, command=lambda: numeroPulsado("1"))
boton1.grid(row=4, column=1)
boton2 = Button(miFrame, text="2", width=3, command=lambda: numeroPulsado("2"))
boton2.grid(row=4, column=2)
boton3 = Button(miFrame, text="3", width=3, command=lambda: numeroPulsado("3"))
boton3.grid(row=4, column=3)
botonSuma = Button(miFrame, text="+", width=3,
                   command=lambda: suma(numeroPantalla.get()))
botonSuma.grid(row=4, column=4)

# ---------------------FILA 4 -----------------------------------------------------
botonDiv = Button(miFrame, text="/", width=3,
                  command=lambda: divide(numeroPantalla.get()))
botonDiv.grid(row=5, column=1)
boton0 = Button(miFrame, text="0", width=3, command=lambda: numeroPulsado("0"))
boton0.grid(row=5, column=2)
botonComa = Button(miFrame, text=",", width=3,
                   command=lambda: numeroPulsado("."))
botonComa.grid(row=5, column=3)
botonIgual = Button(miFrame, text="=", width=3, command=lambda: el_resultado())
botonIgual.grid(row=5, column=4)
  
raiz.mainloop()
```
$$CONSOLA$$
![[Pasted image 20230929121546.png|200]]

___
## 6- Radiobuttons
___
![](https://www.youtube.com/watch?v=YfYUOUGMaXU&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=50&ab_channel=pildorasinformaticas)



El video muestra cómo crear radiobuttons o botones de opción en Python usando Tkinter. Sirven para preguntas con respuesta única como género masculino/femenino. Se crean con `Radiobutton`, se asigna variable y valor entero para identificar opción elegida. Con `variable.get()` obtenemos el valor y ejecutamos código según opción. Se muestra un ejemplo con 2 radiobuttons para elegir género, imprimiendo opción elegida. Se pueden agregar más opciones y lógica según necesidad. Ideales para opciones excluyentes.  

Lista de puntos importantes:

- 03:01 - Crear con clase `Radiobutton`, indicando contenedor y texto
- 04:39 - Asignar variable y valor entero a cada opción 
- 05:59 - Con `variable.get()` obtenemos valor seleccionado
- 07:11 - Llamar función con lógica según opción usando `command`
- 09:41 - Cambiar texto de Labels según opción elegida 
- 11:23 - Se pueden agregar más opciones si necesario

```python
import tkinter as tk
  
# Función para mostrar el género seleccionado
def mostrar_genero():
    genero_seleccionado = genero_var.get()
    resultado.config(text="Género seleccionado: " + genero_seleccionado)
  
# Crear la ventana principal
ventana = tk.Tk()
ventana.title("Ejemplo de Radiobuttons")
  
# Variable para rastrear el género seleccionado
genero_var = tk.StringVar()
  
# Crear Radiobuttons
opcion_masculino = tk.Radiobutton(ventana, text="Masculino", variable=genero_var, value="Masculino", command=mostrar_genero)
opcion_femenino = tk.Radiobutton(ventana, text="Femenino", variable=genero_var, value="Femenino", command=mostrar_genero)
  
# Crear una etiqueta para mostrar el género seleccionado
resultado = tk.Label(ventana, text="Género seleccionado: ")
  
# Colocar los widgets en la ventana
opcion_masculino.pack()
opcion_femenino.pack()
resultado.pack()
  
# Iniciar el bucle principal
ventana.mainloop()
```
$$CONSOLA$$
![[Pasted image 20230929130119.png|300]]

___
## 7- Checkbuttons
![](https://www.youtube.com/watch?v=TzeU61X-dnI&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=51&ab_channel=pildorasinformaticas)

___
Este video explica el uso de los checkbox o casillas de verificación en Python. Se pueden seleccionar varios a la vez, a diferencia de los radiobuttons. Se crean con la clase `Checkbutton` y permiten opciones múltiples en formularios. Se utilizan variables enteras para detectar si están activados (1) o no (0), y condicionales para ejecutar código según estén marcados. Se muestra un ejemplo creando 3 checkbox para elegir destinos, detectando cuáles están activos y mostrando las opciones elegidas.

Lista de puntos importantes:

- 00:32 - Checkbutton permiten seleccionar varios a la vez, no como radiobutton 
- 01:41 - Se crean con la clase `Checkbutton`, se indica contenedor y texto
- 02:13 - Utilizar variables enteras para detectar estado seleccionado (1) o no (0)
- 05:48 - Crear función para evaluar variables y ejecutar código según estado
- 10:14 - Asociar variable y función a evento `command` de cada Checkbutton
- 12:36 - Se pueden mezclar con radiobuttons y otros elementos en la interfaz


```python
import tkinter as tk
  
# Función que se ejecuta cuando se hace clic en un Checkbutton
def mostrar_opciones():
    resultado.config(text="Opciones seleccionadas:")
    if opcion1_var.get():
        resultado.config(text=resultado.cget("text") + " Opción 1") # cget se diferencia de get en que se usa para obtener  
    if opcion2_var.get():
        resultado.config(text=resultado.cget("text") + " Opción 2") # el texto de los label y los buttons widgets
    if opcion3_var.get():
        resultado.config(text=resultado.cget("text") + " Opción 3") #  que no son de entrada de texto como entry o text
  
# Crear la ventana principal
ventana = tk.Tk()
ventana.title("Ejemplo de Checkbuttons")
  
# Variables para rastrear el estado de los Checkbuttons
opcion1_var = tk.IntVar()
opcion2_var = tk.IntVar()
opcion3_var = tk.IntVar()
  
# Crear Checkbuttons
opcion1 = tk.Checkbutton(ventana, text="Opción 1", variable=opcion1_var, command=mostrar_opciones)
opcion2 = tk.Checkbutton(ventana, text="Opción 2", variable=opcion2_var, command=mostrar_opciones)
opcion3 = tk.Checkbutton(ventana, text="Opción 3", variable=opcion3_var, command=mostrar_opciones)
  
# Crear un label para mostrar las opciones seleccionadas
resultado = tk.Label(ventana, text="Opciones seleccionadas:")
  
# Colocar los widgets en la ventana
opcion1.pack()
opcion2.pack()
opcion3.pack()
resultado.pack()
  
# Iniciar el bucle principal
ventana.mainloop()
```
$$CONSOLA$$
![[Pasted image 20230929123645.png|300]]

___
## 7- Menús
![](https://www.youtube.com/watch?v=Dv1ALaWwScI&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=52&ab_channel=pildorasinformaticas)

___
**Resumen**

El video explica cómo crear menús y submenús en Python usando el widget Menu de Tkinter. Se crea una barra de menú asignándola a una variable. Se agrega al root con .config(menu=). Se crean elementos de menú indicando nombre y barra padre. Se asignan Labels visibles con .add_cascade(). Se agregan submenús con .add_command() indicando texto. Se pueden poner separadores entre opciones. Se muestra un ejemplo con menú Archivo, Edición, Herramientas y Ayuda, con distintas opciones en cada uno.

**Lista de puntos importantes:**

- 01:43 - Crear barra de menú asignándola a variable 
- 02:15 - Agregar elementos indicando nombre y barra padre  
- 04:00 - Asignar Labels visibles con .add_cascade()
- 07:21 - Agregar submenús con .add_command()  
- 09:42 - Poner separadores entre opciones con .add_separator()
- 12:15 - Quitar barra separadora con tearoff=0

```python
import tkinter as tk
  
# Funciones para las opciones del menú
def abrir_archivo():
    # Aquí puedes agregar la lógica para abrir un archivo
    pass
  
def guardar_archivo():
    # Aquí puedes agregar la lógica para guardar un archivo
    pass
  
def acerca_de():
    # Aquí puedes mostrar información "Acerca de"
    pass
  
# Crear la ventana principal
ventana = tk.Tk()
ventana.title("Ejemplo de Menú con Tkinter")
  
# Crear la barra de menú
barra_menu = tk.Menu(ventana)
ventana.config(menu=barra_menu)
  
# Crear el menú "Archivo" con opciones
menu_archivo = tk.Menu(barra_menu, tearoff=0)
barra_menu.add_cascade(label="Archivo", menu=menu_archivo)
menu_archivo.add_command(label="Abrir", command=abrir_archivo)
menu_archivo.add_command(label="Guardar", command=guardar_archivo)
menu_archivo.add_separator()
menu_archivo.add_command(label="Salir", command=ventana.quit)
  
# Crear el menú "Ayuda" con una opción
menu_ayuda = tk.Menu(barra_menu)
barra_menu.add_cascade(label="Ayuda", menu=menu_ayuda)
menu_ayuda.add_command(label="Acerca de", command=acerca_de)
  
# Iniciar el bucle principal
ventana.mainloop()
```
$$CONSOLA$$
![[Pasted image 20230929135124.png|300]]


___
## 8- Ventanas emergentes
![](https://www.youtube.com/watch?v=xUGUglpaTJc&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=53&ab_channel=pildorasinformaticas)

___
**Resumen**:

El video explica cómo crear ventanas emergentes o popups en Python usando Tkinter. Se importa messagebox y se utiliza showinfo(), showwarning() o showerror() según necesidad. Se pasa título y mensaje. Con askquestion() muestra botones Sí/No. Con askokcancel() muestra Aceptar/Cancelar. Con askretrycancel() muestra Reintentar/Cancelar. Devuelven valor para ejecutar código según opción. Se muestra un ejemplo en menú de aplicación con distintos tipos de ventanas emergentes. Útiles para informar o pedir confirmación al usuario.

**Lista de puntos importantes: **

- 03:28 - Importar messagebox
- 04:10 - showinfo() para información
- 06:29 - showwarning() para advertencia 
- 08:19 - askquestion() para confirmar con Sí/No
- 11:14 - askokcancel() para confirmar con Aceptar/Cancelar
- 13:33 - askretrycancel() para confirmar con Reintentar/Cancelar
- 14:56 - Obtener valor devuelto para ejecutar código



```python
import tkinter as tk
from tkinter import messagebox
  
# Función para mostrar una ventana emergente de información
def mostrar_info():
    messagebox.showinfo("Información", "Esto es un mensaje informativo")
  
# Función para mostrar una ventana emergente de advertencia
def mostrar_advertencia():
    messagebox.showwarning("Advertencia", "¡Esto es una advertencia!")
  
# Función para mostrar una ventana emergente de confirmación con botones Sí/No
def mostrar_confirmacion():
    resultado = messagebox.askquestion("Confirmación", "¿Estás seguro?")
    if resultado == "yes":
        messagebox.showinfo("Resultado", "Has seleccionado Sí")
    else:
        messagebox.showinfo("Resultado", "Has seleccionado No")
  
# Función para mostrar una ventana emergente de confirmación con botones Aceptar/Cancelar
def mostrar_confirmacion_aceptar_cancelar():
    resultado = messagebox.askokcancel("Confirmación", "¿Deseas continuar?")
    if resultado:
        messagebox.showinfo("Resultado", "Has seleccionado Aceptar")
    else:
        messagebox.showinfo("Resultado", "Has seleccionado Cancelar")
  
# Función para mostrar una ventana emergente de confirmación con botones Reintentar/Cancelar
def mostrar_confirmacion_reintentar_cancelar():
    resultado = messagebox.askretrycancel("Confirmación", "Reintentar la operación?")
    if resultado:
        messagebox.showinfo("Resultado", "Has seleccionado Reintentar")
    else:
        messagebox.showinfo("Resultado", "Has seleccionado Cancelar")
  
# Crear la ventana principal
ventana = tk.Tk()
ventana.title("Ejemplo de Menú con Tkinter y Ventanas Emergentes")
  
# Crear botones para mostrar ventanas emergentes
boton_info = tk.Button(ventana, text="Mostrar Info", command=mostrar_info)
boton_advertencia = tk.Button(ventana, text="Mostrar Advertencia", command=mostrar_advertencia)
boton_confirmacion = tk.Button(ventana, text="Mostrar Confirmación", command=mostrar_confirmacion)
boton_confirmacion_aceptar_cancelar = tk.Button(ventana, text="Mostrar Confirmación Aceptar/Cancelar", command=mostrar_confirmacion_aceptar_cancelar)
boton_confirmacion_reintentar_cancelar = tk.Button(ventana, text="Mostrar Confirmación Reintentar/Cancelar", command=mostrar_confirmacion_reintentar_cancelar)
  
# Colocar los botones en la ventana
boton_info.pack()
boton_advertencia.pack()
boton_confirmacion.pack()
boton_confirmacion_aceptar_cancelar.pack()
boton_confirmacion_reintentar_cancelar.pack()
  
# Iniciar el bucle principal
ventana.mainloop()
```
$$CONSOLA$$
![[Pasted image 20230929140414.png|350]]


___
## 9- Ventana emergente Abrir/Guardar archivo 
![](https://www.youtube.com/watch?v=TmQZBzwIMGk&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS&index=54&ab_channel=pildorasinformaticas)

___


El video explica cómo crear en Python ventanas emergentes para que el usuario seleccione un archivo para abrir. Se utiliza filedialog.askopenfilename() indicando título. Devuelve la ruta del archivo elegido. Se puede establecer directorio inicial con initialdir y filtrar tipos de archivo con filetype especificando texto y extensión. Se muestra ejemplo con botón para abrir archivo mostrando ventana para buscar archivo Excel o texto en carpeta documentos. Muy útil para seleccionar archivo a procesar en aplicación.

Lista de puntos importantes:

- 03:14 - filedialog.askopenfilename() para ventana de apertura 
- 04:19 - Devuelve ruta del archivo seleccionado
- 06:32 - Establecer directorio inicial con initialdir
- 08:50 - Filtrar tipos de archivo con filetype 
- 10:38 - Permitir todos los archivos con *.* 
- 11:51 - Obtener ruta del archivo para después abrirlo


```python
import tkinter as tk
from tkinter import filedialog
  
# Funciones para las opciones del menú
def abrir_archivo():
    # Aquí puedes agregar la lógica para abrir un archivo
    pass
  
def guardar_archivo():
    ruta_archivo = filedialog.asksaveasfilename(
        title="Guardar Archivo",
        filetypes=[("Archivos de Texto", "*.txt"), ("Archivos Excel", "*.xlsx")]
    )
    if ruta_archivo:
        # Aquí puedes agregar la lógica para guardar el archivo en la ruta seleccionada
        print("Archivo guardado en:", ruta_archivo)
  
def acerca_de():
    # Aquí puedes mostrar información "Acerca de"
    pass
  
# Crear la ventana principal
ventana = tk.Tk()
ventana.title("Ejemplo de Menú con Tkinter")
  
# Crear la barra de menú
barra_menu = tk.Menu(ventana)
ventana.config(menu=barra_menu)
  
# Crear el menú "Archivo" con opciones
menu_archivo = tk.Menu(barra_menu, tearoff=0)
barra_menu.add_cascade(label="Archivo", menu=menu_archivo)
menu_archivo.add_command(label="Abrir", command=abrir_archivo)
menu_archivo.add_command(label="Guardar", command=guardar_archivo)
menu_archivo.add_separator()
menu_archivo.add_command(label="Salir", command=ventana.quit)
  
# Crear el menú "Ayuda" con una opción
menu_ayuda = tk.Menu(barra_menu)
barra_menu.add_cascade(label="Ayuda", menu=menu_ayuda)
menu_ayuda.add_command(label="Acerca de", command=acerca_de)
  
# Iniciar el bucle principal
ventana.mainloop()
```
$$CONSOLA$$
![[Pasted image 20230929141509.png]]


___

%%
tags:  #programación #pagfundamentospython #python  

Vínculos:   [[000-Menú Fundamentos Python 📃|Menú Fundamentos Python 📃]]
%%