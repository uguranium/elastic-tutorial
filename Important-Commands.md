# Important Commands

## List All Indices
> GET /_cat/indices?v

## Create an Index
> PUT /customer?pretty

**Note: Use the Postman for sending methods** 

## Put the values

Use the put method (**PUT**) and send the values via Json

Let�s index a simple customer document into the customer index, "external" type, with an ID of 1 as follows:

> PUT /customer/external/1?pretty

*query body*:

```
{
  "name": "John Doe"
}
```

response:
```
{
  "_index": "customer",
  "_type": "external",
  "_id": "1",
  "_version": 1,
  "result": "created",
  "_shards": {
    "total": 2,
    "successful": 1,
    "failed": 0
  },
  "created": true
}
```

Note: It is important to note that Elasticsearch does not require you to explicitly create an index first before you can index documents into it.
In the previous example, Elasticsearch will automatically create the customer index if it didn�t already exist beforehand.


**Retrieve that document that we just indexed**

> GET /customer/external/1?pretty

Response:

```
{
  "_index": "customer",
  "_type": "external",
  "_id": "1",
  "_version": 2,
  "found": true,
  "_source": {
    "name": "John Doe"
  }
}
```

## Delete an Index
Let�s delete the index
> DELETE /customer?pretty

Then list all the indexes
> GET /_cat/indices?v

Look again at some of the API commands
```
PUT /customer
PUT /customer/external/1
{
  "name": "John Doe"
}
GET /customer/external/1
DELETE /customer
```

## How Access Data In Elasticsearch
>  [REST Verb] Url:port  / Index / Type / ID 

## Modifing Data
We�ve previously seen how we can index a single document. 

> PUT /customer/external/1?pretty
```
{
  "name": "John Doe"
}
```

Again, the above will index the specified document into the customer index, external type, with the ID of 1. If we then executed the above command again 
with a different (or same) document, Elasticsearch will replace (i.e. reindex) a new document on top of the existing one with the ID of 1
> PUT /customer/external/1
```
{
  "name": "Jane Doe"
}
```

When indexing, the ID part is optional. If not specified, Elasticsearch will generate a random ID. **Use POST method**
> POST /customer/external
```
{
  "name": "Ugur CELIK"
}
```

Response:
```
{
  "_index": "customer",
  "_type": "external",
  "_id": "AVljjEw2RkLM0AX4vb3n",
  "_version": 1,
  "result": "created",
  "_shards": {
    "total": 2,
    "successful": 1,
    "failed": 0
  },
  "created": true
}
```





