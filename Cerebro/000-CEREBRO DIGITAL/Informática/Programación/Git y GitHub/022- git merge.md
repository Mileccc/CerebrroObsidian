---
"ID:": 22
nombre: git merge
tags:
  - paggitygithub
"Vínculos:": "[[000- Menú Git y GitHub]]"
---
___
## Git merge
La fusión es la forma que tiene Git de volver a unir un historial bifurcado. El comando `git merge` permite tomar las líneas independientes de desarrollo creadas por `git branch` e integrarlas en una sola rama.

Ten en cuenta que todos los comandos presentados a continuación se fusionan en la rama actual. La rama actual se actualizará para reflejar la fusión, pero la rama de destino no se verá afectada en absoluto. Una vez más, esto significa que `git merge` se suele utilizar junto con `git checkout` para seleccionar la rama actual y `git branch -d` para eliminar la rama de destino obsoleta.

## Funcionamiento

---

`git merge` combinará varias secuencias de confirmaciones en un historial unificado. En los casos de uso más frecuentes, `git merge` se utiliza para combinar dos ramas. Los ejemplos siguientes del presente documento se centrarán en este patrón de fusión de ramas. En estos casos, `git merge` toma dos punteros de confirmación, normalmente los extremos de la rama, y encuentra una confirmación base común entre ellos. Una vez que Git encuentra una confirmación base en común, crea una "confirmación de fusión" nueva que combina los cambios de cada secuencia de confirmación de fusión puesta en cola.

Supongamos que tenemos una rama de función nueva que se basa en la rama `main`. Ahora, queremos fusionar esa rama de función con la rama `main`.

![[Pasted image 20231028104530.png|1000]]

Al invocar este comando, la rama de función especificada se fusionará con la rama actual, la cual asumiremos que es la `main`. Git determinará el algoritmo de fusión automáticamente (véase más adelante).

![[Pasted image 20231028104606.png|1400]]
Las confirmaciones de fusión son únicas con respecto a otras confirmaciones en el hecho de que tienen dos confirmaciones principales. Al crear una confirmación de fusión, Git tratará de fusionar automáticamente los historiales independientes. Sin embargo, si encuentra datos que se han cambiado en ambos historiales, no podrá combinarlos de ese modo. En ese caso, se crea un conflicto de control de versiones y Git solicitará la intervención del usuario para poder continuar.

## Preparación para fusionar

---

Antes de ejecutar una fusión, hay un par de pasos de preparación que llevar a cabo con el fin de garantizar que la fusión se realice sin problemas.

## Confirmación de la rama de recepción

---

Ejecuta `git status` para asegurarte de que `HEAD` apunte a la rama de fusión-recepción correcta. En caso necesario, ejecuta `git checkout`  para cambiar a la rama de recepción. En nuestro caso, ejecutaremos `git checkout main`.

## Recuperación de las últimas confirmaciones remotas

---

Asegúrate de que la rama de recepción y la rama de fusión están actualizadas con los cambios remotos más recientes. Ejecuta `git fetch` para incorporar los cambios de las confirmaciones remotas más recientes. Una vez que la recuperación se haya completado, asegúrate de que la rama `main` tenga las actualizaciones más recientes mediante la ejecución del comando `git pull`.

## Fusión

---

Una vez adoptados los pasos comentados anteriormente de "preparación para la fusión", se puede iniciar una fusión ejecutando `git merge`  donde  es el nombre de la rama que se fusionará con la rama de recepción.

## Fusión de avance rápido

---

Puede que se produzca una fusión con avance rápido cuando hay un proceso lineal desde el extremo de la rama actual hasta la rama de destino. En lugar de fusionar “realmente” las ramas, lo único que tiene que hacer Git para integrar los historiales es mover el extremo de la rama actual al extremo de la rama de destino (es decir, realizar un “avance rápido”). De este modo, combina de manera eficaz los historiales, ya que todas las confirmaciones alcanzables desde la rama de destino están ahora disponibles a través de la rama actual. Por ejemplo, una fusión con avance rápido de una rama de función en una `main` se vería de la siguiente manera:


