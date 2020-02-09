# San Francisco Crimes with Apache Spark Structured Streaming

In this project I use Apache Spark Structured Streaming to analyze crimes in the city of San Francisco.

## Prerequisites
* Apache Spark 2.4.3
* Scala 2.11.x
* Java 1.8.x
* Kafka build with Scala 2.11.x
* Python 3.6

## Setup
```
./start.sh
```

run the following commands:


1. Start Zookeeper and Kafka
```
bin/zookeeper-server-start.sh config/zookeeper.properties
bin/kafka-server-start.sh config/server.properties
```

The `config` directory includes configuration files for  Zookeeper & Kafka.

2. Start  producer server to read JSON data and write to a Kafka topic:
```
python kafka_server.py
```

3. Start  consumer server to read JSON data from the Kafka topic:
```
python consumer_server.py
```
4. Display Output to the console
```
kafka-console-consumer --topic calls --from-beginning --bootstrap-server localhost:9092
```
This consumer will provide output as show in the screenshot below.
### Kafka Consumer Console Output

![kafka consumer output](https://github.com/Sichon3/Data-Streaming-Nanodegree-SF-Crime-Data-Project-Files/blob/master/Kafka%20Consumer%20Console%20Output.PNG)


4. Start Apache Spark Structured Streaming consumer:
```
spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.4 --master local[*] data_stream.py
```

The `config` includes the configuration file for Spark.
couldn`t submit progress because it takes very long to start apache spark structred streaming consumer


## Questions

1. How did changing values on the SparkSession property parameters affect the throughput and latency of the data?

The latency affects throughput, since the execution of the next batch waits until the current batch is processed by the query. 

2. What were the 2-3 most efficient SparkSession property key/value pairs? Through testing multiple variations on values, how can you tell these were the most optimal?

...
