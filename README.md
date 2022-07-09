<h1>Curso de Fundamentos de Spark y Big Data</h1>

<a href='https://colab.research.google.com/drive/1Aq_5hRcGupgKXUUvWw8NhR-u-RWYraBy?usp=sharing'>Notebook</a>

<h2>Introducción a los RDDs y DataFrames</h2>


Transformaciones
Acciones

No se visualizara los errores hasta realizar una acción

Principal abstracción de datos: Es la unidad básica, existen desde su inicio hasta su versión 3.0.
Distribución: Los RDD se dritribuyen y particionan a lo largo del clúster.
Creación simple: Al no poseer estructura formalmente, adoptan las más intuitiva.
Inmutabilidad: Posterior a su creación no se pueden modificar
Ejecución perezosa: A menos que se realice una acción.

Características de los DataFrame

Formato: A diferencia de un RDD poseen columnas, lo cual les otorga tipos de datos.
Optimización: Poseen una mejor implementación, lo cual los hace preferibles.
Facilidad de creación: Se pueden crear desde una base de datos externa, archivo o RDD existente.

¿Cuándo usar un RDD?

Cuando te interesa controlar el flujo de Spark.
Si eres usuario Python, convertir a RDD un conjunto permite mejor control de datos.
Estás conectándote a versiones antiguas de spark.

¿Cuándo usar DataFrames?

Si poseemos semánticas de datos complicadas.
Vamos a realizar tareas de alto nivel como filtros, mapeos, agregaciones, promedios o sumas.
Si vamos a usar sentencias SQL.

<h2>Instalación de Spark en Google Colab</h2>

```Bash
!apt update
```

```Bash
!apt upgrade
```

```Bash
# innstall java
!apt-get install openjdk-8-jdk-headless -qq > /dev/null

# install spark (change the version number if needed)
!wget -q https://archive.apache.org/dist/spark/spark-3.0.0/spark-3.0.0-bin-hadoop3.2.tgz

# unzip the spark file to the current folder
!tar xf spark-3.0.0-bin-hadoop3.2.tgz

# set your spark folder to your system path environment. 
import os
os.environ["JAVA_HOME"] = "/usr/lib/jvm/java-8-openjdk-amd64"
os.environ["SPARK_HOME"] = "/content/spark-3.0.0-bin-hadoop3.2"


# install findspark using pip
!pip install -q findspark
```

```Bash
from pyspark.sql import SparkSession
import findspark
```


```Bash
findspark.init()
spark = SparkSession.builder.master("local[*]").getOrCreate()
```

<h2>Transformaciones y acciones</h2>