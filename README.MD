# How to Create a multi-node GrayLog.

Steps:
* Install needed component
* Setup MongoDB
* Setup Cluster ElasticSearch
* Setup GrayLog Server for multi-node
* Done!!!

## Install needed component

Please followed [graylog official](https://www.graylog.org/) and [Documentation](http://docs.graylog.org/) for details.

## Setup MongoDB

* Create replica set (Must)

First setup the mongo config for enviorment.

```linux
# change in all nodes.
# Located in "/etc/mongod.conf"

net:
  port: 27018
  bindIp: 0.0.0.0

```


* Create DB (Must)

* Create user(optical)

```bash
$ mongo admin -u admin -p admin --eval "db.getSiblingDB('dummydb').addUser('dummyuser', 'dummysecret')"
```

## Setup Cluster ElasticSearch

## Setup GrayLog Server for multi-node

DONE!

