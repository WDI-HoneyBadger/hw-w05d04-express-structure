USE THE COLOR MODEL AS REFERENCE

# Palette Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
var db = require('../db/dbconfig')
var palette = {};
## Middleware
Each middleware method is added to our model. the basic structure is as follows:

```js
palette.getAll = function(req, res, next){
  db.manyOrNone(`SELECT * FROM pallette ;`)
    .then(function(result){
      res.locals.palette = result;
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
        res.locals.palette = result;
        next();
      })
      .catch(function(error){
        console.log(error);
        next();
      })
  }

  palette.create = function(req, res, next) {
  db.one("INSERT INTO colors(name, bgcolor, pallette_id ) VALUES($1, $2, $4) RETURNING id;", [req.body.name, req.body.bgcolor, req.params.pallette_id])
    .then(function(result){
      res.locals.palette_id = result.id;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}


palette.update = function(req, res, next) {
  db.one(`UPDATE colors SET name = $1, bgcolor = $2
   WHERE id = $3 AND pallette_id = $4 RETURNING id;`, [req.body.name, req.body.bgcolor, req.params.id, req.params.pallette_id])
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
colors.delete = function(req, res, next) {
  db.none("DELETE FROM palette WHERE id=$1;", [req.params.id])
    .then(function(){
      console.log('DELETE');
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

#### `getAllByColor()` - gets all the colors for a given palette 
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
```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
- **Locals key:**  

## Exports
EXPORT PALETTE