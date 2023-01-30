# Redes Neuronales Profundas (densas)

En la capa de entrada, comienzan los datos de las características disponibles. La red neuronal realiza todas las combinaciones entre estas características a lo largo de todas las capas. Hasta la capa de salida donde la cantidad de neuronas se limita a las respuestas que se quieren obtener del modelo. 

Esta salida será el mejor resultado del procesamiento de todas las combinaciones anteriores. Por la tanto, la se consigue un modelo complejo utilizando estructuras lineales sencillas. Cuanto más capas, más compleja será la estructura, por eso se considera *profunda* la red neuronal.

Existen diferentes tipos de capas (convolucionales, recurrentes...), especializadas en resolver diferentes problemas.

## La función de activación

En un modelo de red neuronal densa, utilizar dos capas sin nada en medio no aportan nada diferente a una única capa. Las redes neuronales densas siempre aportan líneas o planos. Se necesita algo no lineal: la **función de activación**.

Sin función de activación las redes neuronales densas solo pueden aprender relaciones lineales entre las característas.

La **función de activación** es simplemente una función que se aplica a la salida de las neuronas de cada capa. La función más común es la función de rectificación *$max(0,x)$*.  

!!! info    "Salida"

    La función de salida se debe ajustar al tipo de predicción que se está realizando:
    
    - Regresión.
    - Clasificación binaria.
    - Clasificación multiclase.

Para conseguir buenos resultados con las redes neuronales es preciso que los datos de entrada estén normalizados a valores entre 0 y 1.

        > La función convierte en 0 los valores negativos.
