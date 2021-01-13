# hello-spark
> create spark environment to test feature

## Prerequisites
- Docker
- docker-compose

## Run Spark in Cluster Mode
```shell
# start spark master and workers
docker-compose -f docker-compose.yml up -d
# exec spark master shell in local
docker exec -it spark bash
# run Java example in spark master shell
./bin/spark-submit \
  --class org.apache.spark.examples.SparkPi \
  --master spark://spark:7077 \
  --deploy-mode cluster \
  ./examples/jars/spark-examples_2.12-3.0.0.jar \
  100
# run Python example in spark master shell
./bin/spark-submit \
  --master spark://spark:7077 \
  ./examples/src/main/python/pi.py \
  100
```
### Notes
> You can open interface to see what happened in spark master and workers
- open spark master UI

    http://localhost:8080

- open spark worker UI
  
    http://localhost:8081
  
    http://localhost:8082

### What's Next
> Submit your spark application

---

## Test Pyspark with Jupyter Notebook
```shell
docker-compose -f docker-compose-notebook.yml up -d
# or simple one-liner if spark setup not required
docker run -it -p 8888:8888 jupyter/pyspark-notebook
```
