# Redes convolucionales

Las redes convolucionales ofrecen ventajas, frente a las redes de capas densas, para el procesamiento de imágenes.

!["Esquema convolucional"](https://miro.medium.com/v2/resize:fit:720/format:webp/1*CrjJwSX9S7f759dK2EtGJQ.png)


Las capas convolucionales son el elemento clave en este tipo de redes.





# De capas densas a capas convolucionales

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