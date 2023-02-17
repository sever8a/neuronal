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

Utilizando [Google playground](https://playground.tensorflow.org) se puede prácticar como evoluciona el resultado al modificar algunos hiperparámetros.



