USE THE COLOR MODEL AS REFERENCE
# palette Model
Models contain middleware functions that are used to talk to our database. 
var db = require('../db/config');
## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
var palette = {};
## Middleware
Each middleware method is added to our model. the basic structure is as follows:

```js
palette.getAll = function(req, res, next){
  db.manyOrNone(`SELECT * FROM data;`)
    .then(function(result){
      res.locals.color = result;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}
```

### Middleware for this model:

FILL OUT THE REST OF THE MIDDLEWARE

#### `getAllByPalette()` - gets all the colors for a given palette 
- **pg-promise method:** `db.manyOrNone`
- **SQL Query:**
```sql 

```
- **Locals key:** `res.locals.palette`
#### `find()` - gets a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 

palette.find = function(req, res, next) {
  db.oneOrNone("SELECT * FROM data WHERE id = $1;", [req.params.id])
    .then(function(result){
      console.log('$$$$$$$$$', result);
      res.locals.palette = result;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}

```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql 
palette.create = function(req, res, next) {
  db.one("INSERT INTO data(name, color) VALUES($1, $2) RETURNING id;", [req.body.name, req.body.color])
    .then(function(result){
      res.locals.data_id = result.id;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}
```

- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
palette.update = function(req, res, next) {
  db.one(`UPDATE data SET name = $1, color = $2
   WHERE id = $3 RETURNING id;`, [req.body.name, req.body.color, req.params.id])
   .then(function(result){
     console.log(`table updated for ${result.id}`);
     res.locals.palette_id = result.id;
     next();
   })
   .catch(function(error){
    console.log(error);
    next();
  })
}
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
palette.delete = function(req, res, next) {
  db.none("DELETE FROM data WHERE id=$1;", [req.params.id])
    .then(function(){
      console.log('SUCCESSFUL DELETE');
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}
```
- **Locals key:**  

## Exports
PUT WHAT YOU EXPORT HERE
module.exports = palette;