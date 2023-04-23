# Algoritmos Machine Learning

Machin Learning consiste en extraer patrones de comportamiento, a partir de los datos recopilados disponibles. Usando estadística, álgebra lineal y optimización numérica.

Se basan en conseguir realizar alguna tarea en función de los datos de acontecimientos anteriores. Utilizando algoritmos matemáticos y estadísticos.

Los algoritmos están divididos en tres clases principales:

*   Aprendizaje Supervisado.
*   Aprendizaje No Supervisado.
*   Aprendizaje Por Refuerzo.

En general se pueden afrontar los siguientes tipos de problemas:

*   **Clasificación binaria**, consiste en determinar si un elemento pertenece o no a una categoría. Por ejemplo, determinar si un cliente es apropiado para concederle un crédito o no.

*   **Clasificación multiclase**, determina a qué clase, entre varias posibles, pertece un elemento concreto. Por ejemplo, establecer el perfil de usuario, para un cliente que ha realizado una compra en un supermercado.

*   **Regresión**, son problemas en los que hay que determinar un valor continuo. Por ejemplo, determinar los kilometros de autonomía de un vehículo.


## Regresión Lineal


## Regresión Logistica




## K-Nearest Neighbors

Es un algortimo de clasificación de aprendizaje supervisado. Se utiliza para minería de datos, reconocimiento de patrones y detección de intrusos.

No hace suposiciones sobre los datos, de manera que los datos tienen la misma importancia en el modelo. Para predecir utiliza las instacias clasificadas, en lugar de un algoritmo que devuelve una respuesta.

Requiere gran cantidad de procesado y de memoria, ya que se almacenan las instancias.

Se encuentran los puntos similares más cercandos. Considerando la distancia (Euclidiana, Manhatan, Minkoski).

El valor a predecir se situa en el modelo, y se realizan votaciones de inclusión a la clase que consiga más votos.

El valor de k corresponde con la cantidad de vecinos que se consideran para definir la clase de la instancia que se quiere averiguar. Es decir, con **k=5** se tomará la clase mayoritaria de los 5 puntos más cercanos.

En la herramienta Weka, el algoritmo aparece en el apartado de clasificación - ***Lazy - LBK***

## Support Vector Machine (SVM)

Se utiliza en aprendizaje supervisado o no supervisado. Sirve para clasificar. Trabaja solo con dos clases. 

El principio fundamental se basa en establecer la línea óptima de división entre los dos grupos de clasificación.

Para determinar la posición de esta línea de separación, se utiliza la distancia entre los puntos de ambas clases. Se pueden considerar los puntos más cercanos de ambas clases o los más lejanos.

Se añade un hiperparámetro para generar cambios en la línea, de manera que deja de ser recta, para adaptarse mejor a la distribución de los elementos de cada clase.


