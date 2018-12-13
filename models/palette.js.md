USE THE COLOR MODEL AS REFERENCE
# Color Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
var db = require('../db/dbconfig');
var model = {};

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

#### `getAll()` - gets all the palettes.
- **pg-promise method:** `db.manyOrNone`
- **SQL Query:**
```sql 
SELECT * FROM palette;
```
- **Locals key:** `res.locals.palettes`
#### `find()` - gets a specific palette
- **pg-promise method:** `db.oneOrNone`
- **SQL Query:**
```sql 
SELECT * FROM palette WHERE id=$1;
```
- **Locals key:** `res.locals.palette`
#### `create()` - adds a palette to our database
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
INSERT INTO palette(name, description) VALUES($1, $2) RETURNING id;
```
- **Locals key:** `res.locals.palette_id`
#### `update()` - edits a specific palette
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
UPDATE palette SET name=$1, description=$2 WHERE id=$3 RETURNING id;
```
- **Locals key:** 
#### `delete()` - deletes a specific palette
- **pg-promise method:** 
- **SQL Query:** `db.none`
```sql 
DELET FROM palette WHERE id=$1;
```
- **Locals key:**  

## Exports
module.exports = model;