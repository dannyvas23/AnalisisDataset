## Dataset: Stellar Classification Dataset - SDSS17

### Recurso sacado de https://www.kaggle.com/fedesoriano/stellar-classification-dataset-sdss17
Contexto

Este datasat tiene como objetivo clasificar estrellas, galaxias y cuásares en función de sus características espectrales.

Es importante conocer que la catalogación temprana de las estrellas y su distribución en el cielo ha llevado a la comprensión de que forman nuestra propia galaxia y, siguiendo la distinción de que Andrómeda era una galaxia separada de la nuestra, numerosas galaxias comenzaron a estudiarse a medida que se construían telescopios más potentes.

Acontinuación se menciona cada una de las columnas que contiene el dataset:

| Variables | Descripción | 
| --- | --- | 
| obj_ID | Identificador de objeto, el valor único que identifica el objeto en el catálogo de imágenes utilizado por el CAS. | 
| alfa | Ángulo de ascensión derecha (en la época J2000). | 
| delta | Ángulo de declinación (en la época J2000).| 
| u | Filtro ultravioleta en el sistema fotométrico. | 
| g | Filtro verde en el sistema fotométrico. | 
| r | Filtro rojo en el sistema fotométrico. | 
| i | Generates the code of the function that given the structure variable. | 
| z | Generates the code of the function that given the structure variable. | 
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


