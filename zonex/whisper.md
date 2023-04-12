# Primeros pasos con Whisper

Este model gratuito y abierto, está disponible para su uso y adaptación a cualquier circunstancia.

Desarrollado por OpenAI. Entrenado con miles de horas basadas en lecturas de la Wikipedia. Ofrece la posibilidad de multilenguaje.

Se basa en la arquitectura ***transformer***, que está consiguiendo resultado impresionanentes para problemas de secuenciación. Y en particular para Procesamiento de Lenguaje Natural.

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


No sirve de nada esparar 15 segundos para obtener un resultado que no es correcto. En este sentido resulta adecuado elegir la versión **small**.

Hay que tener en cuenta el volumen del modelo y todo el procesamiento que supone. Disponer de procesamiento paralelo facilitará obtener un resultado más rápidamente.



