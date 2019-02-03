# palette Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
```js
var db = require('../db/config');
var palette = {};
```
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

#### `getAllByPalette()` - gets all the palettes for a given palette 
- **pg-promise method:** `db.manyOrNone`
- **SQL Query:**
```sql 
SELECT * FROM palettes;
```
- **Locals key:** `res.locals.palette`
#### `find()` - gets a specific palette
- **pg-promise method:** `db.oneOrNone`
- **SQL Query:**
```sql 
SELECT * FROM palettes WHERE palette_id=$1 ;
```
- **Locals key:**  `res.locals.palettes`
#### `create()` - adds a palette to our database
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
`INSERT INTO palettes (name) VALUES ($1) RETURNING id;`
```
- **Locals key:**  `res.locals.palette_id`
#### `update()` - edits a specific palette
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
`UPDATE palettes SET name = $1  , explanation = $2 WHERE id = $3 RETURNING id;`
```
- **Locals key:** `res.locals.palette_id`
#### `delete()` - deletes a specific palette
- **pg-promise method:** `db.none`
- **SQL Query:**
```sql
`DELETE FROM palettes WHERE id=$1 ` 
```
- **Locals key:**  

## Exports
```js
module.exports = palette;
```