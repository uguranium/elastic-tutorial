# Elasticsearch Beginner Tutorial

## About Elastic
Elasticsearch is a near real time search platform. What this means is there is a slight latency (normally one second) from the time you index a document 
until the time it becomes searchable.

## Cluster
A cluster is a collection of one or more nodes (servers) that together holds your entire data and provides federated indexing and search capabilities across all nodes. 
A cluster is identified by a unique name which by default is "elasticsearch". This name is important because a node can only be part of a cluster if the node is set up 
to join the cluster by its name. (Like Mysql Master Host)

## Node
A node is a single server that is part of your cluster, stores your data, and participates in the cluster’s indexing and search capabilities. 
Just like a cluster, a node is identified by a name which by default is a random Universally Unique IDentifier (UUID) that is assigned to the node at startup. 
You can define any node name you want if you do not want the default. This name is important for administration purposes where you want to identify which servers 
in your network correspond to which nodes in your Elasticsearch cluster.  (Like Mysql Database)

## Index
An index is a collection of documents that have somewhat similar characteristics. For example, you can have an index for customer data, another index for a product catalog, 
and yet another index for order data. An index is identified by a name (that must be all lowercase) and this name is used to refer to the index when 
performing indexing, search, update, and delete operations against the documents in it.

## Type
Within an index, you can define one or more types. A type is a logical category/partition of your index whose semantics is completely up to you. In general, a type is defined 
for documents that have a set of common fields. For example, let’s assume you run a blogging platform and store all your data in a single index. In this index, you may define 
a type for user data, another type for blog data, and yet another type for comments data.

## Document
A document is a basic unit of information that can be indexed. For example, you can have a document for a single customer, another document for a single product, 
and yet another for a single order. This document is expressed in JSON (JavaScript Object Notation) which is an ubiquitous internet data interchange format.

