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
   
   <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/xXsw9h2W/image6.png">
</p>
3. Una vez importado el dataset que contiene el 80% de los datos, se procede al entrenamiento se sigue los siguientes pasos:
   a. Seleccionar la pestaña classify.
   b. Seleccionar el algoritmo de entrenamiento (RandomForest). 
   c. Seleccionar Use Training set.
   d. Seleccionar la variable dependiente.
   e. Presionar start.
<p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/s17C5TYh/image1.png">
</p>
   
4. Una vez importado el dataset, se seleccionó el algoritmo de clasificación de árbol RandomForest.
   <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/jLT0cyck/image2.png">
</p>

5. Para usar el algoritmo se utilizó los parámetros que traen por defecto en el apartado de propiedades y así mismo se modificaron algunos de ellos para hacer la comparativa de los resultados.
- Parámetros por defecto:
   <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/7fNvWbQP/image3.png">
</p>

- Parámetros modificados: 
 <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/SX2vkKVM/image17.png">
</p>
Como se puede visualizar los parámetros modificados son “bagSizePercent” y “numIterations”, con valores de 25 y 20 respectivamente, esto se lo hizo con la finalidad de visualizar los cambios en los resultados finales al realizar el entrenamiento del modelo. Además, el tamaño de cada muestra aleatoria se especifica en bagSizePercent, qué es un tamaño como porcentaje del conjunto de datos de entrenamiento sin procesar. El valor predeterminado es 100%, lo que creará una nueva muestra aleatoria del mismo tamaño que el conjunto de datos de entrenamiento, pero tendrá una composición diferente. Mientras el numIterations es el número de interacciones máximas del modelo base que se desea crear. 

6. A continuación, se procede a seleccionar el botón de “Start” para que el modelo empiece a entrenar.


### Análisis e Interpretación de los datos.
Los resultados obtenidos por la herramienta Weka son los siguientes:

Principalmente se realizó el entrenamiento utilizando los parámetros por defecto para el análisis haciendo uso del 80% de los datos del dataset con lo cual se obtuvo un resultado general de clasificación correcta de un 99.99% y con un valor de clasificación incorrecta de 0.0025%, lo que muestra una clasificación precisa.

 <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/GBV6yD9K/image9.png">
</p>
A continuación se procedió a modificar los parámetros  “bagSizePercent” y “numIterations”, con valores de 25 y 20 respectivamente, con lo que se obtuvo un cambio en las estadísticas del entrenamiento. Los valores obtenidos con el cambio de los parámetros son a nivel general tiene un 98.31% de efectividad y 1.68% de error al clasificar los datos.

 <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/mPrnpjHV/image16.png">
</p>

Por lo tanto, dentro del análisis se puede visualizar que el algoritmo RandomFores pudo clasificar de forma correcta con sus valores predeterminados, así como modificando sus parámetros para la clasificación del DATASET empleado, con lo cual arrojó valores de 99.99% en sus valores predeterminados y un 98.31% actualizando los parámetros antes descritos con lo que se puede inferir que RandomFores es apropiado para la clasificación del DATASET utilizado, además se puede observar que el valor más notorio son los 970  observaciones que fueron colocados como falsos negativos por lo que estos fueron clasificados como GALAXY.


### Predicciones con nuevos datos como ejemplo de aplicación del algoritmo
1. Se agregó otra columna denominada “class_value”, en la cual permitirá realizar las predicciones posteriores.
 <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/crhjc2rr/image4.png">
</p>
2. División del dataset, 80% para entrenamiento  y 20% para pruebas.
 <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/F7N83NFM/image7.png">
</p>
3. Guardado de archivos test y train en formato CSV.
 <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/XZpTqLNX/image8.png">
</p>
4. Para subir los datos con los cuales se va a realizar la predicción, en base al modelo antes entrenado, se tiene que ingresar en Test options en la sección de supplied test set, el mismo que presenta una pestaña que permite subir un dataset nuevo y escoger la class o variable con la cual se va a realizar la predicción
 <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/hzm6bGdB/image10.png">
</p>
Cabe destacar que para realizar una predicción correcta se tiene que agregar un dataset con el campo de la variable dependiente o class con el **signo de interrogación (?)**,  el cual permite al algoritmo de weka analizar dicha variable en base a los valores antes ingresados al modelo. En la siguiente ilustración se muestra un ejemplo del dataset utilizado para el análisis
 <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/QB2ntrnn/image13.png">
</p>
5. Una vez subidos los nuevos datos el algoritmo RamdonForest realiza la predicción creando varios árboles para luego usarlos con la variable de interés que en este caso es la clase a la cual se le agregó el signo de interrogación al subir el dataset. Por lo que se puede ver en la siguiente ilustración presenta una tabla con los valores obtenidos de la predicción, la cuen en la columna de predicted se observa que las clases de clases tiene un valor y el nombre al cual pertenecen como por ejemplo: **1 pertenece a GALAXY, 2 pertenece a QSO y 3 a STAR**. Como se puede ver en la columna de predicction existen valores de 0.5 hasta 0.7 con lo que se puede inferir que el modelo está realizando predicciones precisas
 <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/NL1ZK5t8/image14.png">
</p>
En la tabla de summary se presenta que tiene un porcentaje de clasificación  correcta de un 90.145% y una clasificación incorrecta de 9.855% lo cual el modelo está clasificando correctamente las clases en base a las variables independientes con las cuales fue entrenado el modelo anteriormente
 <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/yDYq4Bwm/image5.png">
</p>
Dentro de la matriz de confusión se puede evidenciar que el modelo está funcionando correctamente ya que en la diagonal principal los valores son mayores a los valores de los falsos positivos y falsos negativos, por ejemplo  se puede ver que el valor de verdadero positivos de la primera columna clasifico que 11684 pertenecen a la clase GALAXY y que tiene 29 falsos positivos los cuales los clasificó como QSO y 96 como STAR, de igual forma los falsos negativos que seleccionó son 1844 los mismos que los clasificó como GALAXY.   <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/LgM7yMtZ/image11.png">
</p>
### Requerimientos previos mínimos
1. Ingresar al repositorio en el siguiente enlace y descargar los archivos de train y test:  https://github.com/dannyvas23/AnalisisDataset
2. Tener instalado Java en windows:
  <p align="center">
  <img width="300" height="300" src="https://i.postimg.cc/WdfHBZmV/image15.png">
</p>
3. Tener instalado la herramienta Weka. Disponible en: https://sourceforge.net/projects/weka/files/weka-3-8/3.8.6/weka-3-8-6-azul-zulu-windows.exe/download?use_mirror=razaoinfo

### LINK VIDEO:
https://www.youtube.com/watch?v=GCFZXFH7ObU


