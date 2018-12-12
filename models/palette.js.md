USE THE COLOR MODEL AS REFERENCE
# Palette Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE

## Middleware
Each middleware method is added to our model. the basic structure is as follows:
```
var db = require('the right path');
var palette = {};
```
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

#### `getAll()` - gets all the palettes 
- **pg-promise method:** `db.manyOrNone`
- **SQL Query:**
```sql 
SELECT * FROM palettes WHERE id=$1;
```
- **Locals key:** `res.locals.palettes`
#### `find()` - gets a specific palette
- **pg-promise method:** `db.oneOrNone`
- **SQL Query:**
```sql 
SELECT * FROM palettes WHERE id=$1
```
- **Locals key:**  `res.locals.palette`
#### `create()` - adds a palette to our database
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
INSERT INTO palettes VALUE($1, $2, $3) RETURNING id;
```
- **Locals key:** `res.locals.palette_id` 
#### `update()` - edits a specific palette
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
UPDATE palettes
SET column1 = $1, column2 = $2, column3 = $3 WHERE id =$4;
```
- **Locals key:** `res.locals.palette_id`
#### `delete()` - deletes a specific palette
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
DELETE FROM palettes WHERE id=$1;
```
- **Locals key:**  `res.locals.palette_id`

## Exports
PUT WHAT YOU EXPORT HERE
`module.exports = palettes;