![ReLU](https://i.imgur.com/aeIyAlF.png)


## Apilando capas

De esta forma se consigue aumentar la complejidad de la red neuronal.
![Red neuronal](https://i.imgur.com/Y5iwFQZ.png)

Las capas anteriores a la capa de salida permanecen ocultas.

También hay que destacar que en la capa de salida no hay función de activacion, será una función lineal. Esto indica que se está utilizando para una regresión. Si se tratase de una clasificación habría que utilizar una función de activación.

## Construcción del modelo

La construcción del modelo mediante un framework (TensorFlow / PyTorch), requiere establecer una secuencia de capas. Indicando el número de neuronas, la función de activación que utilizará la capa, y el número de salidas.

``` python hl_lines="6"
from tensorflow import keras
from tensorflow.keras import layers

model = keras.Sequential([
    # the hidden ReLU layers
    layers.Dense(units=4, activation='relu', input_shape=[2]),
    layers.Dense(units=3, activation='relu'),
    # the linear output layer 
    layers.Dense(units=1),
])
```

## El gradiente estocástico descendente

Cuando creamos una red neuronal densa, todas las capas están interconectadas. Los pesos de estas conexiones *w* se establecen de manera aleatoria, la red todavía "no sabe nada".

### El entrenamiento
Al igual que en todos los procesos de Machine Learning, comienza con un conjunto de datos de entrenamiento. Cada instancia de estos datos consistirá en un conjunto de características (la entrada) junto con el objetivo esperado (salida). **Entrenar la red neuronal significa ajustar los pesos *w* de manera que pueda transformar las características en el objetivo. Los pesos representan de algún modo la relación entre la entrada y el resultado.


Para entrenar los datos es necesario:
- Una **función de pérdida**, que mida cómo son de buenas las predicciones que realiza la redn neuronal.
- Un **optimizador** que dice a la red neuronal cómo tiene que cambiar los pesos.

### La función de pérdida

Mide la diferencia entre el valor real del objetivo y el valor que el modelo predice.

Según el tipo de problema que se esté tratando (regresión o clasificación) la función de pérdida tendrá que ser diferente. Por ejemplo; el error absoluto medio, o el error cuadrático medio son dos funciones para regresiones.

!!! info "Funciones de pérdida"

    Ajustadas a cada tipo de problema.
    
    - Clasificación múltiple con one hot encoding --> *categorical_crossentropy*
    - Clasificación múltiple con indice categoria --> *sparse_categorical_crossentropy*
    - Regresión --> *mse*
    - Clasificación binaria --> *binary_crossentropy*

### El optimizador - Gradiente Estocástico Descendente

Es un algoritmo que ajusta los pesos para minimizar la pérdida.

Se utiliza el algoritmo del **Gradiente Estocástico Descendente**, es iterativo en cada paso realiza las siguientes tareas:

1. Utiliza un subconjunto de los datos de entrenamiento y los utiliza en la red neuronal para realizar predicciones.
2. Mide la pérdida entre las predicciones y los valores reales.
3. Finalmente ajusta los pesos en una dirección que hace la pérdida menor.

Estos pasos se repiten una y otra vez hasta que la pérdida es tan pequeña como se considere (o ya no disminuya).

Cada iteracion con un grupo de datos de entrenamiento se llama **mini-lote (minibatch)**, mientras que el entrenamiento de la red neuronal con todos los datos del conjunto de entrenamiento se llama **época (epoch)**.


#### La tasa de aprendizaje y el tamaño del lote
La tasa de aprendizaje determina la velocidad de aprendizaje de la red neuronal. Se trata de un modificador que altera los pesos en una dirección. Si esta modificación es más pequeña el entrenamiento será más preciso, pero tendrá que dar más pasos utilizando más minilotes.

La tasa de aprendizaje y el tamaño del minilote son dos hiperparámetros claves en el resultado que se consiga. Afortunadamente se puede elegir el algoritmo **Adam** que tiene una tasa de aprendizaje adaptable, y es una buena solución generica para cualquier problema.

Se indica en el método de compilación:

``` python
model.compile(
    optimizer="adam",
    loss="mae",
)
```

## Overfitting y Underfitting

Una vez entrenado el modelo es necesario realizar una valoración de qué tal predice valores distintos a los utilizados para el entrenamiento.

Si se dibuja en un gráfico las curvas de aprendizaje, representando en cada época el valor el valor de la función de pérdida con los valores de entrenamiento y los valores reales. Se puede interpretar si existe overfitting o underfitting.

Considerando que en el dataset de entrenamiento hay datos correctos (permiten una buena predicción) y ruido (datos que distorsionan la solución). El overfitting es cuando los datos de ruido tienen mucha relevancia en el modelo. 
El underfitting ocurre cuando la función de pérdida no baja (sigue siendo alta después del entrenamiento). Se puede solucionar añadiendo más neuronas.

Al principio el modelo no es lo suficientemente complicado para captar los diferentes patrones de los datos (underfitting), luego al complicarse demasiado, falla en encontrar los patrones generales porque aprende peculiaridades concretas del dataset de entrenamiento (overfitting).

### Early stopping

Se trata de una funcionalidad que permite detectar el momento óptimo de las dos líneas de aprendizaje, para detener el entrenamiento y no exceder el número de épocas necesarios.

![Early stopping](https://i.imgur.com/eP0gppr.png)


### Dropout

Se utiliza para solucionar el overfitting. Consiste en agregar una capa que se encarga de 'desactivar' algunas neuronas de la capa, de manera que no todos participen en todos los pasos de aprendizaje. De esta manera el aprendizaje es más difícil y se pueden evitar datos que producen ruido.


### Batch Normalization

Los datos de entrada a la red neuronal deben estar normalizados, ya que el Gradiente Estocástico Descendente modifica los pesos, en función de los valores de salida. Si hay valores de salida dispares se ponderarán más los valores altos.

La normalización por lotes, es una capa especial que se añade a la red neuronal para realizar una normalización adicional respecto a los valores de cada mini-lote que se está utilizando. Volviendo a normalizar los valores.

## Clasificación binaria

La principal diferencia entre los problemas de regresión y clasificación es: la función de activación y la capa de salida. La salida se asigna a dos valores de la etiqueta 0 y 1, para cada caso.


### Accuracy y entropía cruzada

Para problemas de clasificación, la precisión (acuracy) es la métrica que representa la relación entre predicciones correctas y el total de predicciones. *+precision = correctas / total+*.

Es una buena métrica siempre que la probabilidad de que suceda cada una de las clases sea la misma.

El problema es que las metrícas de clasificación no pueden usarse como función de perdida. En su lugar se utliza la **entropía cruzada** (probabilidad de predecir la clase correcta).

#### Función Sigmoide

De esta forma se puede obtener un valor 0-1 de la predicción.

![Sigmoid](https://i.imgur.com/FYbRvJo.png)


# Ajuste de hiperparámetros

La precisión de un modelo de red neuronal puede modificarse utilizando los hiperparámetros.

- Cambio de función de activación.
- Aumento de epocas (veces que se usan todos los datos en el entrenamiento).
- Aumentar las neuronas en una capa.
- Agregar más capas.

Sin embargo, todo este tipo de aumentos supondrá también una aumento en los requisitos de procesamiento. La clave es encontrar un punto equilibrado adecuado.


Es necesario diferenciar entre *hiperparámetros* y *parámetros* de un modelo. Los **parámetros** son los valores internos a la red nueronal, por ejemplo los pesos de las neuronas. Aprenden automáticamente a partir de las muestras de entrenamiento. Estos parámetros se utilizan para hacer predicciones en un modelo ya entrenado que se encuentra en producción.

Los **hiperparámetros** son parámetros externos al modelo, los establece el programador de la red neuronal, por ejemplo seleccionando la función de activación a utilizar, o el tamaño del lote en el entrenamiento. Los hiperparámetros tienen un gran impacto en la precisión de una red neuronal.

Se pueden clasificar en dos grandes grupos:

- Hiperparámetros a nivel de **estructura y topología** de la red: número de capas, número de neuronas por capa, sus funciones de activación, inicialización de los pesos, etc.
- Hiperparámetros a nivel de **algoritmo de aprendizaje**: epocas, tamaño del lote, tasa de aprendizaje, etc.


## Hiperparámetros relaciones con el algoritmo de aprendizaje

### Número de epocas

Nos indica el número de veces que los datos de entrenamiento han pasado por la red neuronal durante el entrenamiento.

Un número alto de epocas provoca que el modelo se ajuste en exceso a los datos y puede tener problemas de generalización con el conjunto de datos de prueba y validación. También puede producir *vanishing gradients* y *exploding gradient*.

Si el número de épocas es escaso, supone que el modelo no ha visto suficientes datos para entrenarse, y no hará buenas predicciones.

Hay que probar diferentes valores. Incrementando el número de épocas hasta que **la métrica de precisión con los datos de validación** empiece a decrecer, incluso cuando la precisión de los datos de entrenamiento contiúe incrementándose (posible overfitting).


### Tamaño del lote

Se pueden particionar los datos en lotes de entrenamiento para pasar por la red.
Su tamaño depende de básicamente de la capacidad de memoria del equipo utilizado.

### Tasa de aprendizaje

El vector del gradiente tiene una *dirección* y una *magnitud*. Los algoritmos de gradiente descendente multiplican la +magnitud* por el **learning rate** (tasa de aprendizaje).

!!! note    "Ejemplo!"
Si el gradiente tiene una magnitud de 1.15 y el *learning rate* es 0.01, entonces el algoritmo del gradiente descente seleccionará el próximo punto a 0.0115 de distancia del anterior.


Si el valor es demasiado grande, el aprendizaje será más rápido pero al ser pasos demasiado grandes pasará el valor mínimo de la función de pérdida.

Si el valor es demasiado pequeño, se avanzará con pasos pequeños. Esto supone que el proceso de aprendizaje puede extremadamente lento.

En general, si el modelo de aprendizaje no funciona hay que disminuir el *learning rate*.

Existe otro hiperparámetro el **learning rate decay** que permite disminuir la tasa de aprendizaje a medida que van pasando las épocas. El aprendizaje avanza más rápido al principio y luego se ralentiza.

!!! info    "optimizador"
El valor de la tasa de aprendizaje depende del optimizador utilizado. Por ejemplo, para el optimizador **sdg** (descenso gradiente estocastico) *learnning rate* 0.1
Para el optimizador **adams** es mejor un *learnning rate* entre 0.001 y 0.01


### Inicialización de los pesos de las neuronas

Es recomendable inicializar los pesos con valores aleatorios y pequeños.


### Funciones de activación

La función de activación sirve para introducir la no linealidad en las capacidades de modelado de la red.

***linear***
No aporta cambio a la señal de entrada. La salida coincide con la entrada.

***sigmoid***
La mayor parte de su salida estará próxima a los valores 0 o 1.

***tanh***
En este caso la salida estará próxima a los valores -1 o 1.

***softmax***
Devuelve la distribución de probabilidad sobre clases mutuamente excluyentes. A menudo se ubica en la capa de salida.

***relu***
Cuando la entrada tenga un valor menor que 0 la salida será 0, y en otro caso coincidirá con la entrada.

!!! note    "Métricas importantes"
Hay que distinguir entre la función de pérdida con los **datos de entrenamiento** y los **datos de validación** 

Utilizando [Google playground](https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=4,2&seed=0.33012&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false) se puede prácticar como evoluciona el resultado al modificar algunos hiperparámetros.