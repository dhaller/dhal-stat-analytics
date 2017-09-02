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


docker-machine.exe ssh default "sudo date -u $(date -u +%m%d%H%M%Y)"

docker run -it --rm -p8888:8888 -v c:/dev/STAT:/home/jovyan/work -e TZ=America/Vancouver jupyter/all-spark-notebook

run as root:
>docker run -it --rm -p8888:8888 -v c:/dev/STAT:/home/jovyan/work -e TZ=America/Vancouver -e GRANT_SUDO=yes --user root jupyter/all-spark-notebook


Docker:
docker exec -it <containerIdOrName> bash

docker-machine ssh default "sudo date -u $(date -u +%m%d%H%M%Y)"
