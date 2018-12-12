# Color Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
var express = require('express');
var router = express.Router();

var palette = require('../models/palette');
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
- **pg-promise method:** `db.one`
- **SQL Query:** `SELECT * FROM colors WHERE color='someColor'`
```sql 
```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** `db.ond`
- **SQL Query:** `INSERT INTO todo(color) VALUES($1) RETURNING id;
```sql 
```
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** db.one
- **SQL Query:** (`UPDATE colors SET color = $1
   WHERE id = $2 RETURNING id;`, [req.body.color, req.params.id])
```sql 
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** db.none
- **SQL Query:** ("DELETE FROM colors WHERE id=$1;", [req.params.id])
```sql 
```
- **Locals key:**  

## Exports
PUT WHAT YOU EXPORT HERE

exports = router;