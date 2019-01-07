# Database Config
``` js
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();
```
## Required Modules

## Config
``` js
var config = {
  host: 'localhost',
  port: 5432,
  database: 'express_structure',
  user: 'trevorpreston'
}
```
## Exports
``` js
var connection = pgInstance(config);
module.exports = connection;
```