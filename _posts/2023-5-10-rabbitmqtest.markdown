---
layout: post
title:  "rabbitmq test connection"
date:   2023-05-10 16:08:34 +0200
categories: linux rabbitmq
---
# push a message

``` python
#!/usr/bin/env python
import pika
credentials = pika.PlainCredentials(
            username='user', password='password'
        )
host='hostname'
print('connecting to: ',host)
connection = pika.BlockingConnection(
            pika.ConnectionParameters(
                host=host,
                credentials=credentials
            )
        )
channel = connection.channel()
channel.queue_declare(queue='hello')
channel.basic_publish(exchange='',
                      routing_key='hello',
                      body='Hello World!')
print(" [x] Sent 'Hello World!'")
connection.close()
```
# push message and read the queue

``` python
#!/usr/bin/env python
import pika
credentials = pika.PlainCredentials(
            username='user', password='password'
        )
#connection = pika.BlockingConnection(pika.ConnectionParameters('172.23.1.213'))
host='hostname'
print('connecting to: ',host)
connection = pika.BlockingConnection(
            pika.ConnectionParameters(
                host=host,
                credentials=credentials
            )
        )
channel = connection.channel()
channel.queue_declare(queue='hello')
channel.basic_publish(exchange='',
                      routing_key='hello',
                      body='Hello World 2 !')
print(" [x] Sent 'Hello World!'")

for method_frame, properties, body in channel.consume('hello'):

    # Display the message parts
    print(method_frame)
    print(properties)
    print(body)

connection.close()
```