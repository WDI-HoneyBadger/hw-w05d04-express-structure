# Database Config

## Required Modules

```js
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();
```
## Config

```js 
var config = {
  host: 'localhost',
  port: 5432,
  database: 'colorsPalettes_db',
  password: '123456',
  user: 'postgres';
}

var connection = pgInstance(config);
```


## Exports

```js
module.exports = connection;
```