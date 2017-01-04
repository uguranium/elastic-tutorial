# Search Api

Before the using search api we must be add some data. For example 
>PUT localhost:9200/bank/account/1
```
{
    "account_number": 0,
    "balance": 16623,
    "firstname": "Bradshaw",
    "lastname": "Mckenzie",
    "age": 29,
    "gender": "F",
    "address": "244 Columbus Place",
    "employer": "Euron",
    "email": "bradshawmckenzie@euron.com",
    "city": "Hobucken",
    "state": "CO"
}
```
Put this information.

## Using Search Api

Example search query
> GET /bank/_search?q=*&sort=account_number:asc&pretty

Response:

```
{
  "took": 5,
  "timed_out": false,
  "_shards": {
    "total": 5,
    "successful": 5,
    "failed": 0
  },
  "hits": {
    "total": 1,
    "max_score": null,
    "hits": [
      {
        "_index": "bank",
        "_type": "account",
        "_id": "1",
        "_score": null,
        "_source": {
          "account_number": 0,
          "balance": 16623,
          "firstname": "Bradshaw",
          "lastname": "Mckenzie",
          "age": 29,
          "gender": "F",
          "address": "244 Columbus Place",
          "employer": "Euron",
          "email": "bradshawmckenzie@euron.com",
          "city": "Hobucken",
          "state": "CO"
        },
        "sort": [
          0
        ]
      }
    ]
  }
}
```

**took** – time in milliseconds for Elasticsearch to execute the search
**timed_out ** – tells us if the search timed out or not
**_shards** – tells us how many shards were searched, as well as a count of the successful/failed searched shards
**hits** – search results
**hits.total** – total number of documents matching our search criteria
**hits.hits** – actual array of search results (defaults to first 10 documents)
**sort** – sort key for results (missing if sorting by score)

## Query 
Dissecting the above, the query part tells us what our query definition is and the match_all part is simply the type of query 
that we want to run. The match_all query is simply a search for all documents in the specified index.
> POST /bank/_search
```
{
  "query": { "match_all": {} }
}
```


Here we pass in size
> POST /bank/_search
```
{
  "query": { "match_all": {} },
  "size": 1
}
```


This example does a match_all and returns documents 11 through 20:
> POST /bank/_search
```
{
  "query": { "match_all": {} },
  "from": 10,
  "size": 10
}
```

This example does a match_all and sorts the results by account balance in descending order and returns the top 10 (default size) documents.
> POST /bank/_search
```
{
  "query": { "match_all": {} },
  "sort": { "balance": { "order": "desc" } }
}
```
**Note that if size is not specified, it defaults to 10.**

## Executing Searches
If we use
> POST bank/_search
```
{
  "query" : { "match_all": {} }
}
```
Response source is like this:
```
"_source": {
          "account_number": 0,
          "balance": 16623,
          "firstname": "Bradshaw",
          "lastname": "Mckenzie",
          "age": 29,
          "gender": "F",
          "address": "244 Columbus Place",
          "employer": "Euron",
          "email": "bradshawmckenzie@euron.com",
          "city": "Hobucken",
          "state": "CO"
}
```

If we need just account_number and balance we can make query like this:
> POST /bank/search
```
{
	"query": { "match_all": {} }
	"_source": ["account_number","balance"]
}
```
source will be like this:
```
"_source": {
          "account_number": 0,
          "balance": 16623
        }
```
Its like sql query Select XXX from ...


This example returns the account numbered 20:
> POST /bank/_search
```
{
  "query": { "match": { "account_number": 20 } }
}
```

## Search Examples

This example returns all accounts containing the term "mill" in the address:
> POST /bank/_search
```
{
  "query": { "match": { "address": "mill" } }
}
```


This example returns all accounts containing the term "mill" or "lane" in the address:
> POST /bank/_search
```
{
  "query": { "match": { "address": "mill lane" } }
}
```


This example is a variant of match (match_phrase) that returns all accounts containing the phrase "mill lane" in the address:
> POST /bank/_search
```
{
	"query": { "match_phrase": { "address": "mill lane" } }
}
```



This example composes two match queries and returns all accounts containing "mill" and "lane" in the address:
> POST /bank/_search
```
{
  "query": {
    "bool": {
      "must": [
        { "match": { "address": "mill" } },
        { "match": { "address": "lane" } }
      ]
    }
  }
}
```

