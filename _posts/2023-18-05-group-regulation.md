---
title: REGULACION EN GRUPO
date: 2023-03-18
categories: [TOPOLOGIAS, GROUP-REGULATION]
tags: [topologia, psu, groupRegulation]
author: aaron
---

## POR SI NO QUIERES LEER:

<p style="text-align:justify">La regulación en grupo está presente en muchas fuentes baratas, que no aseguran proteger por completo el ensamble ni a suministrar la energía de forma eficiente a tus componentes, por ende a una diferencia de 20-40 USD que tienen vs mejores fuentes, no deberían ser una opción a considerar para tu pc.</p>

## ¿QUÉ ES UNA TOPOLOGÍA?
<p style="text-align:justify">Tratando de ser lo más entendibles posibles, una topología es el método de regulación para los raíles de una fuente. Todas las fuentes se constituyen de 3 raíles primordiales; los cuales son:</p>

![topologia](/assets/posts/gr/topologia.webp){: w="600" h="400" .center}

## ¿CÓMO FUNCIONA?

<p style="text-align:justify">La regulación en grupo se compone primordialmente de 2 bobinas en el lado secundario (a partir de donde se despliegan los cables)
La bobina chica genera el raíl de 3.3v y la grande los de 5 y 12v, por lo cual se entiende que en situaciones de carga cruzada se dé un mal desempeño.
A continuación algunas muestras de la desviación en carga cruzada, más adelante encontrarán información sobre que valores son seguros para no causar un daño a las VRM de tus componentes.</p>

![example](/assets/posts/gr/psu-exa.webp){: w="600" h="400" .center}

## DESVIACIÓN

| | 12v | 5v | 3.3v |  | Watts | Eficiencia |
|-|-|-|-|-|-|-|
| CL1 | 4.000A | 13.003A | 13.001A | 0.001A | 155.059 | 78.886% |
| CL1 | 12.434V | 4.816V | 3.284V | 5.094V | 196.562 | 78.886% |
| CL2 | 43.524A | 1.000A | 1.002A | 0.001A | 512.010 | 82.401% |
| CL2 | 11.568V | 5.247V | 3.266V | 5.076V | 621.364 | 82.401% |

## ESTABILIDAD DE RAÍLES

<p style="text-align:justify">Es importante que los raíles estén correctamente regulados, eso es, que en escenarios de carga se "desvíen" lo menor posible y sigan entregando el voltaje adecuado, con un margen de +/-5% de desviación.
Estas medidas de seguridad se rigen por el estándar ATX, a continuación la tabla de voltajes más vigentes al momento (recién fue implementado el ATX 3.0), sin embargo este estándar aún no es cubierto totalmente.</p>

| Voltaje | Mínimo | Máximo |
|-|-|-|
| 12v | 11.4v | 12.6v |
| 5V | 4.75v | 5.25v |
| 3.3v |  3.135v | 3.465v |
| -5v | -5.5v | -4.5v |
| -12v | -13.2v | -10.8v |

## CONSECUENCIAS
<p style="text-align:justify">Que una fuente se acerque o sobrepase el umbral de desviación de voltaje, puede causar que a un plazo medio o largo, dañe las VRM de tus componentes, o si el caso es extremo, llega a apagarse en escenarios de carga. Sumado a otros aspectos como el rizo, es el motivo de que muchas fuentes no se recomiendan para las gráficas más recientes.
¿Y eso cómo afecta a la regulación en grupo?
Pues bueno, justamente es de las topologías más baratas y sencillas, a continuación mostraremos una lista de las PSU más comunes que son reguladas en grupo.</p>

## LISTA DE FUENTES

- Aerocool
  - Cylon, KCAS <=800W
- Corsair
  - CV <=550W, VS
- Cooler Master
  - Elite, Masterwatt Lite
- EVGA
- Gigabyte
  - B, BV, BT, N1, N2, W1
  - PB<=550W
- Seasonic
  - S1211
- Thermaltake
  - Smart SE, SE2, BM1, BX1<650w, TR2, GX2, GF

- **Nota: Estas fuentes SOLO comparten ser reguladas en grupo pero no son de la misma calidad, pueden consultar la tier list para más información. (Enlace en la publicación)**

CONCLUYENDO
<p style="text-align:justify">Considerando que una fuente regulada en grupo no sólo abarató en su plataforma y topología, si no también en otros componentes como el supervisor y ventiladores, en general no es una buena idea comprar una de estas PSU, especialmente por que su precio no es precisamente competitivo.</p>

