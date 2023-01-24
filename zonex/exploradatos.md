# Exploración básica de los datos

El primer paso en cualquier proyecto es conocer los datos con los que se trabaja. La librería Pandas es una buena herramienta para este propósito.

El elemento principal es el DataFrame. Es comparable a una hoja de cálculo Excel, o una tabla en una base de datos SQL.

### Pasos básicos habituales
    * Leer los datos y almacenarlos en un DataFrame. `read_csv()`.
    * Mostrar un resumen estadístico de los datos, `describe()`.

##### Interpretación de **describe**

- **`count`** indica la cantidad de filas no vaias. Hay que considerar que puede haber valores vacios * cuando alguna característica no existe en ese elemento.
- **`mean`** media de los valores.
- **`std`** Desviación estandar, mide la dispersión numérica de los valores.
- **`min`** Si se ordena cada columna de características de menor a mayor, el primer valor.
- **`25%`** Valor que se sitúa entre un 25% de valores menores y el resto mayores.
- **`50%`** Valor que se sitúa entre un 50% de valores menores y 50% de valores mayores.
- **`75%`** Valor que se sitúa entre un 75% de valores menores y 25% de valores mayores.
- **`max`** Valor mayor.

# Seleccionar datos para el modelo
De entre todos los datos del dataset, se pueden elegir algunas características (utilizando la intuición), pero también es posible utilizar **técnicas estadísticas** para automáticamente priorizar el uso de algunas características frente a otras.

!!! note    "columns"
    La propiedad `columns` muestra la lista de nombres de loas características del DataFrame.
    `.columns`


!!! note    "dropna"
    Se utiliza para eliminar los valores Na.
    `.dropna(axis=0)`

Para seleccionar un subconjunto de datos se puede hacer utilizando la notacion "punto", indicando el nombre de la característica en el DataFrame. Normalmente es útil para obtener el vector `y` con las etiquetas objetivo.

Otra forma, es crear una lista con los nombres de las columnas de las características del DataFrame. Se utliza para crear el vector X con los datos de entrada al modelo.


