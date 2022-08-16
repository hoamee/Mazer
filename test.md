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
*Client is the main object to working with ElasticSearch *
```
const ekClient = new EkClient(searchConfiguration)
```
