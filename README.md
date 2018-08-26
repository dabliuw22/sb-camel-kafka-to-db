# Kafka to DB - Spring Boot and Apache Camel

En este proyecto crearemos un consumidor para Kafka con *Apache Camel* y realizaremos inserciones en H2 DB.

1. [Descargar](https://www.apache.org/dyn/closer.cgi?path=/kafka/1.1.0/kafka_2.11-1.1.0.tgz) Kafka y Zookeeper.

2. Descomprimir e ingresar al folder de Kafka:
```
cd kafka_x.y-z
```
3. Run Zookeeper:
```
$ ./bin/zookeeper-server-start.sh ./config/zookeeper.properties
```
4. Run Kafka:
```
$ ./bin/kafka-server-start.sh ./config/server.properties
```
5. Crear *message.t*:
```
$ ./bin/kafka-topics.sh --create --topic message.t -zookeeper localhost:2181 --replication-factor 1 --partitions 3
```
5. Crear Producer en Kafka:
```
$ ./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic message.t
```
6. Agregar un mensaje al Producer:
```
> {"id": 1, "name": "One", "username": "one"}
```
7. Correr el Proyecto y verificar que el registro fue insertado en la DB, para eso utilizaremos la consola de H2:
	* *http://localhost:8080/h2-console*