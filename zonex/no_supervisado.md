# Aprendizaje no supervisado

Los datos que se obtienen del mundo real, generalmente, no están etiquetados. Para obtener información a partir de estos datos se utilizan algoritmos de aprendizaje no supervisado.

Se trata de una serie de algoritmos de Machine Learning que permiten trabajar con datasets no etiquetados, es decir que no se utiliza una características conocida como objetivo. En general los datos que se obtienen del mundo real serán de este tipo. Para etiquetarlos sería necesario realizar un proceso manual o automático.

# Segmentación de datos. Clusters

*Organizar automáticamente datos en grupos similares entre ellos y distintos de los demás.*

Uno de los algoritmos más utilizados, es la segmentación de datos. Problemas donde es necesario conocer qué objetos se parecen o agrupan por similitud. Para ello se utilizan las técnicas de **clustering** consiguiendo una segmentación automática en grupos de datos.

info: "Atención"
    Las características de referencia no deben ser usados para el agrupamiento.

Este tipo de problema consiste en realizar agrupaciones de los elementos. De cada agrupamiento hay que identificar alguna característica que permita caracterizar al cluster.

Los elementos de referencia, determinan cada tipo de agrupamiento, considerando al resto de elementos del mismo: *elementos del mismo tipo*.

La dificultad de esta técnica es: determinar cuantos agrupamientos se van a realizar con los datos. En función de este valor, se obtendrán diferentes agrupamientos posibles.



## Algorítmo G-means

Una vez seleccionados los datos más relevantes, se calcula el **centroide** y la distancia de cada elemento a esos puntos centrales. Los **centroides** son el promedio de todas las distancias de los objetos agrupados alrededor de él. 

Los grupos estarán mejor definidos cuanto más próximos al centroide estén y más lejanos a otros centroides.

Las nuevas instacias se claficarán en el grupo al que pertenecen, según el todas las características que se han tenido en cuenta para el modelo.

Su funcionamiento se basa en realizar divisiones de las agrupaciones previas realizadas. Modificando el valor de ***k***. En la primera iteración, el valor es **1**, luego realiza una división (valor 2)


## Algoritmo K-means

Este algoritmo necesita saber cuántos grupos se quieren conseguir con los datos existentes. 

Es necesario determinar las características relevantes que se van a utilizar para la clasificación.

También se pueden valorar las características más relevantes.

Con los datos del dataset también se puede crear un batch-centroid, que corresponde a los datos de un cluster.


# Funciones para determinar el número óptimo de clusters

La función Silueta, es la más utilizada para determinar cuántos clusters se deben establecer con los datos.

Se prueba con varios valores para el número de agrupaciones, y se compara la métrica silueta. Por lo general, se consigue determinar cuál es el valor óptimo de agrupamientos.