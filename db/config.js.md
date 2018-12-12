# Database Config

## Required Modules

## Config

## Exports


var pgPromise = require('pg-promise');
var pgInstance = pgPromise();

var config = {
  host: 'localhost',
  port: 5432,
  database: 'database name',
  user: 'ak'
}

var connection = pgInstance(config);

module.exports = connection;
