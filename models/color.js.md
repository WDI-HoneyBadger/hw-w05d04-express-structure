# Color Model
Models contain middleware functions that are used to talk to our database. 
var db = require('../db/config');




## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
var color = {};
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
```
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
color.find = function(req, res, next) {
  db.oneOrNone("SELECT * FROM colors WHERE palette_id=$1;", [req.params.id])
    .then(function(result){
      console.log('$$$$$$$$$', result);
      res.locals.colors = result;
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
colors.create = function(req, res, next) {
  db.one("INSERT INTO colors(subject, content) VALUES('yellow, 'blue') RETURNING id;", [req.body.subject, req.body.content])
    .then(function(result){
      res.locals.colors_id = result.id;
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
colors.update = function(req, res, next) {
  db.one(`UPDATE colors SET subject = 'yellow', content = 'blue'
   WHERE id = $3 RETURNING id;`, [req.body.subject, req.body.content, req.params.id])
   .then(function(result){
     console.log(`table updated for ${result.id}`);
     res.locals.colors_id = result.id;
     next();
   })
   .catch(function(error){
    console.log(error);
    next();
  })

```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
colors.delete = function(req, res, next) {
  db.none("DELETE FROM colors WHERE id=$1;", [req.params.id])
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
module.exports= color;
