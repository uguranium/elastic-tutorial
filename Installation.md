# Installation
## Java
Elasticsearch requires at least Java 8. Specifically as of this writing, it is recommended that you use the Oracle JDK version 1.8.0_73.

## Download the Elasticsearch
Download the Elasticsearch 5.1.1 tar as follows (Windows users should download the zip package)

## Cluster Health
Let’s start with a basic health check, which we can use to see how our cluster is doing. We’ll be using curl to do this but you can use any tool that allows you to make HTTP/REST calls. 

> GET /_cat/health?v
> GET /_cat/nodes?v
