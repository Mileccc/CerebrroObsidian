---
ID: 7
nombre: Clasificación de Computadoras Taxonomía de Flynn
tags:
  - pagprogramación_de_servicios_y_procesos
"Vínculos:":
---
___
[![](https://mermaid.ink/img/pako:eNpdks9um0AQxl9lNadEopYxBByudf74QFuJniouU5ikq7KzaFmU2JYfpg_QU2-58mIZ42LZ4bTzfd_8djTsDipbE2RgNNcG25KVctb6q6vv-GrZmuEvqprUfbNhvr4-2Erl0tLYTn2xn76hw2YsrCqo6okrLUJ3DE5RVayL1SSps-CHWH4Ry4e3xutWaGrNnXd9VWnLE3sa4jTB1Fis8zPI3ZOuNLGn01UX9gMxSb_ajEHcHp3PtvP0X9PjpOfwTOXEcvMjuvoF3QVZvOFPJwAzvLEQ6Iz61T0j6y1WevjHh6U2KCRjnUZFfDHYJAunRed1jR-dlZaN6J-9WBCAIWdQ1_Ifd4dgCf4XGSohk2ON7ncJJe8lh723xYYryGSdFEDf1uhppfHZoYHsCZvupN7V2lt3Emks8-NrGR9NAC3yD2vNRJMSsh28QhYvZ-EyidM0ScIwWizDADaQhYtklkbxPEzicBnfpPNoH8B2BMxnt9HiNozn8kVxehOl-3ckYdF8?type=png)](https://mermaid.live/edit#pako:eNpdks9um0AQxl9lNadEopYxBByudf74QFuJniouU5ikq7KzaFmU2JYfpg_QU2-58mIZ42LZ4bTzfd_8djTsDipbE2RgNNcG25KVctb6q6vv-GrZmuEvqprUfbNhvr4-2Erl0tLYTn2xn76hw2YsrCqo6okrLUJ3DE5RVayL1SSps-CHWH4Ry4e3xutWaGrNnXd9VWnLE3sa4jTB1Fis8zPI3ZOuNLGn01UX9gMxSb_ajEHcHp3PtvP0X9PjpOfwTOXEcvMjuvoF3QVZvOFPJwAzvLEQ6Iz61T0j6y1WevjHh6U2KCRjnUZFfDHYJAunRed1jR-dlZaN6J-9WBCAIWdQ1_Ifd4dgCf4XGSohk2ON7ncJJe8lh723xYYryGSdFEDf1uhppfHZoYHsCZvupN7V2lt3Emks8-NrGR9NAC3yD2vNRJMSsh28QhYvZ-EyidM0ScIwWizDADaQhYtklkbxPEzicBnfpPNoH8B2BMxnt9HiNozn8kVxehOl-3ckYdF8)
La taxonomía de Flynn es una clasificación de computadoras basada en su flujo de instrucciones y datos. Los modelos que se destacan son SISD, SIMD, MISD y MIMD. El modelo SISD corresponde a la programación secuencial y no explora el paralelismo. 
### 🔄 Modelos No-Paralelos o Secuenciales

- **Modelo SISD**: Este modelo se alinea con la programación secuencial, donde un único conjunto de instrucciones opera en un solo conjunto de datos. No se aprovecha el paralelismo en este enfoque.

- **Modelo MISD**: En este caso, se utilizan múltiples flujos de instrucciones que trabajan simultáneamente en un solo conjunto de datos.

En esencia, mientras que el modelo SISD se centra en un enfoque secuencial sin paralelismo, el modelo MISD permite múltiples instrucciones para trabajar en el mismo conjunto de datos.

### 🌐 Modelos Paralelos: SIMD vs MIMD

En el ámbito de la programación paralela, los modelos SIMD y MIMD son los más relevantes. SIMD es eficiente en términos de hardware y tiempo de inicio para la comunicación entre procesadores, pero no permite la ejecución de diferentes instrucciones simultáneamente. En contraste, MIMD es más general y eficaz, siendo el más utilizado en la computación paralela. 

### 💰 Coste y Eficiencia

Aunque los sistemas SIMD requieren menos hardware, los sistemas MIMD generalmente tienen un coste inferior y son más eficaces, lo que los hace más comunes en aplicaciones de computación paralela.

### 🧠 Organización de la Memoria en MIMD

Los sistemas MIMD pueden ser de dos tipos según la organización del espacio de direcciones de memoria: 
- **Memoria Compartida**: Todos los procesadores acceden al mismo espacio de direcciones.
- **Memoria Distribuida**: Cada procesador tiene su propia memoria a la que solo él puede acceder.

En resumen, entender la taxonomía de Flynn y las diferencias entre los modelos paralelos como SIMD y MIMD es crucial para seleccionar la arquitectura más adecuada para proyectos de computación paralela.

___
%%
tags:  #pagprogramación_de_servicios_y_procesos  #TaxonomíaDeFlynn #ModelosParalelos #ModelosNoParalelos #SIMD #MIMD #SISD #MISD #ProgramaciónParalela #ProgramaciónSecuencial #CosteYEficiencia #MemoriaCompartida #MemoriaDistribuida
Vínculos:  [[000-Menú Programación de servicios y procesos 📃|Menú Programación de servicios y procesos 📃]]
%%