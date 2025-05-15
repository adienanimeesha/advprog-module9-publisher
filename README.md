## 1. How much data your publisher program will send to the message broker in one run? 
The publisher sends five messages, each serializing and packing two strings. The first string contains a user_id consisting of a single character (1 byte) with a 4-byte length prefix. The second string contains a fifteen-character user_name (15 bytes), also with a 4-byte length prefix. This yields 5 bytes for the user_id and 19 bytes for the user_name, for a total of 24 bytes of payload per message. With all five messages published, the raw serialized data amounts to 5 × 24 = 120 bytes per run.

## 2. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?
It means that both publisher and subscriber are effectively pointing to the very same RabbitMQ instance running on my local machine. The first guest is the username, the second guest the corresponding password, localhost tells the client to connect to a broker on the same host, and :5672 selects the default AMQP port where RabbitMQ listens. This uniform URL ensures that any messages the publisher emits end up in the exact broker (and queue) that the subscriber is monitoring.

## RabbitMQ browser
![RabbitMQ](RabbitMQ.png)

## Publisher Subscriber Consoles
![PublisherSubscriber](publishersubscriber.png)
The publisher succesfully sent five messages to RabbitMQ, and the subscriber successfully received and printed the five messages. 