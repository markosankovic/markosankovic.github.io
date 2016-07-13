---
layout: post
title:  "MongoDB dump from remote server and restore"
date:   2016-07-13
comments: true
tags: nosql mongodb dump remote restore server
---

    mongodump --host ds015192.mlab.com -d mydb --port 15194 --username foo --password bar --out mongodump-mydb
    mongorestore --host 127.0.0.1 --port 27017 mongodump-mydb
