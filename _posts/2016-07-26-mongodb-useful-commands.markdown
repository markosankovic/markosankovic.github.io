---
layout: post
title:  "MongoDB Useful Commands"
date:   2016-07-26
comments: true
tags: nosql mongodb dump remote restore server docker container
---

Dump and Restore
----------------

### Dump from a remote server:

    $ mongodump \
      --host ds015192.mlab.com \
      -d mydb \
      --port 15194 \
      --username foo \
      --password bar \
      --out mongodump-mydb

### Dump from a running MongoDB Docker container:

    $ docker run \
      --rm \
      --link mongodb:mongo \
      -v /root/mongodb-backup:/backup \
      mongo \
      bash -c 'mongodump --out /backup --host $MONGO_PORT_27017_TCP_ADDR'

In the --link option mongodb is the name of the running MongoDB Docker container.

### Restore to a running MongoDB Docker container:

    $ docker run \
      --rm
      --link mongodb:mongo \
      -v /root/mongodb-backup:/backup \
      mongo \
      bash -c 'mongorestore /backup --host $MONGO_PORT_27017_TCP_ADDR'

Manipulate Database
-------------------

### Drop database from a local MongoDB server:

    $ mongo <dbname> --eval "db.dropDatabase()"

### Drop database from a running MongoDB Docker container:

    $ docker run \
      --rm
      --link mongodb:mongo \
      mongo \
      bash -c 'mongo <dbname> --host $MONGO_PORT_27017_TCP_ADDR --eval "db.dropDatabase()"'
