---
layout: post
title:  "docker api certs"
date:   2022-08-31 10:58:00 +0200
categories: certs docker
---

```
openssl genrsa -aes256 -out ca-key.pem 4096
openssl req -new -x509 -days 1000 -key ca-key.pem -sha256 -out ca.pem

openssl genrsa -out server-key.pem 4096
openssl req -subj "/CN=d-jenk-dr-dev" -sha256 -new -key server-key.pem -out server.csr
openssl x509 -req -days 1000 -sha256 -in server.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out server-cert.pem -extfile extfile.cnf

openssl genrsa -out key.pem 4096
openssl req -subj '/CN=d-jenk-dev.jrc.it' -new -key key.pem -out client.csr
openssl x509 -req -days 1000 -sha256 -in client.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out cert.pem -extfile extfile-client.cnf
```