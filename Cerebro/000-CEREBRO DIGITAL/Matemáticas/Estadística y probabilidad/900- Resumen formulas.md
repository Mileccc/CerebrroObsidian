---
ID: 900
-nombre: Resumen formulas
"-tags:":
---
___
# Resumen formulas
___

## Recta

$$\color{red}y=mx+b$$
$b= abscisa \;u\; ordenada\; al\; origen$
#### Pendiente
$$\color{cyan}m = \frac{y_{2}-y{1}}{x_{2}-x_{1}}$$
___
## Medidas de medición y dispersión
#### Media 
##### Poblacional
$$\color{orange}\mu=\sqrt{\frac{\sum^N_{i=1} x_{i} }{N} }$$
##### Muestral

$$\color{orange}\bar{x}=\sqrt{\frac{\sum^N_{i=1} x_{i} }{n} }$$
___
#### Varianza
##### Muestral
$$\color{\pink}s^2=\frac{\sum^n_{i=1}(x_{i}-\bar{x})^2}{n-1}$$
##### Poblacional
$$\color{\pink}\sigma^2=\frac{\sum^n_{i=1}(x_{i}-\mu)^2}{N}$$

___
#### Desviación estándar
##### Muestral
$$\color{\yellow }S_{x}=\sqrt{ \frac{\sum^n_{i=1}(x_{i}-\bar{x})^2}{n-1} }$$

##### Poblacional
$$\color{\yellow}\sigma=\sqrt{\frac{\sum^n_{i=1}(x_{i}-\mu)^2}{N}  }$$


#### Puntaje Z
$$\color{\purple}z=\frac{x-\mu}{\sigma}$$

#### Distribución Normal
![[Pasted image 20230912171755.png|700]]


$RIQ= \;rango \;intercuartil$

## Regresión Lineal

#### Datos numéricos bivariados
- $Variables \;dependientes: y$
- $Variables \;independientes: x$


#### Error de la recta
$$\hat{y}=mx+n$$
$$ce_{\mathrm{Re}cta}=(y_{n}-\hat{y})^2$$
$$ce_{\bar{y}}=(y_{n}-\bar{y})^2$$

##### Media de los errores al cuadrado o residuo promedio

$$\sqrt{\frac{ce_{Recta}}{n-1}}$$


##### Coeficiente de determinación

$$r^2=1-\frac{ce_{\mathrm{Re}cta}}{ce{ _{\bar{y}} }}$$


#### Coeficiente de correlación o residuo
$$\color{orange}r=\frac{1}{n-1}\sum \begin{bmatrix}
\frac{x_{i}-\bar{x}}{S_{x}}
\end{bmatrix}\begin{bmatrix}
\frac{y_{i}-\bar{y}}{S_{y}}
\end{bmatrix}$$

$$r^2=(\frac{1}{n-1}\sum \begin{bmatrix}
\frac{x_{i}-\bar{x}}{S_{x}}
\end{bmatrix}\begin{bmatrix}
\frac{y_{i}-\bar{y}}{S_{y}}
\end{bmatrix})^2$$ 

#### Ecuación de la recta de mínimos cuadrados
$$\color{orange}\hat{y}=r·\frac{S_{y}}{S_{x}}·x+b$$







![](https://www.youtube.com/watch?v=kYCyNrPToTc)


![](https://www.youtube.com/watch?v=wRqntzPxNXU)














___
%%
Vínculos:
[[000-Menú Estadística y probabilidad📃|Menú Estadística y probabilidad📃]]

Tags:
#matemáticas #pagestadística_y_probabilidad
%%