# Database Config

## Required Modules
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();

## Config
var config = {
  host: 'localhost',
  port: 5432,
  database: 'data_db',
  user: 'Azooz' 
}

var connection = pgInstance(config);

## Exports
module.exports = connection;