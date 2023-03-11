# Proyectos de inteligencia artificial
***No es un producto, es un proceso***


Comienza con la definición y concreción del problema, de esta forma se podrá valorar el resultado conseguido.

Es necesario conocer los datos disponibles. Cuál va a ser el origen de los datos. Son datos estructurado o no estructurados. 

Los datos requerirán de una fase de preprocesado para poder adaptarlos a los procesos matemáticos del modelo de inteligencia artificial que se va a utilizar.

El modelo elegido, se basa en algortimos y estructuras matemáticas. Existe una bibliografía (white papers) que recomienda su uso para determinados problemas, así commo, ilustra su uso.

Realización de un proceso de entrenamiento. No siempre es necesario comenzar un entrenamiento desde el principio, al contrario, es muy adecuado aprovechar modelos ya entrenados para ajustar parámetros de reentrenamiento para el problema que se quiere resolver.

Hay que establecer métricas de análisis de rendimiento del modelo, de esta manera se puede conocer la efectividad de la solución que se está encontrando.

El despliegue del modelo en un entorno de producción, es clave para establecer su utilidad.

!!! info "Un proyecto completo"
    También es importante considerar que un proyecto basado en una solución de inteligencia artificial, no tiene porqué limitarse al uso de un único modelo.

## El origen de datos

El dato es fundamental en un proyecto de inteligencia artificial. Se obtiene de forma masiva, y su procesamiento puede ser en tiempo real (en streamming) o directo accediendo a un fichero estático.

El origen puede ser **interno**, considerando datos generados por la propia organización. O **externos** generados y conseguidos en fuentes públicas o privadas adquiridos para su uso.

![cientifico de datos moderno](https://www.business-science.io/assets/2019-05-23-financial-data-scientist/modern_data_scientist.jpg)

!!! info "Nota"
    El analista de datos busca conclusiones y alertas sobre métricas que la organización considera críticas. El científico de datos construye nuevos modelos y busca conocimiento sobre indicadores que la organización aún no sabe que son importantes.


## Definir el problema
Definir el problema que se quiere resolver o el planteamiento que se quiere comprobar. No se trata de comprobar aquello que uno piensa, sino concretar de manera objetiva una medida de la solución que se va conseguir, teniendo en cuenta los objetivos de la organización.

## Selección de datos
No únicamente los disponibles internamente, también los internos que no se disponen (se podría intentar obtener) y los externos que se pueden incorporar (algunos a coste cero y otros de pago).

Ejemplo de datos internos, son los que se generan en los procesos de negocio de la organización. Los datos externos pueden ser, comentarios de redes sociales, datos abiertos generados por otras entidades (como información atmosférica), o datos adquiridos de otras organizaciones.

## Preprocesamiento
Conocer los datos es clave para poder iniciar el proceso de aprendizaje del modelo.

Si existen datos vacios, hay que determinar un criterio para completarlos o eliminarlos. También hay que detectar anomalías que puedan provocar desviaciones en el modelo. Así mismo, es relevante detectar posibles sesgos en las muestras de datos. 

## Transformación
Se transforman los datos en bruto para poderlos utilizar en los algoritmos deseados. Normalmente regularizando el formato de los datos, estandarizando los valores para que no existan descompesaciones con los valores numéricos. El resultado debe ser el dataset.

El dataset se divide en un grupo de datos para el entrenamiento y otro para la validación del modelo (train y test).

## Descubrimiento de conocimiento
La etapa menos compleja, y más visible. Se aplican los algoritmos deseados. Hay que decidir si se utiliza un algoritmo supervisado o no supervisado, si se trata de clasificar o predecir.

La mayor parte de los algoritmos ya están disponibles en librerías de fácil uso, solo hay que aplicarlos.

## Evaluación
El resultado es simplemente un modelo. Hay que comprobar y entender si el modelo responde a las cuestiones planteadas inicialmente. Es el momento de considerar si es necesario volver a empezar, sea desde cualquiera de las fases, para mejorar el resultado obtenido o por el contrario el modelo es aceptable y pasa a producción.

Hay que establecer métricas que permitan determinar la validez del modelo.

## Producción
El motivo principal de todo el proceso es que el conocimiento obtenido sea útil. Presentar el resultado de forma inteligible: visualizaciones personalizadas, cuadros de mando o entrada a otros sistemas.

## Volver a empezar
El proceso no acaba nunca. Siempre se pueden añadir nuevos datos, hay que definir un proceso repetible que se adapte a las interferencias existentes en el día a día.
