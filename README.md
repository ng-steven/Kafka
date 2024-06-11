# Apache Kafka

## Overview

Apache Kafka is a distributed streaming platform that allows for building real-time data pipelines and streaming applications. It is designed to handle large volumes of data and provide high throughput, low latency, and fault tolerance.

## Table of Contents

- [Overview](#overview)
- [What is Kafka?](#what-is-kafka)
- [Kafka Architecture Foundations](#kafka-architecture-foundations)
- [Kafka Data Flow](#kafka-data-flow)
- [Kafka Producer](#kafka-producer)
- [Kafka Consumer](#kafka-consumer)
- [Getting Started](#getting-started)
- [References](#references)

## What is Kafka?

Kafka was originally developed by LinkedIn and later open-sourced as part of the Apache Software Foundation. It is used for building real-time streaming data pipelines and applications that adapt to data streams. Kafka is suitable for both offline and online message consumption.

### Key Features

- **Scalability**: Kafka can scale horizontally by adding more brokers to the cluster.
- **Durability**: Messages are persisted on disk and replicated within the cluster to prevent data loss.
- **Performance**: Capable of handling thousands of messages per second with low latency.
- **Fault Tolerance**: Kafka handles failure of nodes in the cluster gracefully.

## Kafka Architecture Foundations

Kafka's architecture is composed of several key components:

### Topics and Partitions

- **Topic**: A stream of records (messages) of a particular type. Topics are split into partitions.
- **Partition**: A topic is divided into partitions to allow parallel processing. Each partition is an ordered, immutable sequence of records.

### Brokers

- A Kafka cluster is composed of multiple brokers. Each broker is responsible for a subset of the partitions.

### Producers

- Producers are clients that publish (write) records to Kafka topics.

### Consumers

- Consumers are clients that subscribe to (read) records from Kafka topics.

### Zookeeper

- Zookeeper is used to coordinate and manage the Kafka cluster.

## Kafka Data Flow

The data flow in Kafka follows a straightforward path from producers to consumers via topics.

1. **Producers** send records to Kafka topics.
2. Kafka brokers store records in partitions within topics.
3. **Consumers** subscribe to topics and consume records from partitions.

### Example Data Flow

1. A producer publishes a message to the `topic1`.
2. The message is stored in a specific partition within `topic1` based on the partitioning strategy.
3. A consumer subscribed to `topic1` reads the message from the assigned partition.

## Kafka Producer

Producers are responsible for sending data to Kafka topics. They push records to topics, and Kafka brokers ensure they are properly stored in the corresponding partitions.

### Key Concepts

- **Message**: The data sent by the producer.
- **Key**: An optional attribute to control which partition a message is sent to.
- **Partitioning**: The mechanism for determining which partition a message goes to.

### Example Code (Python)

```python
from kafka import KafkaProducer

producer = KafkaProducer(bootstrap_servers='localhost:9092')
producer.send('topic1', b'Hello, Kafka!')
producer.close()
```

If you need more information and details: https://kafka.apache.org/documentation/
