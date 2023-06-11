# Kafka sample Docker image

# Dependencies

* Docker >= 20
* Docker Compose >= 2.x

# How to use

```bash
# Start the broker
$ docker compose up -d

# Create a topic
$ TOPIC_NAME=sample_topic
$ docker exec broker \
kafka-topics --bootstrap-server broker:9092 \
             --create \
             --topic ${TOPIC_NAME}

# Write messages to the topic
$ docker exec --interactive --tty broker \
kafka-console-producer --bootstrap-server broker:9092 \
                       --topic ${TOPIC_NAME}

# Read messages from the topic
$ docker exec --interactive --tty broker \
kafka-console-consumer --bootstrap-server broker:9092 \
                       --topic ${TOPIC_NAME} \
                       --from-beginning
```

See [this](https://developer.confluent.io/quickstart/kafka-docker/) for the details.
