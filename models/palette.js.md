USE THE COLOR MODEL AS REFERENCE
```js
var connection = require('../db/dbconfig');
var varName = {};
```


```js
varName.getAll = function(req, res, next){
  db.manyOrNone(`SELECT * FROM table;`)
    .then(function(result){
      res.locals.key = result;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}
```