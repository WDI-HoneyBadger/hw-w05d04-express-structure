# Database Config
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();


## Required Modules
ar config = {
  host: 'localhost',
  port: 5432,
  database: 'confi_db',
  user: 'turkialomari' 
}


## Config
var connection = pgInstance(config);

## Exports
module.exports = connection;