# Color Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE

var db = require('../db/dbconfig');
## Middleware
Each middleware method is added to our model. the basic structure is as follows:

var color={};

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

color.find = function (req, res, next) {
    var id = req.params.id;
    db.oneOrNone("SELECT * FROM table_name WHERE id = $1;", [id])
      .then(function(result){
        res.locals.color = result;
        next();
      })
      .catch(function(error){
        console.log(error);
        next();
      })
    }
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** `db.one()`
- **SQL Query:** `SELECT * FROM colors WHERE color='red'`
```sql 
```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** `db.one()`
- **SQL Query:** ("INSERT INTO palette(subject, content) VALUES($1, $2) RETURNING id;", [req.body.subject, req.body.content])


color.create = function(req, res, next) {
  db.one("INSERT INTO palette(subject, content) VALUES($1, $2) RETURNING id;", [req.body.subject, req.body.content])
    .then(function(result){
      res.locals.todo_id = result.id;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** `db.one()`
- **SQL Query:** (`UPDATE colors SET color = $1
   WHERE id = $2 RETURNING id;`, [req.body.color, req.params.id])
```sql 
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** `db.one()`
- **SQL Query:** ("DELETE FROM colors WHERE id=$1;", [req.params.id])
```sql 
```
- **Locals key:**  

## Exports
PUT WHAT YOU EXPORT HERE

module.export = color;