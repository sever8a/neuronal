# Transferencia de conocimiento

Estos modelos se basan en redes preentrenadas

## Técnicas de tranferencia de conocimiento

### Como funciona


### Ventajas


**Ejemplo:** 
Detectar *tweets* negativos escritos en inglés. En este caso se trata de encontrar Tweets negativos en castellano. Existen dos soluciones:

1. Traducir los *tweets* del castellano al inglés.
    - Utilizar el modelo existente (Universidad de Helsinki).
    - Métrica de evaluación **BLEU**.

2. Entrenar modelos para cada idioma. *Múltiples modelos*:
    - Entrenar modelos de clasificación de *tweets* en castellano.
    - Entrenar un clasificador de idioma (librería langdetect).

3. Modelo multilengüaje.
    - Modelos multilíngües.
    - Ventajas.
    - Entrenar un modelo multilingüe.

## Modelos librería Keras

La siguiente relación de modelos está disponible en la [plataforma de la librería Keras](https://keras.io/api/applications/) (que se utiliza desde TensorFlow). Estos modelos se pueden utilizar para extracción de características, predicción y ajuste (fine tunning).

!!! note    "ImageNet"
Se trata de una organización que dispone de una gran base de datos de imágenes etiquetas y clasificadas. [Más información al respecto](https://www.image-net.org/about.php).

