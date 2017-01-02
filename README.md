﻿# Elasticsearch Beginner Tutorial

## About Elastic
Elasticsearch is a near real time search platform. What this means is there is a slight latency (normally one second) from the time you index a document 
until the time it becomes searchable.

## Cluster
A cluster is a collection of one or more nodes (servers) that together holds your entire data and provides federated indexing and search capabilities across all nodes. 
A cluster is identified by a unique name which by default is "elasticsearch". This name is important because a node can only be part of a cluster if the node is set up 
to join the cluster by its name.
