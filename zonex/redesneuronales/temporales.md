# Series temporales

La predicción de valores futuros es posiblemente la aplicación más común en Machine Learning. En diferentes campos se precisa de esta información: economía, la producción, ventas, meteorología, aumento de población, etc... 

Otra característica importante, es que los datos no son independientes, sino que tiene significado su secuencia y orden temporal.

# Qué es una serie de datos temporales?
Un conjunto de observaciones asociadas a una marca de tiempo. Las observaciones se guardan con una frecuencia constante (diaria, mensual, por hora...).

Por ejemplo, el importe de venta de libros de tapa dura al día durante el mes de agosto, en la librería más pequeña de la ciudad.

Una relación de puntos anteriores tienen implicitamente una relación temporal, implica un número fijo de periodos de tiempo.

Su objetivo será predecir valores futuros utilizando valores previos. Un problema habitual es el **alineamiento** ya que en pocas ocasiones puede asumirse que la secuencia de tiempo de los patrones causales coincide con los periodos de tiempo de las series. Es decir, resulta fácil detectar la consecuencia de un cambio, cuando la variación se manifiesta un tiempo después, pero no si tiene un efectro progresivo (tendencia).

Otro problema es la **segmentación** de la serie. Esto puede ocurrir cuando un factor externo modifica la secuencia de la serie. Por ejemplo, la noticia de una guerra puede alterar el comportamiento de la serie y ya no es predecible a partir de los datos pasados.

## Predicciones basadas en modelos lineales

Se basan en encontrar una fórmula que pronostique con precisión cada entrada de la serie, a partir de entradas anteriores. La misma fórmula se utiliza para pronosticar entradas futuras utilizando las últimas entradas disponibles.

Resulta clave seleccionar el tamaño de la ventana (número de observaciones precedentes a incluir en la función lineal).

ARIMA es un modelo clásico que da buenos resultados, pero tiene la debilidad que precisa datos completos, se centra en relaciones lineales, establece dependencias temporales fijas, se centra en una única variable de entrada.

## Predicciónes basadas en modelos no lineales

Las redes neuronales, árboles de regresión (M5), regresión mediante soporte de vectores o métodos *kernel* corresponden a esta categoría. Además de las variables anteriores, el modelo puede incorporar la variable temporar y variables temporales derivadas (como día de la semana, trimestre, franja horaria).


## Tendencia

Se basa en la lentitud en que cambian los valores a loargo plazo. Es decir, las fluctuaciones a corto plazo no son relevantes, solo los cambios en un rango más ámplio.

