USE THE COLOR MODEL AS REFERENCE# Color Model

var db = require('../db/dbconfig');

var cp = {};

## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE

## Middleware
Each middleware method is added to our model. the basic structure is as follows:

```js
model.getAll = function(req, res, next){
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

### Middleware for this model:

FILL OUT THE REST OF THE MIDDLEWARE

#### `getAllByPalette()` - gets all the colors for a given palette 
- **pg-promise method:** `db.manyOrNone`
- **SQL Query:**
```sql 
SELECT * FROM colors WHERE palette_id=$1;

cp.getAll = function (req, res, next) {
  db.manyOrNone("SELECT * FROM colors WHERE palette_id=$1;") 
    .then(function (result) {   
      res.locals.cp = result;  
      next();  
    })
    .catch(function(error){ 
      console.log(error); 
      next(); 
    })



```
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 


todo.find = function (req, res, next) {
  var id = req.params.id;
  db.oneOrNone("SELECT * FROM cp WHERE id = $1;", [id])
    .then(function(result){
      res.locals.palettes = result;
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
cp.create = function(req, res, next) {
  db.one("INSERT INTO cp(first, last) VALUES($1, $2) RETURNING id;", [req.body.first, req.body.last])
    .then(function(result){
      res.locals.cp_id = result.id;
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
cp.update = function(req, res, next) {
  db.one(`UPDATE cp SET first = $1, last = $2
   WHERE id = $3 RETURNING id;`, [req.body.first, req.body.last, req.params.id])
   .then(function(result){
     console.log(`table updated for ${result.id}`);
     res.locals.cp_id = result.id;
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
cp.delete = function(req, res, next) {
  db.none("DELETE FROM cp WHERE id=$1;", [req.params.id])
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
module.exports = cp;