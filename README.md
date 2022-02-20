## Dataset: Stellar Classification Dataset - SDSS17

### Recurso sacado de https://www.kaggle.com/fedesoriano/stellar-classification-dataset-sdss17
### Contexto

Este datasat tiene como objetivo clasificar estrellas, galaxias y cuásares en función de sus características espectrales.

Es importante conocer que la catalogación temprana de las estrellas y su distribución en el cielo ha llevado a la comprensión de que forman nuestra propia galaxia y, siguiendo la distinción de que Andrómeda era una galaxia separada de la nuestra, numerosas galaxias comenzaron a estudiarse a medida que se construían telescopios más potentes.

Los datos consisten en 100.000 observaciones del espacio tomadas por el SDSS (Sloan Digital Sky Survey). Cada observación se describe mediante 17 columnas de características y una columna de clase que la identifica como estrella, galaxia o cuásar.

A continuación se menciona cada una de las columnas que contiene el dataset:

| Variables | Descripción | 
| --- | --- | 
| obj_ID | Identificador de objeto, el valor único que identifica el objeto en el catálogo de imágenes utilizado por el CAS. | 
| alfa | Ángulo de ascensión derecha (en la época J2000). | 
| delta | Ángulo de declinación (en la época J2000).| 
| u | Filtro ultravioleta en el sistema fotométrico. | 
| g | Filtro verde en el sistema fotométrico. | 
| r | Filtro rojo en el sistema fotométrico. | 
| i | Filtro de infrarrojo cercano en el sistema fotométrico. | 
| z | Filtro infrarrojo en el sistema fotométrico. | 
| run_ID | Número de ejecución utilizado para identificar la exploración específica. | 
| rereun_ID | Número de repetición para especificar cómo se ha procesado la imagen. | 
| cam_col | Columna de la cámara para identificar la línea de escaneo dentro de la ejecución. | 
| field_ID | Número de campo para identificar cada campo.|
| spec_obj_ID |ID único utilizado para los objetos espectroscópicos ópticos (esto significa que 2 observaciones diferentes con el mismo spec_obj_ID deben compartir la clase de salida).|  
| class | clase de objeto (galaxia, estrella u objeto cuásar). | 
| redshift | valor de redshift basado en el aumento de la longitud de onda. | 
| plate | ID de la placa, identifica cada placa en SDSS. | 
| MJD | Fecha juliana modificada, utilizada para indicar cuándo se tomó un dato determinado del SDSS. | 
| fiber_ID | ID de la fibra que identifica la fibra que apuntó la luz al plano focal en cada observación. | 


## Herramienta: WEKA
## Algoritmo: Árboles de decisión

### Concepto.
Un árbol de decisión es un diagrama en forma de árbol que muestra la probabilidad estadística o determina un curso de acción. Muestra a los analistas y, a los que toman las decisiones, qué pasos deben tomar y cómo las diferentes elecciones podrían afectar todo el proceso. 

### Descripción.
Un árbol de decisión es una especie de mapa en que se muestra cada una de las opciones de decisión posibles y sus resultados. Es útil para aquellas personas que tienen que tomar decisiones, ya que te permite comparar diferentes decisiones y acciones según sus costos, probabilidades y beneficios.

### Importancia.
Los árboles de decisión crean un modelo de clasificación basado en diagramas de flujo. Clasifican casos en grupos o pronostican valores de una variable dependiente (criterio) basada en valores de variables independientes (predictoras).
Las ventajas de un árbol de decisión:
 - Facilita la interpretación de la decisión adoptada.
 - Facilita la comprensión del conocimiento utilizado en la toma de decisiones.
 - Explica el comportamiento respecto a una determinada decisión.
 - Reduce el número de variables independientes.
### Algoritmo:  Árbol de decisión - Random Forest
También conocidos en castellano como '"Bosques Aleatorios"' es una combinación de árboles predictores tal que cada árbol depende de los valores de un vector aleatorio probado independientemente y con la misma distribución para cada uno de estos. Es una modificación sustancial de bagging que construye una larga colección de árboles no correlacionados y luego los promedia[2].

En el artículo [3] describe las principales ventajas del algoritmo Random Forest son:

