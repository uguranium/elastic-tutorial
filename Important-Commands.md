# Important Commands

## List All Indices
> GET /_cat/indices?v

## Create an Index
> PUT /customer?pretty

**Note: Use the Postman for sending methods** 

## Put the values

Use the put method (**PUT**) and send the values via Json

Let’s index a simple customer document into the customer index, "external" type, with an ID of 1 as follows:

> PUT /customer/external/1?pretty

query body:

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

