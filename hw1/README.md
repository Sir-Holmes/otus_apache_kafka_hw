# Последовательность действий
```bash
wget https://dlcdn.apache.org/kafka/4.3.0/kafka_2.13-4.3.0.tgz
tar -xzf kafka_2.13-4.3.0.tgz
cd kafka_2.13-4.3.0
sudo apt install openjdk-25-jdk -y
KAFKA_CLUSTER_ID="$(bin/kafka-storage.sh random-uuid)"
bin/kafka-storage.sh format --standalone -t $KAFKA_CLUSTER_ID -c config/server.properties
vi config/server.properties
bin/kafka-server-start.sh config/server.properties

bin/kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092
>This is my first event
>This is my second event

bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092
The consumer rebalance protocol (KIP-848) is production-ready! Set group.protocol=consumer to try it out. See https://kafka.apache.org/documentation/#consumer_rebalance_protocol
This is my first event
This is my second event
```
