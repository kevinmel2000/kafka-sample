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
