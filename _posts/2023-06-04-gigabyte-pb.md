---
title: Revisión Gigabyte P450B-P550B.
date: 2023-4-06
categories: [REVIEWS, GIGABYTE]
tags: [gigabyte, psu, revisión]
author: aaron
---

## ¿QUÉ SE REVISA?

En este orden se revisarán los siguientes elementos:

- Topología 
- Capacitor principal (Bulk cap) 
- Supervisor
- Componentes misceláneos 

`Material habilitado por nosotros;mostrando los elementos más.importantes de una forma sencilla.`

- Desviación
- Transient response
- Rizo
- Ruido y temperatura de operación

`Resultados provistos por Cybenetics dada la naturaleza del equipo requerido para llevar a cabo las pruebas`

## Topología

La encargada de regular los raíles de la fuente; muchas veces determina el sistema máximo recomendable así como los watts máximos.

![topologia](/assets/posts/gigabyte-pb/sample3.jpg){: w="600" h="400" .center}

Esto nos muestra que estamos ante una PSU de entrada, la cual vaa tener problemas con componentes de consumo elevado o picos de consumo notables. Ya que como pudieron ver en la guía de regulación en grupo; las 2 bobinas tratan de nivelar la carga entre ambos raíles de 5 y 12v, creando bastante desviación con daños a las VRM a largo plazo. 

![bobina](/assets/posts/gigabyte-pb/bobina.png){: w="600" h="400 .center"} 

## CAPACITOR

Denominado en inglés como "Bulk cap" , se encarga de filtrarla corriente y rectificarla; su calidad se mide primordiamente en: 
- Capacitancia (medida en micro faradios uF). 
- Voltaje de operación (V). 
- Rating de operación (°C).

### BULK CAP

Esta PSU cuenta con un capacitor de el fabricante TEAPO; a 4O0v,33OuF y rating a 85°C. Especificaciones bastante estándar; considerando que a su precio fuentes a 39OuF y 105°C,y con caps de Nichicon u otros fabricantes con mejores productos. 
Ya veremos más adelante como afecta a su performance:

![cap](/assets/posts/gigabyte-pb/cap.png){: w="600" h="400 .center"} 

## SUPERVISOR
El encargado de las protecciones de la fuente;es indispensable que sea eficiente y "rápido", los valores que se ajustan para activar la protección varían entre fabricantes.

A continuación el pinout del supervisor; rescatado desde la hoja de información provista por el mismo fabricante.

![super](/assets/posts/gigabyte-pb/supervisor.png){: w="600" h="400 .center"} 

Como podemos ver es un supervisor acorde a la gama; con parámetros dentro de lo común; sin embargo no cuenta con OTP (Over Temperature Protection) ni con protección ante fallas de ventilador; lo cual es una mala combinación:

PIN DESCRIPTION

| Pin Name| TYPE |Description| 
|-|-|-|
| PGI| I | Power good input signal pin |
| GND| P | Ground | 
| FPOB | O | Fault protection output pin, open drain output |
| PSONB | I | On/Off switch input | |
| IS12A | I | 12VA over current protection sense input |
| IS12AB | I | 12VA over current protection sense input | 
| RI| I | Current sense adjust input |
| V12B | I | 12VB overlunder voltage input pin | 
| IS12B | I | 12VB over currentprotection sense input | 
| IS5 | I | 5V over current protection sense input |
| IS33 | I | 3.3V over current protection sense input |
| V12A | I | 12VA overlunder voltage input pin |
| VCC2 | I | Current sense power supply | 
| V33 | I | 3.3V overlunder voltage input pin |
| V5 | I | 5V overlunder voltage input pin| 
| VCC | I | Power supply |
| PGO| O | Power good output signal pin, open drain output |

## OTROS COMPONENTES 

Algunas otras características de la PSU antes de pasar al apartado deperformance.

Dentro del resto de piezas se puede ver un intento de la marca por abaratar en costos; por ejemplo en la disipación; la cual es bastante sencilla; la plataforma y demás indican una elección "mediocre" la cual tendrá consecuencias de frente al performance y fiabilidad, sin contar que el precio resultante no es del todo competitivo. 

