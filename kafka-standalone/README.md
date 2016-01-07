# kafka-standalone

Example installing and running Kafka
 
Kafka port: 9092
Zookeeper port: 2181

## Quick Start

Create test topic

    bin/kafka-topics.sh --create --zookeeper localhost:2181 --topic test --partitions 1 --replication-factor 1

Verify topic creation

    bin/kafka-topics.sh --list --zookeeper localhost:2181

Write data to topic

    bin/kafka-console-producer.sh --broker localhost:9092 --topic test <<< "Test Message"

Read data to topic

    bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic test --from-beginning
