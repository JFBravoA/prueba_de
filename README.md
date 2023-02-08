# prueba_de

**Razonamiento de la solución del reto para el rol de Data Engineering

Para resolver el reto, opté por utilizar Python. Así, comencé definiendo una función que realiza el scraping del servicio web, la descompresión de los archivos y el procesamiento de los datos para convertirlos en un dataframe de Pandas. De esta forma, dicha función se invoca dentro de un loop que se ejecuta en automático cada hora debido al uso de la función sleep() del módulo "time", que permite detener un proceso durante un determinado periodo de tiempo. Asimismo, cada vez que se ejecuta el proceso, los datos extraídos se concatenan en un dataframe, de tal manera que, cada dos horas, se realiza la agrupación por municipio y se calculan las temperaturas y precipitaciones promedio de las útlimas dos horas. Esto se realizó colocando un contador que se actualiza con cada iteración, y cuando el contador es un número par (es decir, cada dos horas), se realizan las agrupaciones. Finalmente, el archivo más reciente en la carpeta data_municipios es identificado en automático y se realiza el cruce con los datos de dicho archivo. Las tablas son guardadas en las rutas indicadas, versionadas por fecha y hora, y una copia con la data más actual se guarda en la carpeta “current”.

**Puntos fuertes:

Es una solución sencilla para esta situación plasmada en un lenguaje versátil y conocido como lo es Python, que no requiere de softwares especializados para realizar las tareas de extracción, automatización ni almacenado de los datos. Esto permitiría que el equipo de Data Science pueda incorporar la solución directamente en sus códigos.

Asimismo, es una solución funcional, siempre y cuando no se requiera el almacenaje de una gran cantidad de datos.

**Puntos débiles:

Existen plataformas que permitirían la automatización del proceso de una manera más eficiente y óptima, como por ejemplo, Apache Airflow o Docker. Esto evitaría el uso de loops y condicionales como se propone en esta solución.
Asimismo, tal como se encuentra el código actualmente, es necesario introducir la cantidad de horas deseadas manualmente, y en dado caso que se desee correr indefinidamente, se tendría que recurrir a un loop infinito, lo cual es ineficiente. 
Finalmente, si el proceso se desea escalar o se decide incorporar nuevos procesos que incluyan una cantidad masiva de datos, habría que recurrir a otras herramientas de despliegue.

**¿Qué mejoras propondrías a tu solución para siguientes versiones?

Automatización de la ejecución del proceso en otra plataforma para evitar el uso de loops, condicionales y modificación de código manualmente.
Almacenado de los datos de entrada y de salida en un servidor de SQL para evitar consumir CSVs guardados localmente, lo que puede llenar la memoria y ser ineficiente.
Limpiar y optimizar código.
En caso de ser necesario escalar el proceso, migrar la solución a una plataforma como AWS.

**Tu solución le ha gustado al equipo y deciden incorporar otros procesos, habrá nuevas personas colaborando contigo, ¿Qué aspectos o herramientas considerarías para escalar, organizar y automatizar tu solución?

Para escalar y organizar la solución, almacenar los datos en un servidor de SQL, y en dado caso de ser necesario, migración a PySpark (AWS) para desplegar la solución con grandes cantidades de datos. Para la automatización de la solución, utilizar Docker o Apache Airflow en lugar de usar loops y condicionales como se propuso.
