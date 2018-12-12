# Database Config

var config = {
  host: 'localhost',
  port: 5432,
  database: 'palette_db',
  user: 'mac' // your username here!!
}

var connection = pgInstance(config);


## Required Modules
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();

## Config



## Exports

module.exports = connection;