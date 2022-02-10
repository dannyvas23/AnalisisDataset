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


## Herramienta: IBM SPSS
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

Describir los pasos que se deben seguir para la aplicación del algoritmo.

Algoritmo: Árbol de decisión, con método de crecimiento CHAID y CRT.
Permite crear en cada partición desde dos subconjuntos hasta el mismo número de grupos que de categorías de la variable predictora, consiguiendo reducir en mayor medida la varianza residual y, al mismo tiempo, mejorar la selección de otras variables explicativas.

1. Una vez importado el dataset, se seleccionó el algoritmo de clasificación de árbol.

![Screenshot](https://drive.google.com/drive/u/3/folders/1iCdTcN3PUW6Fw7Lz-Nk4tC1h5e-KUc0t)

2. Se identifica cuales son las variables dependientes, independientes y las que causan ruido o no tienen importancia, a continuación se describe:
Variable dependiente: class.
alpha
delta
u
g
r
i
z
MJD
redshift
Variables sin importancia para el análisis(son identificadores): 
run_ID
rerun_ID
cam_col
field_ID
spec_obj_ID
fiber_ID
obj_ID
plate

3. Se selecciona el método de crecimiento que mejor nos parezca conveniente usar.


 -El método de crecimiento que se utilizó fue el CRT (Árboles de clasificación y regresión), el cual divide los datos en segmentos para que sean lo más homogéneos posible respecto a la variable dependiente. 

 -Además, se usó CHAID (Detector automático de interacción chi-cuadrado), el mismo que explora datos de forma rápida y eficaz, y crea segmentos y perfiles con respecto al resultado deseado. CHAID elige la variable independiente (predictora) que presenta la interacción más fuerte con la variable dependiente.

4. A continuación, se procede a seleccionar el botón de “Aceptar” para que se procesen los datos.

-Interpretarlos y realizar predicciones con nuevos datos como ejemplo de aplicación del algoritmo.

Los resultados obtenidos por la herramienta IBM SPSS son los siguientes:

Con el método de crecimiento CRT se alcanzó una acierto del 96,6% frente al método CHAID con 96,1%, lo cual permite analizar que la clasificación fue mejor en el primer método, además hay que señalar que en los datos clasificados por “QSO” y “START” existen gran variación, como por ejemplo: lo que provoca que la primera clase mencionada anteriormente existen un total de 2607 falsos negativos, lo que quiere decir que esos valores reales son de la clase “QSO” pero el modelo los predijo como valores “Galaxy”, por lo que tanto, pierde efectividad en la predicción dando un porcentaje de 86,2% (El error correspondiente sería del 13,8% que serían un total de 2610 muestras clasificadas en otros aspectos).

**IMAGENES ALEXIS**

|  |RESUMEN DE MODELO CHAID| | 
| --- | --- | ---|   
|  | Método de crecimiento | CHAID | 
|  | Variable dependiente | class |
||Variables independientes|alpha, delta, u, g, r, i, z, MJD, redshift|
|**Especificaciones**|Validación|Ninguna|
||Máxima profundidad de árbol |5|
||Mínimo de casos en un nodo filial|100|
||Mínimo de casos en un nodo paren |50|
| --- | --- | ---| 
||Variables independientes incluidas|redshift, r, u, z, i, alpha, MJD, g|
||Número de nodos|37|
|**Resultados**|Número de nodos terminales |19|
||Profundidad|5|
