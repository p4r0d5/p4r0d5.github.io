---
layout: post
title:  "rabbitmq connection test"
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

## tls support

source: [https://www.rabbitmq.com/ssl.html#automated-certificate-generation](https://www.rabbitmq.com/ssl.html#automated-certificate-generation)

```
import pika
import ssl 
import logging

logging.basicConfig(level=logging.INFO)

credentials = pika.PlainCredentials(
            username='user', password='password'
        )
host='hostname'
print('connecting to: ',host)

context = ssl.create_default_context(
    cafile="/opt/app-root/src/certs/ca.pem")
context.verify_mode = ssl.CERT_REQUIRED
context.load_cert_chain("/opt/app-root/src/certs/certificate.pem",
                        "/opt/app-root/src/certs/key.pem")

ssl_options = pika.SSLOptions(context, host)

connection = pika.BlockingConnection(
            pika.ConnectionParameters(
                host=host,
                credentials=credentials,
                ssl_options = ssl_options,
                port=5672
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

# rabbitmq conf file

```
kind: ConfigMap
apiVersion: v1
metadata:
  name: rabbit-config
  namespace:defautl
data:
  10-defaults.conf: |-
    loopback_users.guest = false
    log.console = true
  20-tls.conf: |-
    listeners.tcp = none
    listeners.ssl.default = 5672
    ssl_options.cacertfile = /etc/rabbitmq/certs/ca.pem
    ssl_options.certfile   = /etc/rabbitmq/certs/certificate.pem
    ssl_options.keyfile    = /etc/rabbitmq/certs/key.pem
    ssl_options.verify     = verify_peer
    ssl_options.fail_if_no_peer_cert = true
    ssl_options.password   = #password if set
```