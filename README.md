# kafka-sample
Simple Kafka Producer-Consumer implementation using Java

> original implementation from https://mapr.com/blog/getting-started-sample-programs-apache-kafka-09/

### Running Kafka and Zookeeper locally
- start zookeeper `zkeeper start`
- start kafka `kafka-server-start /usr/local/etc/kafka/server.properties`

### How tu run using Maven
- `mvn clean packages`
- run Producer `target/kafka-example producer`
- run Consumer `target/kafka-example consumer`

### Cleaning Up
- stop zookeper `zkeeper stop`
- terminate kafka using `ctrl+c`
- [ ] remove log produced by zookeper and kafka in mac

### From the github of https://github.com/mapr-demos/kafka-sample-programs
#### Send more messages
In a separate window, run the producer again without stopping the consumer. Note how the messages are displayed almost instantly by the consumer and the latencies measured by the consumer are now quite small, especially compared to the first time the consumer was run.

This isn't a real production-scale benchmark, but it does show that two processes can send and receive messages at a pretty high rate and with pretty low latency.

#### Fun Step: Mess with the consumer
While the producer is producing messages (you may want to put it in a loop so it keeps going) and the consumer is eating them, try killing and restarting the consumer. The new consumer will wait for about 10 seconds before Kafka assigns it to the partitions that the killed consumer was handling. Once the consumer gets cooking, however, the latency on the records it is processing should drop quickly to the steady state rate of a few milliseconds. You can have similar effect by using control-Z to pause the consumer for a few seconds but if you do that, the consumer should restart processing immediately as soon as you let it continue. The way that this works is if you pause for a short time, the consumer still has the topic partition assigned to it by the Kafka broker, so it can start right back up. On the other hand, if you pause for more than about 10 seconds, the broker will decide the consumer has died and that there is nobody available to handle the partitions in the topic for that consumer group. As soon as the consumer program comes back, however, it will reclaim ownership and continue reading data.
