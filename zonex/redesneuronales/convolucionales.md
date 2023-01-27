# Redes convolucionales

Las redes convolucionales ofrecen ventajas, frente a las redes de capas densas, para el procesamiento de imágenes.

!["Esquema convolucional"](https://miro.medium.com/v2/resize:fit:720/format:webp/1*CrjJwSX9S7f759dK2EtGJQ.png)


Las capas convolucionales son el elemento clave en este tipo de redes.





# De capas densas a capas convolucionales

El dataset de prendas de ropa de Zalando sirve para probar los resultados que se pueden conseguir con un modelo de red neuronal de capas densas, frente a una red con capas convolucionales.

[Ejemplo para comparar](https://colab.research.google.com/drive/1VdwtqDSlz1TzNVyWU0R-X9qvrkQ-z7c5?usp=sharing)



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

