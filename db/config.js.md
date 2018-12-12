# Database Config

## Required Modules
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();
## Config
var config = {
  host: 'localhost',
  port: 5432,
  database: 'todo_db',
  user: 'yahyamo.'
}
## Exports
var connection = pgInstance(config);

module.exports = connection;