# Database Config
## Required Modules
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();

## Config
var config = {
  host: 'localhost',
  port: 5432,
  database: 'db_color',
  user: 'maymo7a'
}
var connection = pgInstance(config);

## Exports
module.exports = connection;