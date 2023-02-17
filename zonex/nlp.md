# Procesamiento del Lenguaje Natural

# Transformer
Se trata de una librería de última generación que facilita la interpretación de contenidos textuales. La promoción de esta librería se realiza desde Hugging Face. 
Intervienen los siguientes elementos:
* **Encambio**.
* **Tokenización**.
* **Preprocesado**.

# El ecosistema de Hugging Face
## Hub
Contiene todos los modelos, datasets, y spaces. Estos últimos son demos de los modelos. Finalmente también está disponible la documentación de todas las librerías.

Conjunto de herramientas y liberías para utilizar fácilmente la inteligencia artificial.

ültimamente están añadiendo más librerías para tareas específicas, como visión artificial.

## Librería transformers
En Google colab es necesario instalarla. 
El pipeline es un elemento muy sencillo para comenzar a utilizar modelos.

Todos los modelos disponibles están en el *hub*, y pueden ser utilizados directamente.

Tareas de clasificación o generación de texto.

También es posible modificar las etapas de **pipeline**
* **Tokenizador**. Codificación de las palabras de un texto.
* **Model**. Modelo utilizado.
* **Posprocesado**. Se tiene que realizar el postprocesado para ajustar el resultado a lo que se busca.

Se puede utilizar el autotokenizer.
El automodel.
Cada capa es la entrada de la siguiente.

También es posible instanciar el modelo directamente.

## La librería dataset
Una vez instalada se puede utilizar directamente.
Concretando el dataset que se quiere utilizar, directamente se puede llamar y viene directamente separado en datos de entrenamiento y validación.

Es posible crear dataset propios, cargando desde un formato concreto.

Etapas de procesado de texto
* Proceso de normalización de un texto. Transformar mayusculas en minúsculas y quitar acentos.
* Pretokenización. Separa espacios en blanco y signos de puntación. El resultado es una lista.
* Modelado, generación de unidades semánticas. (No confundir con la red neuronal). Utiliza una representación compacta del lenguaje. Verbos en diferentes conjugaciones se utilizan en infinitivo. Las palabras en singular más un token para indicar cuando está en plural.
* Postprocesado, añade tokens especiales, como el inicio o fin de frase. Se consigue un alista de id.

* El decodificador, es un elemento importante porque permite volver a convertir los identificadores en texto original. 

El resultado de este procesado es el texto tokenizado, preparado para ser la entreda al modelo.


## Representación textos

Para entrenar modelos de Machine Learning se pueden utilizar diferentes formas de representación de las palabras y textos en formato de vector numérico.

Métodos de representación:
- One-hot encoding.
- Bag-of-words.
- Tf-idf.
- Word embedding.
- Language Models.

## Modelos PLN

**BERT** unido a la librería *Transformers* de Hugging Face. 