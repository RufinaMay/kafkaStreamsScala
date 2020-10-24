# First steps in Kafka Streams with Scala

More information can be found in official [documentation](https://kafka.apache.org/26/documentation/streams/quickstart)

## Download 
Download Kafka on official page [link](https://www.apache.org/dyn/closer.cgi?path=/kafka/2.6.0/kafka_2.13-2.6.0.tgz). For now the most recent one is 2.6.0.

Extract downloaded files 
```
tar zxvf kafka-2.6.0-src.tgz
cd kafka-2.6.0-src/
```

## Start Kafka server

Run a ZooKeeper server ``` bin/zookeeper-server-start.sh config/zookeeper.properties ```
Run a Kafka server ```  bin/kafka-server-start.sh config/server.properties ```

## Create input and output topics

Note: Before running your code to consume or produce to some topic, this topic should be created, otherwise you will get an exception.
Open a new tab in the terminal and run the following commands to create zn input and output topics for our application:
```
bin/kafka-topics.sh --create \
    --bootstrap-server localhost:9092 \
    --replication-factor 1 \
    --partitions 1 \
    --topic streams-plaintext-input
Created topic "wordcount-input".
```

 ``` 
 bin/kafka-topics.sh --create \
    --bootstrap-server localhost:9092 \
    --replication-factor 1 \
    --partitions 1 \
    --topic streams-wordcount-output \
    --config cleanup.policy=compact
Created topic "wordcount-output".
```

To check all of existing topics run: ``` bin/kafka-topics.sh --list --zookeeper localhost:2181 ```

## Write code 

