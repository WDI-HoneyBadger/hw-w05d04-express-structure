# Database Config
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();


## Required Modules
var config = {
  host: 'localhost',
  port: 5432,
  database: 'palette', // database name 
  user: 'layalkashgari' // my username here
}

## Config
var connection = pgInstance(config);

## Exports
module.exports = connection;