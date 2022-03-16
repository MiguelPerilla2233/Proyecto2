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

Inicialmente, tomando los datos de las elecciones del 2014 y del 2018, se compararon los partidos con mayor cantidad de votos en cada departamento, asignando el valor de 0 si hubo un cambio en el mismo y 1 de lo contrario. Esto se representa en la siguiente lista:

```python
[1., 1., 1., 1., 1., 0., 1., 0., 0., 1., 1., 0., 1., 0., 0., 1., 1.,
       0., 0., 1., 0., 0., 0., 0., 1., 1., 1., 1., 1., 1., 1., 1., 1.]
```

Asimismo, se obtuvo la diferencia porcental de votos que el partido mayoritario obtuvo en cada caso. Con esto, obtenemos la siguiente gráfica:

<p align="center">
  <img src="https://github.com/MiguelPerilla2233/Proyecto2/blob/main/results/data.png?raw=true">
</p>

Ahora, queremos hacer una regresión logística para ajustar los datos. Para esto, se utilizó el método de Metropolis Hastings, obteniendo así una distribución de probabilidad para los coeficientes de la regresión:

<p align="center">
  <img src="https://github.com/MiguelPerilla2233/Proyecto2/blob/main/results/alphasbetas.png?raw=true">
</p>

Entonces, teniendo estas distribuciones de probabilidad, se obtuvo el valor medio como el mejor estimado, teniendo los siguientes valores para el caso en particular:

```python
alpha_mean = 0.80437705893299
beta_mean = -2.2899558310652495
```

Así, por utilizando los coeficientes obtenidos para la regresión logística, se obtuvo el siguiente modelo:

<p align="center">
  <img src="https://github.com/MiguelPerilla2233/Proyecto2/blob/main/results/model.png?raw=true">
</p>

Ya teniendo el mismo, se realizó el mismo procedimiento para los datos de las elecciones del 2022, evaluándolos en el modelo ya obtenido:

```python
[0., 1., 1., 1., 1., 0., 1., 0., 0., 1., 0., 1., 0., 0., 0., 0., 0.,
       0., 0., 1., 0., 1., 0., 0., 1., 0., 1., 0., 0., 1., 0., 1., 1.]
```

Así, se calculó la siguiente matriz de confusión:

<p align="center">
  <img src="https://github.com/MiguelPerilla2233/Proyecto2/blob/main/results/confusion_matrix.png?raw=true">
</p>

Con los siguientes parámetros:

```python
Exactitud: 0.6666666666666666
Precisión: 0.5714285714285714
Cobertura (Recall): 0.8571428571428571
```

Y los F1-Score correspondientes:

```python
F1-Score (0): 0.6451612903225806
F1-Score (1): 0.6857142857142857
```

Asimismo, se realizaron curvas de precisión vs cobertura (recall) y de F1-Score vs Probabilidad:

<p align="center">
  <img src="https://github.com/MiguelPerilla2233/Proyecto2/blob/main/results/recall_precision.png?raw=true">
</p>

<p align="center">
  <img src="https://github.com/MiguelPerilla2233/Proyecto2/blob/main/results/probability_f1score.png?raw=true">
</p>

## Resultados

Se obtuvo un modelo capaz de predecir, con una precisión del 57%, si habrá un cambio en el partido que mayor cantidad de votos tenga, para las elecciones del Senado Colombiano, en cada departamento. Para el caso de las elecciones legislativas del 2022, los resultados son los sse resumen en el siguiente mapa:

<!--- https://simplemaps.com/custom/country/jpO8h3sO#states --->

<p align="center">
  <img src="https://github.com/MiguelPerilla2233/Proyecto2/blob/main/results/map.png?raw=true">
</p>

Donde se muestran en verde claro los departamentos dónde el modelo predijo que sí habría un cambio y lo hubo, en verde oscuro en los que el modelo predijo que no habría un cambio y no lo hubo, en rojo claro en los que el modelo predijo que sí habría un cambio y no lo hubo y en rojo oscuro en los que el modelo predijo que no habría un cambio y sí lo hubo.
