# Kafka Learnings

## Installing Kafka

Download the kafka binaries from https://kafka.apache.org/downloads

Download & Extract to the desired path

Create a folder in Kafka Root folder named 'kafka-logs' , inside 'kafka-logs' folder create 2 more folders 
1) 'server' - folder will hold server logs
2) 'zookeeper' - folder will hold zookeeper logs

## Configuring Kafka

1) Open config/zookeeper.properties, 
    1) Change the 'dataDir' value to the path of the zookeeper folder that we created in earlier step
    2) Change 'maxClientCnxns' value to 1
2) Open config/server.properties
    1) Uncomment 'listeners' property line
    2) Change 'log.dirs' value to 'server' folder path that we created in earlier steps
    3) Cross check 'zookeeper.connect' value is pointed to same port as zookeeper,properties port. Mostly this will be 2181
    4) Change 'zookeeper.connection.timeout.ms' value to 60000 (in milliseconds). This is required for windows users as it takes longer time to connect to localhost:2181 when there are multiple network interfaces

## Starting the servers

1) Starting zookeper, In terminal: 
    ```terminal

    <KAFKA-ROOT-FOLDER>/bin/zookeeper-server-start.sh <KAFKA-ROOT-FOLDER>/config/zookeeper.properties

2) Starting Kafka, In Terminal
    ```terminal

    <KAFKA-ROOT-FOLDER>/bin/kafka-server-start.sh <KAFKA-ROOT-FOLDER>/config/server.properties

## Creating Kafka Topics

 ```terminal

<KAFKA-ROOT-FOLDER>/bin/kafka-topics.sh --create --topic <TOPIC_NAME> --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1

```


## Listing the created Kafka Topics

 ```terminal

<KAFKA-ROOT-FOLDER>/bin/kafka-topics.sh --bootstrap-server=localhost:9092 --list

```

## Open a new terminal to sending messages & run below command

```terminal

<KAFKA-ROOT-FOLDER>/bin/kafka-console-producer.sh --topic documentPublished --bootstrap-server localhost:9092

```

## Open a new terminal to receive messages & run below command

```terminal

<KAFKA-ROOT-FOLDER>/bin/kafka-console-consumer.sh --topic documentPublished --from-beginning --bootstrap-server localhost:9092

```

## Testing Producer and Consumer

Type anything and hit enter in producer terminal and you should be able to see in consumer terminal


## Producing messages in python
```terminal

pip install kafka-python

```

Refer main.py for producing messages in python




