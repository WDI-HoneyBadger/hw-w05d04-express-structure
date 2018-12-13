# Database Config

## Required Modules
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();

## Config

var config = {
  host: 'localhost',
  port: 5432,
  database: 'todo_db',
  user: 'ranimdahli'
}

var connection = pgInstance(config);
## Exports

module.exports = connection;