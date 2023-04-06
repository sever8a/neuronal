# Aprendizaje no supervisado

Por lo general, los datos que se obtienen del mundo real **no están etiquetados**. Para extraer información a partir de estos datos se pueden utilizar algoritmos de aprendizaje no supervisado. En lugar de realizar procesos de etiquetado (manual o atomático).

Son algoritmos de Machine Learning basados en funciones estadísticas y matemáticas.

# Reducción de la dimensionalidad

El objetivo de estos algoritmos es reducir el número de características de un dataset, para hacerlo asequible para emplear otro algoritmo, o para facilitar la interpretación por una persona. 


# Asociación de datos. Asociación

Se pretende descubrir asociaciones entre características, de manera que se pueden evidenciar relaciones entre items. Por ejemplo, analizando los detalles de todos los tickets de compra, se obtiene que el producto (cerveza), está asociado con otro (pañales).

***A priori***, es un algoritmo de asociacion que permite desvelar la relación entre diferentes elementos del dataset.

# Categorización de datos. Clustering

*Organizar automáticamente datos en categorías similares entre ellas y distintas de las demás.*

Se utilizan en problemas donde es necesario conocer qué objetos se parecen o agrupan por similitud. Para ello se utilizan las técnicas de **clustering** consiguiendo una segmentación automática en grupos de datos.

info: "Atención"
    Las características de referencia de cada categoria (clustering) no deben ser usadas para el agrupamiento.

![No supervisado](https://bookdown.org/dparedesi/data-science-con-r/img/kmeans-centers.png)

Este tipo de problema consiste en realizar agrupaciones de los elementos. En cada agrupamiento hay que identificar alguna característica que permita caracterizar al cluster (recetas con alto contenido en sal, bajas calorias, ...)

Los items de referencia de una categoría, determinan el agrupamiento en el que se situan. Se puede generalizar, considerando al resto de elementos de la misma categoría: ***elementos de la misma tipología***.

La dificultad del clustering es: determinar en cuantas categorías se pueden asociar los datos. En función de este valor, se obtendrán diferentes categorizaciones posibles.

![Algoritmos de clustering](https://scikit-learn.org/stable/_images/sphx_glr_plot_cluster_comparison_001.png)

## Algorítmo Esperanza-Maximización (EM)

Se usa para encontrar estimadores de máxima verisimilitud de parámetros. Es un proceso iterativo para maximizar verosimilitud en presencia de datos faltantes. Cada iteración consiste de dos pasos:

* Calcular el valor esperado de la log-verosimilitud promediando sobre datos faltantes con una aproximación de la solución.

* Obtener una nueva aproximación maximizando la cantidad resultante en el paso previo.


## Algoritmo K-means

Este algoritmo necesita saber cuántos grupos se quieren conseguir con los datos existentes. 

Es necesario determinar las características relevantes que se van a utilizar para la clasificación.

También se pueden valorar las características más relevantes.

Con los datos del dataset también se puede crear un batch-centroid, que corresponde a los datos de un cluster.


# Funciones para determinar el número óptimo de clusters

La función Silueta, es la más utilizada para determinar cuántos clusters se deben establecer con los datos.

Se prueba con varios valores para el número de agrupaciones, y se compara la métrica silueta. Por lo general, se consigue determinar cuál es el valor óptimo de agrupamientos.

En este caso es necesario seleccionar **indicadores** que permitan evidenciar si el número de cluster elegido es el más adecuado para los datos disponibles.

# Los datos importantes

Las caracteristicas de los datos del dataset, pueden determinar el resultado que se obtiene con el algoritmo. Es importante recordar los tipos de datos que nos podemos encontrar:

- Binarios. Valores con dos posibilidades de respuesta.
- Nominales. Textos.
- Ordinales. Valores que dependen de una escala.
- Numéricos. Valores numéricos que tienen un sentido total en el dato.

La codificación de los datos también es importante, ya que las técnicas que se aplican en estos algoritmos se basan en funciones estadísticas y matemáticas. 

Tanto los datos ordinales como los binarios, pueden codificarse para estar representados en el dataset de una manera adecuada para su procesamiento. *One hot encoding* o *creación de escalas progresivas* son algunas de las técnicas que se pueden emplear.


## La normalización

Como puede haber datos de diferente naturaleza, y los algoritmos se basan en el cálculo de las distancias entre los elementos. La existencia de valores dispares en escala entre diferentes características, pueden sesgar la distancia entre elementos, y por tanto, el resultado de la categorizacion en clusters.

Es conveniente aplicar técnicas de normalización, como el **raging**, que básicamente consiste en normalizar los valores de las características al intervalo continuo [0, 1]. 

Otra posibilidad es la estandarización, asignando al valor medio de una caracteristica el 0 y con una desviación de 1. De esta forma los valores están en el rango [-1, 1].


