# Taller #2
Se presentan los resultados del Taller #2 del curso de Introducción a la Ciencia de Datos.

## Pregunta a Responder
**Es posible estimar si habrá un cambio en el partido con mayor cantidad de votos para las elecciones del Senado Colombiano por cada departamento?**

## Datos Utilizados
Los datos utilizados fueron obtenidos a partir del **MOE** (Misión de Observación Electoral) y la Registraduría Nacional del Estado Civil de Colombia.

Los datos, ya limpios, consisten de 5 columnas: departamento, partido con mayor número de votos, votos, sufragantes totales y porcentaje de votos correspondientes al partido mayoritario. Un extracto ejemplo de los datos correspondientes a las elecciones del 2014 se presenta a continuación:

| Departamento | Partido | Votos | Sufragantes | Porcentaje |
| :---: | :---: | :---: | :---: | :---: |
| Bogotá D.C. | Centro Democrático | 373798 | 1844016 | 20.27 |
| Antioquia | Centro Democrático | 436896 | 1692837 | 25.80 |
| Atlántico | Partido Conservador | 256433 | 888027 | 21.17 |
| Cundinamarca | Centro Democrático | 133349 | 737392 | 18.08 |
| Santander | Partido Liberal | 149942 | 733111 | 20.45 |
| Valle del Cauca | Partido de la U | 181852 | 1217266 | 14.93 |

## Procedimiento

Inicialmente, tomando los datos de las elecciones del 2014 y del 2018, se compararon los partidos con mayor cantidad de votos en cada departamento y, si éste era diferente se asignaba el valor de 0, o 1 de lo contario. Asimismo, se obtuvo la diferencia entre la fracción de votos que el partido mayoritario obtuvo en cada caso. Así, por medio de una regresión logística, se obtuvo el siguiente modelo:

<p align="center">
  <img src="https://github.com/MiguelPerilla2233/Proyecto2/blob/main/results/model.png?raw=true">
</p>

## Resultados