* Pueden usarse para clasificación o predicción: En el primer caso, cada árbol “vota” por una clase y el resultado del modelo es la clase con mayor número de “votos” en todos los árboles, de forma que cada nueva observación se presenta a cada uno de los árboles y se asigna a la clase más “votada”. En el segundo caso, el resultado del modelo es el promedio de las salidas de todos los árboles.
* El modelo es más simple de entrenar en comparación con técnicas más complejas, pero con un rendimiento similar.
* Tiene un desempeño muy eficiente y es una de las técnicas más certeras en bases de datos grandes.
* Puede manejar cientos de predictores sin excluir ninguno y logra estimar cuáles son los predictores más importantes, es por ello que esta técnica también se utiliza para reducción de dimensionalidad.
* Mantiene su precisión con proporciones grandes de datos perdidos.

Por otra parte en el artículo [3] describe, sus principales desventajas son las siguientes:

* La visualización gráfica de los resultados puede ser difícil de interpretar.
* Puede sobre ajustar ciertos grupos de datos en presencia de ruido.
* Las predicciones no son de naturaleza continua y no puede predecir más allá del rango de valores del conjunto de datos usado para entrenar el modelo. En el caso de predictores categóricos con diferente número de niveles, los resultados pueden sesgar hacia los predictores con más niveles.
* Se tiene poco control sobre lo que hace el modelo (en cierto sentido es como una caja negra).

### Pasos para la aplicación del Algoritmo.
1. Una vez descargado el dataset se procedió a dividirlo en dos partes al conjunto datos, correspondiente al 80% para entrenamiento y 20 % para pruebas.
2. Se identifica cuales son las variables dependientes, independientes y las que causan ruido o no tienen importancia, a continuación se describe:
- Variable dependiente: class.
- Variables independientes: alpha, delta, u, g, r, i, z, MJD, redshift.
- Variables sin importancia para el análisis(son identificadores): run_ID, rerun_ID, cam_col, field_ID, spec_obj_ID, fiber_ID, obj_ID, plate.
3. Una vez importado el dataset que contiene el 80% de los datos, se procede al entrenamiento se sigue los siguientes pasos:
   a. Seleccionar la pestaña classify.
   b. Seleccionar el algoritmo de entrenamiento (RandomForest). 
   c. Seleccionar Use Training set.
   d. Seleccionar la variable dependiente.
   e. Presionar start.
   
4. Una vez importado el dataset, se seleccionó el algoritmo de clasificación de árbol RandomForest.}
5. Para usar el algoritmo se utilizó los parámetros que traen por defecto en el apartado de propiedades y así mismo se modificaron algunos de ellos para hacer la comparativa de los resultados.
- Parámetros por defecto:

- Parámetros modificados: 

Como se puede visualizar los parámetros modificados son “bagSizePercent” y “numIterations”, con valores de 25 y 20 respectivamente, esto se lo hizo con la finalidad de visualizar los cambios en los resultados finales al realizar el entrenamiento del modelo. Además, el tamaño de cada muestra aleatoria se especifica en bagSizePercent, qué es un tamaño como porcentaje del conjunto de datos de entrenamiento sin procesar. El valor predeterminado es 100%, lo que creará una nueva muestra aleatoria del mismo tamaño que el conjunto de datos de entrenamiento, pero tendrá una composición diferente. Mientras el numIterations es el número de interacciones máximas del modelo base que se desea crear. 

6. A continuación, se procede a seleccionar el botón de “Start” para que el modelo empiece a entrenar.

###Análisis e Interpretación de los datos.
Los resultados obtenidos por la herramienta Weka son los siguientes:

Principalmente se realizó el entrenamiento utilizando los parámetros por defecto para el análisis haciendo uso del 80% de los datos del dataset con lo cual se obtuvo un resultado general de clasificación correcta de un 99.99% y con un valor de clasificación incorrecta de 0.0025%, lo que muestra una clasificación precisa.


A continuación se procedió a modificar los parámetros  “bagSizePercent” y “numIterations”, con valores de 25 y 20 respectivamente, con lo que se obtuvo un cambio en las estadísticas del entrenamiento. Los valores obtenidos con el cambio de los parámetros son a nivel general tiene un 98.31% de efectividad y 1.68% de error al clasificar los datos.


Por lo tanto, dentro del análisis se puede visualizar que el algoritmo RandomFores pudo clasificar de forma correcta con sus valores predeterminados, así como modificando sus parámetros para la clasificación del DATASET empleado, con lo cual arrojó valores de 99.99% en sus valores predeterminados y un 98.31% actualizando los parámetros antes descritos con lo que se puede inferir que RandomFores es apropiado para la clasificación del DATASET utilizado, además se puede observar que el valor más notorio son los 970  observaciones que fueron colocados como falsos negativos por lo que estos fueron clasificados como GALAXY.
