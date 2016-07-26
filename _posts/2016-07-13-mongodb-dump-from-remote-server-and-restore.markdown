---
layout: post
title:  "MongoDB dump and restore from remote server and Docker container"
date:   2016-07-26
comments: true
tags: nosql mongodb dump remote restore server docker container
---

Dump from a remote server:
--------------------------

    $ mongodump \
      --host ds015192.mlab.com \
      -d mydb \
      --port 15194 \
      --username foo \
      --password bar \
      --out mongodump-mydb

Dump from a running MongoDB Docker container:
---------------------------------------------

    $ docker run \
      --rm \
      --link running-mongodb-container-name:mongo \
      -v /root:/backup \
      mongo \
      bash -c 'mongodump --out /backup --host $MONGO_PORT_27017_TCP_ADDR'

Restore to a running MongoDB Docker container: 
----------------------------------------------

    $ docker run \
      --rm
      --link running-mongodb-container-name:mongo \
      -v /root:/backup \
      mongo \
      bash -c 'mongorestore /backup --host $MONGO_PORT_27017_TCP_ADDR'
