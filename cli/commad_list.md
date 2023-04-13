#Kafka CLI Demo 
* Print messages out of order
* Print timestamps, keys and values
* Describe a topic, see partitions
* Consume messages as a group with one idle consumer
* Consume messages as a group from the beginning
* Consume messages as a different groups
* Examine default consumer group behaviour, read from beginning
* Reset consumer group offsets

##kafka-topics.sh

`kafka-topics --bootstrap-server localhost:29092 --list`

`kafka-topics --bootstrap-server localhost:29092 --topic first_topic --create`

`kafka-topics --bootstrap-server localhost:29092 --topic first_topic --create --partitions 2 --replication-factor 1`

`kafka-topics --bootstrap-server localhost:29092 --describe --topic first_topic`

`kafka-topics --bootstrap-server localhost:29092 --topic first_topic --delete`

##kafka-console-producer.sh

`kafka-console-producer --bootstrap-server localhost:29092 --topic first_topic`

`kafka-console-producer --bootstrap-server localhost:29092 --topic first_topic --producer-property acks=all`

`kafka-console-producer --bootstrap-server localhost:29092 --topic first_topic --property parse.key=true --property key.separator=:`

##kafka-console-consumer.sh

`kafka-console-consumer --bootstrap-server localhost:29092 --topic first_topic`

`kafka-console-consumer --bootstrap-server localhost:29092 --topic first_topic --from-beginning`

`kafka-console-consumer --bootstrap-server localhost:29092 --topic first_topic --formatter kafka.tools.DefaultMessageFormatter --property print.timestamp=true --property print.key=true --property print.value=true --from-beginning`

`kafka-console-consumer --bootstrap-server localhost:29092 --topic first_topic --group first_group`

##kafka-consumer-groups.sh

`kafka-consumer-groups --bootstrap-server localhost:29092 --list`

`kafka-consumer-groups --bootstrap-server localhost:29092 --describe --group first_group`

`kafka-consumer-groups --bootstrap-server localhost:29092 --group first_group --reset-offsets --to-earliest --execute --all-topics`

`kafka-consumer-groups --bootstrap-server localhost:29092 --group first_group --reset-offsets --to-latest --execute --all-topics`

`kafka-consumer-groups --bootstrap-server localhost:29092 --group first_group --reset-offsets --shift-by 2 --execute --all-topics`

`kafka-consumer-groups --bootstrap-server localhost:29092 --group first_group --reset-offsets --shift-by -2 --execute --all-topics`