![Emisión de CO2 del volcan Manu Loa](https://i.imgur.com/EZOXiPs.gif)

Se puede observar como aunque cada año la emisión varía y cambia oscilando con valores altos y bajos, según la estación. la tendencia en un rango más ámplio, año tras año, se puede obtener considerando la media anual, observando el crecimiento.

!!! note    "Tendencia"

    Para observar la tendencia es necesario calcular la media sobre un número más ámplio de datos.
    
## Estacionalidad

Parámetros constantes en el tiempo.

## Ciclos

Los datos presentan una fluctuación variable sin tener una frecuencia fija.
## Predicciones híbridas

# Decisiones ante un problema de serie temporal de datos

Es necesario conseguir la respuesta a las siguientes cuestiones para plantear adecuadamente la resolución del problema concreto.


1. **Inputs y outputs**. Inputs indica los datos pasados que se utilizan para realizar la predicción. Outputs es la predicción para un momento de tiempo futuro, dependiendo de los datos de entrada. Es importante definir los datos de entrada (inputs), no se refiere a los datos de entrenamiento sino a los datos que se utilizan para conseguir una predicción. Por ejemplo, conociendo los últimos 7 días de venta, predecir las ventas el siguiente día. *Entrada y salida de la predicción*.

2. **Endógenos vs Exógenos**. Una variable es endógena cuando depende de otras variables, por ejemplo cuando el valor de una variable observada depende, de una observación en un momento anterior. Una variable es exógena cuando no depende de otras variables del sistema. Siempre existen variables endógenas, ya que la salida depende de valores anteriores. Las variables exógenas pueden o no estar presentes en el modelo, hay que considerarlas. *Detectar datos endógenos y exógenos*.

3. **Estructurados vs no estructurados**. Una representación gráfica puede facilitar la detección de estructuras como la *tendencia*, *ciclos* y *estacionalidad*. Conocer esta característica puede ayudar a resolver el problema. Si no existe este tipo de patrones se trata de datos no estructurados. *Detectar patrones estructurales*.

4. **Regresión vs Clasificación**. Un problema de regresión es cuando se busca un valor, un problema de clasificación se obtiene un valor categoríco (frio, calor, sube, baja...). Hay que tener en cuenta que en muchos casos el problema puede redefinirse de un tipo u otro. *El problema se trata de una clasificación o una regresión*.

5. **Univariable vs Multivariable**. Univariable, una única variable se observada en cada instante de tiempo. Multivariable, se obtienen más de un valor de diferentes variables en cada instante de tiempo. La multivariable puede ocurrir en las variables de entrada o en la cantidad de variables de salida. Considera simultaneamente varias series de tiempo. *Determinar las variables con vinculación temporal, tanto en entrada como salida*.

6. **Paso simple vs Multiple paso**. Paso simple se refiere a la predicción del siguiente instante de tiempo, frente a multiple paso donde la predicción va más allá del siguiente instante de tiempo. *ES una predicción multiple o simple paso*.

7. **Estático vs Dinámico**. Un modelo estático puede utilizarse para varias predicciones después de realizar un entrenamiento, mientras que el modelo dinámico necesita realizar el entrenamiento para cada predicción. *Se precisa un modelo estático o dinámico*.

8. **Contiguo vs Discontinuo**. La serie de datos tiene una continuidad, en este caso los datos son contiguos. Son datos discontiguos cuando se reciben de manera esporádica o con una frecuencia diferente a otros datos de la serie. Es necesario modificar los datos discontinuos para adaptarlos a la serie.*Las observaciones son contiguas o discontiguas*.


Conocer toda esta información ayuda a definir el problema. Se pueden utilizar elementos de visualización, análisis estadísticos o criterios de expertos.

También es necesario diseñar un proceso de evaluación del modelo. Considerando estratégias como dividir los datos en entrenamiento y test, entrenar una aproximación del modelo.

Es importante valorar el modelo más adecuado para el problema, considerando diferentes opciones y tecnologías.


# Como transformar series temporales en problema de aprendizaje supervisado

Los problemas basados en series de datos temporales se pueden rediseñar como problemas de aprendizaje supervisado. De esta manera se puede utilizar para la solución modelos lineales y no lineales de Machine Learning.

Se puede reestructurar el dataset de series temporales en dataset para aprendizaje supervisado, considerando la siguiente toma temporal como el objetivo de la anterior. El previo paso de tiempo es la entrada al modelo (*X*), mientras que el siguiente paso de tiempo es la salida del modelo (*y*).

!!! warning "Orden datos"
    Es muy importante mantener el orden de los datos.

Es posible que los valores primeros y últimos del dataset queden incompletos. En este caso será necesario eliminar estos registros.

Utilizar momentos previos de tiempo para predecir el momento de un tiempo futuro, se denomina método de la **ventana deslizante**. La cantidad de momentos previos se denomína **amplitud de la ventana**.

La variable de salida puede ser simple o múltiple. Con redes neuronales se pueden predecir más de un valor en una secuencia de tiempo. Pero también es posible predecir más allá de un momento futuro (*multiple paso*).

### Ventana deslizante con multiples pasos de tiempo

El número de marcas de tiempo futuro que se quiere predecir es importante.

## Redes Neuronales Recurrentes

Hay tres problemas con las **redes neuronales densas** para tratar problemas con series de datos temporales:

    * No puede mantener el orden de los datos.
    * Requiere un tamaño fijo de entrada.
    * No puede devolver salidas de diferente longitud a la prevista. *Por ejemplo, la traducción de una frase al ruso no se puede ver limitada por solo cinco palabras*.

!["Combinaciones de uso de las redes neuronales"](https://pythongeeks.org/wp-content/uploads/2022/02/types-of-rnn.webp)

Las redes recurrentes solucionan estos inconvenientes, pero han surgido diferentes variedades de ellas. Las *long short-term memory* **LSTM** tienen una evaluoción larga. Se han utilizado para problemas de traducción de texto o análisis de sentimiento.

Potenciales casos de uso de las Redes Neuronales Recurrentes:
    - Aprendizaje de gramática.
    - Reconocimiento de escritura a mano.
    - Reconocimiento de acciones de humanos.
    - Traducción.
    - Composición de música.
    - Predicción de la localización de proteninas en células.
    - Predicción en tratamiento médicos.
    - Detección de proteinas homólogas.
    - Aprendizaje de ritmos.
    - Robótica.
    - Análisis de sentimientos.
    - Reconocimiento de la voz y creación de voz sintética.
    - Detección de anomalías en series temporales.
    - Predicción en series temporales.

### Mecanismo de las Redes Neuronales Recurrentes

Utilizan la información previa almacenándola en memoria, se guarda como `state` con cada neurona.

![Esquema red neuronal recurrente](https://pythongeeks.org/wp-content/uploads/2022/02/rnn-block.webp)

Tres tipos de redes neuronales para series temporales:
    * Tienen en común almacenar en memoria el `state` de un momento anterior.
    * Aplican una función de activación (*tanh*) y realizan operaciones matriciales.
    * Con todos los elementos obtiene el estado del momento actual.
    * Repiten todo el proceso para mejorar los pesos *w* y desviación *b*.

![Redes neuronales series temporales](https://media.licdn.com/dms/image/C5612AQH5Im8XrvLmYQ/article-cover_image-shrink_600_2000/0/1564974698831?e=2147483647&v=beta&t=mVx-N8AfjAS5L-ktV6vmi_5LxR1madQ16yT1fRu__Jk)