![[Pasted image 20231028105139.png|1200]]


Sin embargo, no es posible una fusión con avance rápido si las ramas han divergido. Cuando no hay un proceso lineal hacia la rama de destino, Git no tiene más opción que combinarlas mediante una fusión de 3 vías. Las fusiones de 3 vías utilizan una confirmación específica para unir dos historiales. Esta fusión recibe su nombre del hecho de que Git utiliza tres confirmaciones para generar la confirmación de fusión: los dos extremos de la rama y su predecesor común.

![[Pasted image 20231028105208.png|1200]]


Aunque se pueden utilizar cualquiera de estas estrategias de fusión, a muchos desarrolladores les gusta utilizar las fusiones con avance rápido (facilitadas a través del comando [rebasing](https://www.atlassian.com/es/git/tutorials/rewriting-history/git-rebase)) para funciones pequeñas o correcciones de errores, mientras que se reservan las fusiones de tres vías para la integración de funciones con una ejecución de mayor duración. En este último caso, la confirmación de fusión resultante sirve como una unión simbólica de las dos ramas.

Nuestro primer ejemplo muestra una fusión con avance rápido. El código a continuación crea una rama nueva, le añade dos confirmaciones y, seguidamente, la integra en la línea principal con una fusión con avance rápido.

```bash
# Start a new feature 
git checkout -b new-feature main 
# Edit some files 
git add <file> 
git commit -m "Start a feature" 
# Edit some files 
git add <file> 
git commit -m "Finish a feature" 
# Merge in the new-feature branch 
git checkout main 
git merge new-feature 
git branch -d new-feature
```

Se trata de un flujo de trabajo común para las ramas temáticas transitorias que se utilizan más como un desarrollo aislado que como una herramienta de organización para funcionalidades con una ejecución de mayor duración.

Ten en cuenta también que Git no debería quejarse sobre el comando `git branch -d`, ya que ahora se puede acceder a la nueva función desde la rama principal.

En caso de necesitar una confirmación de fusión durante una fusión con avance rápido para mantener registros, es posible ejecutar `git merge` con la opción `--no-ff`.

```bash
git merge --no-ff <branch>
```

Este comando fusiona la rama especificada en la rama actual, pero siempre genera una confirmación de fusión (incluso si se trata de una fusión con avance rápido). Esto resulta útil para documentar todas las fusiones que tienen lugar en tu repositorio.

## Fusión de 3 vías

---

El siguiente ejemplo es muy similar, pero requiere una fusión de tres vías porque la rama `main` ha avanzado mientras la función se está desarrollando. Este es un caso habitual con funciones grandes o cuando hay varios desarrolladores trabajando en un proyecto simultáneamente.

```bash
# Start a new feature 
git checkout -b new-feature main 
# Edit some files 
git add <file> 
git commit -m "Start a feature" 
# Edit some files 
git add <file> 
git commit -m "Finish a feature" 
# Develop the main branch 
git checkout main 
# Edit some files 
git add <file> 
git commit -m "Make some super-stable changes to main" 
# Merge in the new-feature branch 
git merge new-feature 
git branch -d new-feature
```

Ten en cuenta que es imposible que Git lleve a cabo una fusión con avance rápido, ya que no hay forma de mover la rama `main` a la de `new-feature` sin retroceder.

En la mayoría de los flujos de trabajo, la rama de `new-feature` sería una función muy grande que ha tardado mucho en desarrollarse, por lo que, mientras tanto, se han ido incorporando nuevas confirmaciones a la rama `main`. Si tu rama de función fuera en realidad tan pequeña como la del ejemplo anterior, probablemente sería mejor que la fusionases mediante cambio de base a la rama `main` y que hicieses una fusión con avance rápido. Esto evitaría que apareciesen confirmaciones de fusión superfluas en el historial del proyecto.

## Resolución de conflicto

---

Si las dos ramas que tratas de fusionar han cambiado la misma parte del mismo archivo, Git no podrá averiguar qué versión utilizar. Cuando esto ocurre, Git se detiene justo antes de la confirmación de fusión para que puedas resolver los conflictos manualmente.

Algo muy interesante del proceso de fusión de Git es que utiliza el conocido flujo de trabajo de edición, preparación y confirmación para resolver los conflictos de fusión. Cuando se observa un conflicto de fusión, la ejecución del comando `git status` muestra qué archivos se deben resolver. Por ejemplo, si en ambas ramas se ha modificado la misma sección de `hello.py`, se vería algo parecido a esto:

```bash
On branch main
Unmerged paths:
(use "git add/rm ..." as appropriate to mark resolution)
both modified: hello.py
```

## Cómo se presentan los conflictos

---

Si Git encuentra un conflicto durante una fusión, editará el contenido de los archivos afectados con indicadores visuales que marquen ambas caras del contenido conflictivo. Estos marcadores visuales son: <<<<<<<, =======, y>>>> >>>. Es útil buscar estos indicadores en un proyecto durante una fusión para saber dónde hay que resuelto los conflictos.

```bash
here is some content not affected by the conflict 
<<<<<<< main this is conflicted text from main 
======= this is conflicted text from feature branch 
>>>>>>> feature branch;
```

Normalmente, el contenido que se encuentra delante del marcador ``-=======`` es la rama de recepción y el de la parte de detrás es la rama de fusión. 
Una vez identificadas las secciones conflictivas, puedes entrar y arreglar la fusión a tu gusto. Cuando estés listo para terminar la fusión, lo único que tienes que hacer es ejecutar `git add` en los archivos conflictivos para indicar a Git que se han resuelto. Seguidamente, ejecutas un `git commit` normal para generar la confirmación de fusión. El proceso es exactamente el mismo que el de la confirmación de una instantánea normal, lo que significa que es fácil para los desarrolladores habituales gestionar sus propias fusiones.

Ten en cuenta que los conflictos de fusión solo se producirán en el caso de una fusión de 3 vías. Los cambios conflictivos en una fusión de avance rápido no son posibles.

## Resumen

---

Este documento es un resumen del comando `git merge`. La fusión es un proceso esencial cuando se trabaja con Git. Hemos hablado de los mecanismos internos que hay detrás de una fusión y de las diferencias entre una fusión con avance rápido y una de 3 vías auténtica. Algunas de las principales conclusiones son las siguientes:

1. La fusión en Git combina secuencias de confirmaciones en un solo historial unificado de confirmaciones.

2. En Git hay, principalmente, dos tipos de fusión: con avance rápido y de tres vías.

3. Git permite fusionar las confirmaciones automáticamente salvo que haya cambios que entren en conflicto en ambas secuencias de confirmación.

Este documento ha integrado y hecho referencia a otros comandos de Git como, por ejemplo: [git branch](https://www.atlassian.com/es/git/tutorials/using-branches), [git pull](https://www.atlassian.com/es/git/tutorials/syncing/git-pull) y [git fetch](https://www.atlassian.com/es/git/tutorials/syncing/git-fetch). Para obtener más información sobre ellos, visita sus respectivas páginas.

https://www.atlassian.com/es/git/tutorials/using-branches/git-merge


### Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ylE8cm3mb0?si=oyaVxsCDqIO72L9J&amp;start=8068" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

___
%%
tags:  #paggitygithub  #Git #merge #gitBranch #gitCheckout #gitBranch-d #gitMerge #Funcionamiento #gitStatus #gitFetch #gitPull #PreparaciónParaFusionar #ConfirmaciónDeLaRamaDeRecepción #RecuperaciónDeLasÚltimasConfirmacionesRemotas #Fusión #FusiónDeAvanceRápido #gitMerge--no-ff #FusiónDe3Vías #ResoluciónDeConflicto #CómoSePresentanLosConflictos #gitAdd #gitCommit #Resumen
Vínculos: [[000- Menú Git y GitHub|Menú Git y GitHub]]
%%


