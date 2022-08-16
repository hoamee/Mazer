# Working with ElasticSearch in MTI Project
## Configuration
### NPM Package
```
@elastic/elasticsearch
```
### import elasticsearch
```
import { Client as EkClient } from "@elastic/elasticsearch";
```
### setup configuration for elasticsearch
```
const searchConfiguration = {
  node: 'http://localhost:9200', //ElasticSearch url
  proxy: null,
  auth: {
    username: null, //username if already set
    password: null, //password if already set
    apiKey: null, //...
  },
  maxRetries: 3,
  requestTimeout: 30000
};
```
### Initialize EL client.  
*__Client is the main object to working with ElasticSearch__*
```
const ekClient = new EkClient(searchConfiguration)
```
## Usage
### "INSERT" & "UPDATE" Object
```
await ekClient.index({
    index: 'game-of-thrones',
    id: 1,
    document: {
      character: 'Ned Starks',
      quote: 'Winter is coming.'
    }
  })
```
*For update case, index and id must be specified.*
### "SELECT" - Search for object

```
const result = await els.search({
    index: 'game-of-thrones'
  });

console.log(result.hits.hits);
```
*"result" object has an attribute "hits.hits"*  
*"hits.hits" is a collection of object that we are looking for.*  
The output of **console.log(result)** should be:  
```
{
  took: 4,
  timed_out: false,
  _shards: { total: 1, successful: 1, skipped: 0, failed: 0 },
  hits: { //this is the parent hits
    total: { value: 3, relation: 'eq' },
    max_score: 1,
    hits: [ [Object], [Object], [Object] ] //this is the children hits, that contain objects
  }
}
```
