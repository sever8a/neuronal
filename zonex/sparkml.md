# Spark ML

Pandas resulta una librería adecuada para el procesamiento de los datos, y para disponer de una estructura de organización de los datos: **el dataframe**.

Sin embargo, cuando el dataset tiene un tamaño considerable, los recursos de memoria no serán suficientes, y es necesario utilizar una solución que combine el volumen de los datos, con la posibilidad de procesamiento adecuada.

**SparkML** es una alternativa en este nuevo contexto, combinando las posibilidades de Spark con una libreria de procesamiento de datos y aplicación de algoritmos de *machine learning*.

## Los elementos de Spark ML

* **Transformadores**, se encargan de realizar todo tipo de transformación sobre la estructura de datos (quitar o añadir columnas, normalizar valores, convertir tipo de datos...).

!!! note "Requisitos"

    Hay que tener presentes los requisitos de los datos para poder aplicar cada algoritmo. Todos los datos númericos deben ser tipo *double*.

* **Estimadores**, son los algoritmos de Machine Learning. Su resultado genera un modelo, que es un tipo de *transformador*.


* **Pipeline**, combina transformadores y estimadores en un único modelo. Los pipeline son transformadores que devuelven un modelo


![Imagen Spark](https://raw.githubusercontent.com/dmlc/web-data/master/xgboost/unified_pipeline_new.png)

