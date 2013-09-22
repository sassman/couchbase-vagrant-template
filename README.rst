Vagrant based couchbase cluster
===============================

this small template allows you to launch easily a couchbase cluster, for experimenting around.

It launchs per default 4 nodes that act as a cluster. Each node has 1024MB ram configured.


How to Start
------------

to configure the couchbase cluster on the first node please go to 


::

    http://localhost:8001/

and configure the master node.
all other machines are readable by incrementing the portnumber.


References
----------

This code is mainly based on the ressource [1]

[1] http://blog.couchbase.com/couchbase-cluster-minutes-vagrant-and-puppet