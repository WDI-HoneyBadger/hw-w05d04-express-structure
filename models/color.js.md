# Color Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
var db = require('../db/dbconfig')
var colors = {};
## Middleware
Each middleware method is added to our model. the basic structure is as follows:

```js
colors.getAll = function(req, res, next){
  db.manyOrNone(`SELECT * FROM colors WHERE palette_id= $1;`)
    .then(function(result){
      res.locals.colors = result;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}
colors.find = function (req, res, next) {
    var id = req.params.id;
    db.oneOrNone("SELECT * FROM colors WHERE id = $1 AND palette_id = $2;"), [req.params.id])
      .then(function(result){
        res.locals.colors = result;
        next();
      })
      .catch(function(error){
        console.log(error);
        next();
      })
  }

  colors.create = function(req, res, next) {
  db.one("INSERT INTO colors(name, bgcolor, pallette_id ) VALUES($1, $2, $4) RETURNING id;", [req.body.name, req.body.bgcolor, req.params.pallette_id])
    .then(function(result){
      res.locals.colors_id = result.id;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}


colors.update = function(req, res, next) {
  db.one(`UPDATE colors SET name = $1, bgcolor = $2
   pallette_id = $3 WHERE id = $4 RETURNING id;`, [req.body.name, req.body.bgcolor, req.params.pallette_id, req.params.id])
   .then(function(result){
     res.locals.colorsId = result.id;
     next();
   })
   .catch(function(error){

    next();
  })
}
colors.delete = function(req, res, next) {
  db.none("DELETE FROM colors WHERE id=$1;", [req.params.id])
    .then(function(){
      next();
    })
    .catch(function(error){
 
      next();
    })
}
colors.findByPalette = function(req, res, next) {
  db.manyOrNone("SELECT * FROM colors WHERE palette_id=$1;", [req.params.id])
    .then(function(result){
res.locals.colors = result;
      next();
    })
    .catch(function(error){

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
```
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
SELECT * FROM colors WHERE id = $1 AND palette_id= $2;
```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql 
INSERT INTO colors(name, bgcolor, pallette_id ) VALUES($1, $2, $4) RETURNING id;
```
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
UPDATE colors SET name = $1, bgcolor = $2
   WHERE id = $3 AND pallette_id = $4 RETURNING id;
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
DELETE FROM colors WHERE id=$1;
```
- **Locals key:**  

## Exports
module.exports = colors;