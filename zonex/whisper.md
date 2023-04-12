# Primeros pasos con Whisper

Este modelo gratuito y abierto, está disponible para su uso y adaptación a cualquier circunstancia.

Desarrollado por OpenAI. Entrenado con miles de horas basadas en lecturas de la Wikipedia. Ofrece la posibilidad de multilenguaje.

Se basa en la arquitectura ***transformer***, que está consiguiendo resultado impresionanentes para problemas de secuenciación. Y en particular para Procesamiento de Lenguaje Natural.


![Estructura del modelo Whisper](https://huggingface.co/blog/assets/111_fine_tune_whisper/whisper_architecture.svg)


El modelo tiene varias versiones que ofrecen diferente rendimiento, a la vez que se ajustan a la potencia de cálculo de diferentes plataformas.

* tiny
* base
* small
* medium
* large

!!! note "Prueba en la line"

    Es posible probar las prestaciones del modelo original desde la [página web de **Hugging Face**, dentro del apartado **Spaces**.](https://huggingface.co/spaces/openai/whisper)



# Pruebas de concepto

El objetivo de este modelo es transcribir los sonidos a texto. Consigue unos resultados muy buenos, porque detecta la entonación y las pausas, estableciendo los signos de puntación adecuados.

Para interpretaciones de locuciones largas, se consigue una precisión muy correcta.

Con la versión **small** ya se consiguen unos resultados muy fiables del sonido, incluso con sonidos de baja calidad o ruido. Sin embargo, el tiempo que requiere para obtener el resultado es demasiado alto (60 segundos de promedio por sentecia).

Utilizando los modelos inferiores (**tiny** y **base**) los resultados son muy similares en precisión, lo que no justifica el doble de tiempo que requiere la versión **base** sobre la versión **tiny**.

!!! info "Atención"

    Los resultados similares, no significa que se mantenga la precisión de los modelos superiores. En estos dos más básicos, son frecuentes los errores y trascripciones de palabras incorrectas u omisiones.


No sirve de nada esperar 15 segundos para obtener un resultado que no es correcto. En este sentido resulta adecuado elegir la versión **small**.

Hay que tener en cuenta el volumen del modelo y todo el procesamiento que supone. Disponer de procesamiento paralelo facilitará obtener un resultado más rápidamente.


Se puede especifar algunos parámetros adicionales al realizar al transcripción para agilizar el pre-procesado de los datos. Una de estas opciones es especificar el lenguaje.


La misma funcionalidad se puede conseguir con un cuaderno Google Colab, donde el procesamiento será más rápido, aunque es necesario enviar el fichero de audio.

[Ejemplo en Google Colab, para uso directo.](https://colab.research.google.com/drive/1jnspg2FyeEm9v08_aNqmhPv0bfN2r1PN?usp=sharing)

En este ejemplo se instalan las librerías de Whisper desde el repositorio de github. 

Se establecen las rutas a las carpetas en Google Colab. Cuestión importante en este entorno, ya que la existencia de los ficheros se limita al tiempo de ejecución del kernel.

Crea un entorno gráfico sencillo, integrado en el notebook, para interactuar con el usuario eligiendo las opciones de transcripción.

El fichero a transcribir debe ser subido a la plataforma.

Genera un fichero de texto con la transcripción, por si se quiere descargar para su posterior procesamiento.


# Fine tuning. Ajustando el modelo

El principal objetivo es ajustar el modelo existen a las necesidades particulares de nuestro problema.

Aprovechamos el modelo pre-entrenado para realizar el fine tuning.

1. Carga del dataset. Puede ser muy pesado!.
2. Preparar los datos. Se divide en tres fases: extraer las caracteristicas relevantes del dataset. Tokenizar. Estas dos fases las realiza ***whisper processor***. Finalmente hay que ajustar los datos al formato adecuado de entrada para el entrenamiento del modelo 16kHz.
3. Combinar los elementos del punto dos con **whisper processor**.
4. Entrenar y  evaluar el modelo.
* Métricas de evaluación.
* Inicializar el data collator.
* Cargar el pre-entrenamiento.


! info "Mi primera vez"

    Utilizo el código de ejemplo y guía que ofrece Hugging Face para realizar el fine tuning. Inicialmente lo intento con google colab, pero atención, el ejemplo del dataset de muestra da error. No se descarga. Lo intento en local y lo mismo. Resulta que el dataset ya no está disponible (al menos en las fechas que lo intenté).
    Cambio de dataset, y utilizo uno de mozilla con voces en varios idiomas, también está disponible en Hugging face, lo que facilita el uso ya que está preprocesado para utilizar train y test. El problema es que es demasiado grande (**107GB !!**), Google colab solo permite este espacio en la versión gratuita.
    Ciertamente la instalación de las librerías y el dataset, resulta inviable trasvarios intentos, utilizando diferentes opciones para reducir su tamaño (simplemente la descarga son horas !!).



Prueba una [versión de fine tuning desde colab](https://colab.research.google.com/drive/184wLPXdEnAeJH4bh8XrAHZjo8dLwYbT2?usp=sharing)


