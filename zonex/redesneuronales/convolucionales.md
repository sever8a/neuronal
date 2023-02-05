# Redes convolucionales

Las redes convolucionales ofrecen ventajas, frente a las redes de capas densas, para el procesamiento de imágenes.

!["Esquema convolucional"](https://miro.medium.com/v2/resize:fit:720/format:webp/1*CrjJwSX9S7f759dK2EtGJQ.png)


Las capas convolucionales son el elemento clave en este tipo de redes.

Se basan en el reconocimiento de elementos característicos de cada imagen. Aprende de líneas, bordes, texturas o formas.

!["Aprendizaje"](https://www.researchgate.net/profile/Honglak-Lee/publication/220424626/figure/fig2/AS:277417953382421@1443153002703/Columns-1-4-the-second-layer-bases-top-and-the-third-layer-bases-bottom-learned-from.png)


La primera capa convolucional aprende patrones básicos, y las siguientes capas aprenden patrones compuestos de las capas anteriores, cada vez más complejos.

![aprendizaje de una cara](http://torres.ai/wp-content/uploads/2018/06/Picture.4.1.png)

Las dos capas que definen a las redes convolucionales están especializadas en dos operaciones: *convolution* y *pooling*.


# De capas densas a capas convolucionales

Las capas convolucionales **aprenden patrones locales** en pequeñas ventanas de dos dimensiones. Mientras que las capas densas aprenden patrones globales en su espacio global de entrada.

Una característica muy interesante de las capas convolucionales es que una vez aprendida una característica o rasgo visual en un punto de la imagen, la puede **reconocer en cualquier parte de la imagen**. Sin embargo, una red de capas densas tiene que aprender de nuevo el patrón si aparece en otro lugar de la imagen.

Otra característica destacable, es que las capas convolucionales pueden aprender **jerarquías espaciales de patrones**. Una capa aprende patrones básicos, la siguiente patrones compuestos de elementos básicos aprendidos en la capa anterior.

Las capas convolucionales operan sobre matrices de tres ejes, mapas de características. Dos ejes indican las dimensiones: altura y anchura, el tercer eje es el *canal* en imágenes RGB la dimensión es 3, correspondiendo con cada canal de color. Sin embargo en imágenes en blanco y negro la dimensión es 1 (nivel de gris).

No se conectan todas las entradas (pixels) de la imagen con todas las neuronas, tan solo se hace por pequeñas zonas localizadas (ventanas).

![pequeñas zonas localizadas](http://torres.ai/wp-content/uploads/2018/06/Picture.4.2.png)

Esta ventana va deslizándose por toda la imagen, conectando cada una de ellas con una neurona de la siguiente capa.

![recorrido de la venta por la imagen](http://torres.ai/wp-content/uploads/2018/06/Picture.4.3.png)

La capa convolucional, realiza una reducción de la dimensión de la imagen de entrada, de manera que mediante una ventana de tamaño específico va recorriendo todos los pixel de la imagen de entrada. El movimiento de esta ventana se establece con el parámetro **stride**. Puede ser de un pixel o más.

!["El stride"](https://d2l.ai/_images/conv-stride.svg)

Al tamaño de esta ventana se denomina **kernel**, y corresponde a una matriz cuadrada que abarca tantos pixel como los indicados en este parámetro. Sin embargo, la combinación de estos dos parámetros para el recorrido exploratorio de toda la imagen, deja entrever que unos pixeles participan más que otros, concretamente los pixel más próximos a los bordes, quedan excluidos de más convoluciones.


Para mejorar el barrido de pixel de la imagen, se utiliza el parámetro **padding** que permite añadir a la imagen un bórde extra de pixeles, permitiendo que el *kernel* (ventana o filtro) y su desplazamiento *sride* recorra todos los pixeles significativos en más ocasiones.


Una particularidad importante en redes convolucionales, es que se usa el mismo *kernel* (filtro o ventana) en todas las neuronas de una misma capa, es decir el mismo peso **w** y el mismo sesgo **b**. Esto reduce de forma drástica los parámetros que debe ajustar la red neuronal.

!!! info    "varios filtros"
Un filtro solo puede detectar una característica de la imagen. Para realizar reconocimientos es necesario detectar más características usando varios filtros al mismo tiempo.

''' python  hl_lines="14"
import tensorflow as tf


# We define a helper function to calculate convolutions. It initializes
# the convolutional layer weights and performs corresponding dimensionality
# elevations and reductions on the input and output
def comp_conv2d(conv2d, X):
    # (1, 1) indicates that batch size and the number of channels are both 1
    X = tf.reshape(X, (1, ) + X.shape + (1, ))
    Y = conv2d(X)
    # Strip the first two dimensions: examples and channels
    return tf.reshape(Y, Y.shape[1:3])
# 1 row and column is padded on either side, so a total of 2 rows or columns are added
conv2d = tf.keras.layers.Conv2D(1, kernel_size=3, padding='same')
X = tf.random.uniform(shape=(8, 8))
comp_conv2d(conv2d, X).shape
'''

Cuando la altura y anchura del kernel no son iguales, también es posible establecer una dimensión adecuada para el parámetro padding.



''' python hl_lines="3"
# We use a convolution kernel with height 5 and width 3. The padding on
# either side of the height and width are 2 and 1, respectively
conv2d = tf.keras.layers.Conv2D(1, kernel_size=(5, 3), padding='same')
comp_conv2d(conv2d, X).shape
'''

## Pooling

Las redes convolucionales acompañan a las capas convolucionales de capas de **pooling**, que suelen ser aplicadas inmediantemente después de las capas convolucionales. Las capas **pooling** hacen una simplificación de la información recogida por la capa convolucional y crean una versión condensada de la información contenida.

Aplicar este tipo de capa supone realizar una reducción dimensional de la imagen previa. Hay posibilidad de utilizar el máximo valor, o el valor promedio, de la ventana indicada como kernel

!!! note    "El pooling"
Una ventana (*kernel*) de 2 x 2 pixeles, se simplifica a un único pixel.

[poling 2x2 a 1](http://torres.ai/wp-content/uploads/2018/06/Picture4.5.png)

Hay varias formas de condensar la información. Una opción es utilizar el *max_pooling*, que se queda con el valor máximo de los que había en la ventana (*kernel*).

También se puede utilizar *average_pooling*, donde cada conjunto de valores de pixel se transforma en el valor promedio.

![ejemplo max_pooling](http://torres.ai/wp-content/uploads/2018/06/Picture.4.6.png)

Como la capa pooling se aplica a cada filtro (*kernel*), y la capa convolucional alberga más de un filtro, se obtendrá una **capa pooling** con tantos filtros de pooling como convolucionales.


## Red convolucional básica



El dataset de prendas de ropa de Zalando sirve para probar los resultados que se pueden conseguir con un modelo de red neuronal de capas densas, frente a una red con capas convolucionales.

[Ejemplo para comparar](https://colab.research.google.com/drive/1VdwtqDSlz1TzNVyWU0R-X9qvrkQ-z7c5?usp=sharing)

# Aumento de datos

Permite disponer de más datos aplicando variaciones a las imágenes disponibles (rotación, iluminación, contraste,...).

En algunos casos (problemas de segmentación) puede ser necesario aplicar los mismos filtros a otros elementos del dataset relacionados con cada elemento del dataset. Por ejemplo, la máscara en los problemas de segmentación.

# Segmentación

Los problemas de segmentación en imágenes se basan en identificar elementos en la imagen. La estructura de los modelos es diferente a los que solucionan problemas de clasificación.

## Segmentación semántica

Consiste en determinar los elementos que componen una imagen, detectando su relevancia en la imagen. Etiquetando cada área con una categoría de las clases utilizadas. *Se clasifican los pixels, no los objetos.

En la siguiente imagen se observa como sobre el total de las imagenes se establecen las zonas relevantes a: pasto, avión, edificio, vaca, cielo, camino...

![ejemplo segmentación semantica](https://www.researchgate.net/profile/Cristobal-Silva-5/publication/319766387/figure/fig4/AS:538875850625025@1505489422809/Figura-24-Ejemplo-de-Segmentacion-Semantica-31.png)

### Segmentación binaria

Es un caso particular de segmentación semática, en el cual solo se clasifica cada pixel: *si pertenece al **fondo**, o a la **región de interés***.


## Segmentación de instancias

Consiste en determinar los objetos de la imagnes. *Se clasifican los **pixels** y los **objetos***.

![Ejemplo instancias](https://cocodataset.org/images/detection-splash.png)



## Recursos

La base de datos [CIFAR10](https://www.cs.toronto.edu/~kriz/cifar.html) consiste en un dataset de imágenes cotidianas pertenecientes a 10 clases diferentes. 

Dispone de unas 60.000 imágenes a color de 32 x 32. Distribuidas para entrenamiento y validación.

Las clases que dispone son:
- avión
- automóbil
- pájaro
- gato 
- ciervo
- perro
- rana
- caballo
- barco
- camión

Una desventaja de este dataset es el tamaño (32 x 32), ya que son imágenes con baja resolución.

La base de datos [COCO](https://cocodataset.org/#home) consiste en un dataset de imágenes etiquetadas con 80 categorías. Se utiliza para entrenar modelos para solucionar problemas de **segmentación de instancias**.