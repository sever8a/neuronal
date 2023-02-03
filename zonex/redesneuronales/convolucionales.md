# Redes convolucionales

Las redes convolucionales ofrecen ventajas, frente a las redes de capas densas, para el procesamiento de imágenes.

!["Esquema convolucional"](https://miro.medium.com/v2/resize:fit:720/format:webp/1*CrjJwSX9S7f759dK2EtGJQ.png)


Las capas convolucionales son el elemento clave en este tipo de redes.

Se basan en el reconocimiento de elementos característicos de cada tipo de imagen. Aprende de líneas, bordes, texturas o formas.

!["Aprendizaje"](https://www.researchgate.net/profile/Honglak-Lee/publication/220424626/figure/fig2/AS:277417953382421@1443153002703/Columns-1-4-the-second-layer-bases-top-and-the-third-layer-bases-bottom-learned-from.png)


La primera capa convolucional aprende patrones básicos, y las siguientes capas aprenden patrones compuestos de las capas anteriores, cada vez más complejos.


# De capas densas a capas convolucionales

Las capas convolucionales operan sobre matrices de tres ejes, mapas de características. Dos ejes indican las dimensiones: altura y anchura, el tercer eje es el *canal* en imágenes RGB la dimensión es 3, correspondiendo con cada canal de color. Sin embargo en imágenes en blanco y negro la dimensión es 1 (nivel de gris).

La capa convolucional, realiza una reducción de la dimensión de la imagen de entrada, de manera que mediante una ventana de tamaño específico va recorriendo todos los pixel de la imagen de entrada. El movimiento de esta ventana se establece con el parámetro **stride**.

!["El stride"](https://d2l.ai/_images/conv-stride.svg)

Al tamaño de esta ventana se denomina **kernel**, y corresponde a una matriz cuadrada que abarca tantos pixel como los indicados en este parámetro. Sin embargo, la combinación de estos dos parámetros para el recorrido exploratorio de toda la imagen, deja entrever que unos pixeles participan más que otros, concretamente los pixel más próximos a los bordes, quedan excluidos de más convoluciones.


Para solventar esta circunstancia se utiliza el parámetro **padding** que permite añadir a la imagen un bórde extra de pixeles, permitiendo que el *kernel* y su desplazamiento *sride* recorra todos los pixeles (incluidos los del borde) en más ocasiones.


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

Aplicar este tipo de capa supone realizar una reducción dimensional de la imagen previa. Hay posibilidad de utilizar el máximo valor, o el valor promedio, de la ventana indicada como kernel


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