![global](/assets/posts/gigabyte-pb/global.png)

También se puede observar una calidad de soldadura bastante promedio; el ventilador promete ser "Fluid dynamic bearing", sin embargo es de `rodamiento de rifle`, y no es precisamente silencioso, principalmente dada la alta curva de ventilación puesta gracias a que le cuesta a los componentes operar con esa disipación.

![fan](/assets/posts/gigabyte-pb/fan.png) 

## RENDIMIENTO
Datos provistos por Cybenetics; solo agregaremos los por menores; pero tendrán un enlace directo a su web.

### DESVIACIÓN
Recordando que el máximo de desviación permitido por el estándar ATX es 5%, se puede ver que esta PSU en carga cruzada da los valores:

 - 3.9% en 12v 
 - 4.94% en 5v
 - 1.13% en 3.3

| CL | 12V | 5V | 3.3V | 
|-|-|-|-|
| CL1 | 4.000A | 13.003A | 13.001A |
| CL1 | 12.434V | 4.816V | 3.284V |
| CL2 | 43.524A | 1.000A | 1.002A |
| CL2 | 11.568V | 5.247V | 3.266V |


### TRANSIENT RESPONSE
La respuesta transitoria/transitiva; se podría ver como el tiempo que le toma a la fuente adaptarse a los cambios de consumo abruptos, algo indispensable dado que los mayores consumos de las gráficas se dande 10 a 1ms.
A 50% de carga y en 1Oms (escenario bastante común) se puede ver que el rail de 3.3v son los más afectados; siendo el último el que prácticamente no pasa prueba alguna, sin embargo el de 12v tampoco tiene un comportamiento adecuado. 

Advanced Transient Response at 50% - 1Oms

| Voltage | Before | After | Change| Pass |
|-|-|-|-|-|
| 12V | 12.043V | 11.625V | 3.25% | Pass |
| 5V | 5.052V | 4.826V | 4.47% | Pass |
| 3.3V | 3.285V | 2.971V | 9.56% | Fail |
| 5VSB | 5.028V | 4.937V | 1.81% | Pass | 

## RIZO

El rizo es la corriente alterna que no se filtra correctamente y llega a los componentes. El estándar ATX permite como máximo 120mV, sin embargo no es recomendable acercarse a esos valores. El rizo también aumenta con la carga. Centrándose en el raíl de 12V. si bien `"pasa"` la prueba, en carga cruzada (que es el caso de un ensamble) tiene un rizo demasiado alto y junto a su desviación, representa un daño a la larga a las VRM de la GPU y motherboard 

| 90% Load | 54.2OmV |
|-|-|
| 100% Load | 79.2OmV |
| 110% Load | 108.5Omv |
| Crossload1 | 19.20mV |
| Crossload2 | 87.2OmV |

## RATING DE OPERACIÓN

La fuente menciona tener un rating de operación a 40°C, algo apto para la gama, pero ahora observemos la primera fila de pruebas de carga, la cual es al 10% solamente. 
Se tiene un ventilador a 1303 RPM, produciendo 34.1 dB, algo muy audible y que aumentará hasta 48 dB según la carga, y aún con el ventilador a altas revoluciones, ya está a 36.17°C internamente.
Recordemos que no está bajo carga, y mantener los componentesa altas temperaturas afecta a la eficiencia y tiempo de vida.

| DC/AC (Watts) | Efficiency | Fan Speed (RPM) | PSU Noise (dB[A]) | Temps (In/Out) | 
|-|-|-|-|-|
| 54.966 | 77.695% | 1303 | 34.1 | 36.17°C
| 70.746 | | | |            38.39°C |

## VEREDICTO

Como ya se podía esperar y dado que elegimos esta fuente para el tier F en la tier list, no la recomendamos para ninguna clase de ensamble por su desempeño; y además, por su precio que no permite que sea una opción viable. Pueden revisar la lista para conocer mejores opciones. [aqui](https://psugang.github.io/posts/psu-tierlist/)
