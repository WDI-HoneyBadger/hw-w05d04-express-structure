USE THE COLOR MODEL AS REFERENCE

# Color Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
var db = require('../db/dbconfig');
var task = {};


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
SELECT * FROM palette WHERE color_id=$1;
```
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** 
- **SQL Query:**
```SELECT * FROM palette WHERE color_id=$2;
```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql INSERT INTO color(subject, content) VALUES($1, $2) RETURNING id;", [req.body.subject, req.body.content
```
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql UPDATE color SET subject = $1, content = $2
   WHERE id = $3 RETURNING id;`, [req.body.subject, req.body.content, req.params.id])
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql DELETE FROM color WHERE id=$1;", [req.params.id]
```
- **Locals key:**  

## Exports
PUT WHAT YOU EXPORT HERE
module.exports = paletts;