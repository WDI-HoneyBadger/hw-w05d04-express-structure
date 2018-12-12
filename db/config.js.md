# Database Config

## Required Modules

- **Declear one package to interactive with our database**  
```
var pgPromise = require('The right path');
var pgInstance = pgPromise();
```
## Config

- **Config our database** 
```
var config = {
  host: 'localhost',
  port: 5432,
  database: 'databaseName',
  user: 'userName',
  password: *****
}

var connection = pgInstance(config);
```
## Exports
- `module.exports = connection;`