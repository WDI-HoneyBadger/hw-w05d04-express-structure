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

#### `getAllByPalette()` - gets all the colors for a given palette 
- **pg-promise method:** `db.manyOrNone`
- **SQL Query:**
```sql 
SELECT * FROM colors WHERE palette_id=$1;
```
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** `db.oneOrNone`
- **SQL Query:**
```sql 
SELECT * FROM colors WHERE id=$1;
```
- **Locals key:** `res.locals.color`
#### `create()` - adds a color to our database
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
INSERT INTO colors(name, description, palete_id) VALUES($1, $2, $3) RETURNING id;
```
- **Locals key:** `res.locals.color_id`
#### `update()` - edits a specific color
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
UPDATE colors SET name=$1, description=$2 WHERE id=$3 RETURNING id;
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:** `db.none`
```sql 
DELET FROM colors WHERE id=$1;
```
- **Locals key:**  

## Exports
module.exports = model;