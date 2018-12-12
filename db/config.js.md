# Database Config

## Required Modules
```js
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();
````
## Config
```js
var config = {
  host: 'localhost',
  port: 5432,
  database: 'data_db',
  user: 'aishahalmaghrbi' 
}

var connection = pgInstance(config);
```
## Exports
```js
module.exports = connection;
```






