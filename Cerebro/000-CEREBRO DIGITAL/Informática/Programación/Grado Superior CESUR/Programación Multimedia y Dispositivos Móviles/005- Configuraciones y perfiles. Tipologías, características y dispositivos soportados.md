---
ID: 5
nombre: Configuraciones y perfiles_tipologías, características y dispositivos soportados
tags:
  - pagprogramación_multimedia_y_dispositivos_móviles
---
___

[![](https://mermaid.ink/img/pako:eNpVkMtqwzAQRX9FzCoBY_ySX7uSZNFS00C7Kt5MbCUVjSRHlkpT46_KJ-THqjxpdzPnXIbhDtColkEJgstWYFdLQrRSZjJ5iqoFedA7yw1rjNU4nZ4kITMl13zjQMOPB3lhjj7PZ7eZkOp4-OJb1t_tX_mGqy0zV7fUau2SN1s9zpdXgTvLDOvJS9dwJdFdAw8E0wJ56x4eTrEazAcTrIbSjS3qzxpqObocWqNe97KB0mjLPLBdi4bNOW40iv9w0XKjNJRr3PYOsvNaXVo5l-NBh_JdKXHPuB3KAb6hDKmfBzROsiSJ0igtaOzB3uEo96O4CIs0y7I4iTM6evBzPhH6QZ7QPCzigEZZHoZ0_AU9MnZr?type=png)](https://mermaid.live/edit#pako:eNpVkMtqwzAQRX9FzCoBY_ySX7uSZNFS00C7Kt5MbCUVjSRHlkpT46_KJ-THqjxpdzPnXIbhDtColkEJgstWYFdLQrRSZjJ5iqoFedA7yw1rjNU4nZ4kITMl13zjQMOPB3lhjj7PZ7eZkOp4-OJb1t_tX_mGqy0zV7fUau2SN1s9zpdXgTvLDOvJS9dwJdFdAw8E0wJ56x4eTrEazAcTrIbSjS3qzxpqObocWqNe97KB0mjLPLBdi4bNOW40iv9w0XKjNJRr3PYOsvNaXVo5l-NBh_JdKXHPuB3KAb6hDKmfBzROsiSJ0igtaOzB3uEo96O4CIs0y7I4iTM6evBzPhH6QZ7QPCzigEZZHoZ0_AU9MnZr)
El texto detalla la arquitectura de Java 2 Micro Edition (J2ME) utilizada tanto en dispositivos móviles como en sistemas informáticos de dimensiones reducidas. La arquitectura se divide en tres capas principales:

### 1. Configuration

Esta capa es el núcleo donde reside la máquina virtual y clases adicionales. Hay dos tipos de configuraciones:

- **CLDC (Connected Limited Device Configuration)**: Específica para dispositivos móviles.
- **CDC (Connected Device Configuration)**: Adecuada para tablets.

#### Restricciones en CLDC:

- **Memoria ROM**: Entre 128 KB y 512 KB.
- **Procesador**: 16 o 32 bits, velocidad ≥ 25 MHz.
- **Conexión**: WiFi o a través del proveedor de servicios.

### 2. Profile

Es la capa intermedia que proporciona librerías para el desarrollo de código. En el contexto de CLDC, se introduce el concepto de **MIDP (Mobile Information Device Profile)**, que ofrece librerías necesarias para la implementación de aplicaciones para dispositivos móviles.

#### Restricciones en MIDP:

- **Tamaño de Pantalla**: 96 x 54.
- **Sistema de Entrada**: Pantalla táctil o teclado.
- **Capacidad de Memoria**: 256 KB (CLCD), 8 KB (almacenamiento), 128 KB (memoria no volátil).

### 3. Optional Packages

Esta capa contiene paquetes opcionales que pueden ser ejecutados en ciertos dispositivos pero no en otros, añadiendo funcionalidades extra no presentes en la capa 'Profile'.

**En conclusión**, el texto ofrece una visión completa de cómo está organizada la arquitectura J2ME y las restricciones y funcionalidades que cada capa impone o añade en el contexto del desarrollo de aplicaciones para dispositivos móviles.


___
%%
tags: #pagprogramación_multimedia_y_dispositivos_móviles #Java2MicroEdition #J2ME #DesarrolloMóvil #Arquitectura #Configuration #CLDC #CDC #Profile #MIDP #OptionalPackages #Restricciones #CapacidadDeMemoria #Conexión #Procesador #TamañoDePantalla #SistemaDeEntrada
Vínculos:  [[000-Menú Programación Multimedia y Dispositivos Móviles 📃|Menú Programación Multimedia y Dispositivos Móviles 📃]]
%%