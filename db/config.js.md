# Database Config
var pgPromise = require('pg-promise');
var pgInstance = pgPromise();
## Required Modules
var config = {
  host: 'localhost',
  port: 5432,
  database: 'color_list',
  user: 'Reema' 
}

## Config
var myApp = pgInstance(config);

## Exports

module.exports = myApp;