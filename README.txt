Docker Jupyter + Spark:
source:
Jupyter Notebook Python, Scala, R, Spark, Mesos Stack
https://github.com/jupyter/docker-stacks/tree/master/all-spark-notebook

-- Local folder
/dev/STAT

-- Notebook startup
import pyspark
sc = pyspark.SparkContext()
sqlContext = pyspark.SQLContext(sc)

stat_all = sqlContext.read.format('csv').options(header='true', inferSchema='true').load('getstat_com_serp_report_201707.csv')

-- Docker Startup
docker run -it --rm -p8888:8888 -v c:/dev/STAT:/home/jovyan/work jupyter/all-spark-notebook
-e "TZ=Americas/Vancouver"