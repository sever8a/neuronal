# Aprendizaje no supoervisado

Se trata de una serie de algoritmos de Machine Learning que permiten trabajar con datasets no etiquetados, es decir que no se utiliza una características conocida como objetivo.

# Segmentación de datos

*Organizar automáticamente datos en grupos similares entre ellas y distintos de las demás.*

Problemas donde es necesario conocer qué objetos se parecen o agrupan por similitud. Para ello se utilizan las técnicas de **clustering** consiguiendo una segmentación automática de grupos de datos.

Las características de referencia no deben ser usados para el agrupamiento.

Este tipo de problema se basa en realizar agrupaciones de los elementos. Hay que determinar cuantos agrupamientos se van a realizar con los datos. 

## Algorítmo G-means

Una vez seleccionados los datos más relevantes, se calcula el **centroide** y la distancia de cada elemento a esos puntos centrales. Los **centroides** son el promedio de todas las distancias de los objetos agrupados alrededor de él. 

Los grupos estarán mejor definidos cuanto más próximos al centroide estén y más lejanos a otros.

Las nuevas instacián se claficarán en el grupo al que pertenecen al proporcionar las características.

Se puede generar

## Algoritmo K-means

En este caso se puede establecer cuántos grupos se quieren conseguir con los datos existentes. 

Es necesario determinar las características relevantes que se van a utilizar para la clasificación.

También se pueden valorar las características más relevantes.

Con los datos del dataset también se puede crear un batch-centroid, que corresponde a los datos de un cluster.