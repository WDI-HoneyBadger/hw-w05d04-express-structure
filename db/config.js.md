# Database Config
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();
## Required Modules
var config = {
  host: 'localhost',
  port: 5432,
  database: 'data_db',
  user: 'hnanalshmry'
}
## Config
var connection = pgInstance(config);

## Exports
module.exports = connection;