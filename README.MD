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

```nano
# change in all nodes.
# Located in "/etc/mongod.conf"

net:
  port: 27018
  bindIp: 0.0.0.0
[…]
replication:
   replSetName: "rs01"
```

Then go to the master node you want. log into MongoDB.

Setup the replica claster using following command one by one.

```shell
mongo --port 27018
rs.initiate()
rs.add("<hostname>:27018") # add each node by changing <hostname>
rs.status()
```

That's it!

* Create DB (Must)


* Edit Services if needed

Than Change the service config if needed.

```
# Location : /usr/lib/systemd/system/mongod.service

Restart=on-failure
[…]
[Install]
WantedBy=multi-user.target
```

* Create user(optical)

```bash
$ mongo admin -u admin -p admin --eval "db.getSiblingDB('dummydb').addUser('dummyuser', 'dummysecret')"
```

## Setup Cluster ElasticSearch

## Setup GrayLog Server for multi-node

DONE!

