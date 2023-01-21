# El perceptron

El elmento más básico de una red neuronal es la ***neurona***. La red neuronal más sencilla es el **perceptron**, que está compuesta de una única neurona. 

La potencia de una red neuronal se obtiene de la complejidad de las conexiones entre las neuronas que la forman.

## La neurona
![La neurona](https://i.imgur.com/mfOlDR6.png)

Los componentes fundamentales son:
    * La entrada ***x***.
    * El peso ***w***, Conecta la entrada con la neurona y tiene un peso.
    * Un peso especial llamado desviación (bias) ***b***.
    * Valor final de salida ***y***.
    
La entrada ***x*** llega hasta la neurona mediante una conexión de peso ***w***. El valor para llegar a la neurona es su multiplación ***w * x***. La red neuronal aprende modificando sus pesos ***w***. Obteniendo la salida ***y*** con el resultado.

La desviación (bias) ***b*** modifica el valor de salida de la neurona, independientemente de la entrada.

Por lo tanto, la fórmula de la neurona es ***$y = wx + b$***.

> La fórmula de una ecuación lineal, donde ***w*** es la pendiente y ***b*** el punto de corte de la recta el eje de ordenadas.

!!!
    Como mínimo siempre es necesario definir una capa de entrada y una de salida. La capa de entrada debe tener tantas neuronas de entrada como características de entrada tenga el modelo.

La cantidad de neuronas en la capa de salida dependerá de la respuesta que se esté buscando. En el caso de una valor (regresión), o una clasificación binaria bastará con una neurona. Pero si es una **clasificación multiclse** se necesita una neurona de salida por cada clase diferente.

![modelo neurona](https://www.researchgate.net/profile/Dmitry-Rashkovetsky/publication/348382026/figure/fig3/AS:978712501690376@1610354652732/Schematic-representation-of-a-neuron-A-linear-combination-of-the-inputs-x-i-followed-by.jpg)



