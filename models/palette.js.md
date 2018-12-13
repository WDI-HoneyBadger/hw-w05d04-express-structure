# Palette Model
Models the middleware function that are used to connect to database.

#### Required Modules 
Required database configuration 
```js
var connection = require('../db/dbconfig');
var varName = {};
```

## Middleware
All the middleware methods has same structure:
```js
varName.getAll = function(req, res, next){
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

#### `getAllPalette()` - gets all the colors for a given palette 
- **pg-promise method:** `db.manyOrNone`
- **SQL Query:**
```sql 
SELECT * FROM palettes;
```
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** `db.one`
- **SQL Query:** 
```sql 
SELECT * FROM colors WHERE palette_id=$1 AND color_id=$2;
```
- **Locals key:**  `res.locals.colors`
#### `create()` - adds a color to our database
- **pg-promise method:** `db.one`
- **SQL Query:** 
```sql 
INSERT INTO colors WHERE palette_id=$1 (elem1, elem2) VALUES ($1, $2, $3) RETURNING id;
```
- **Locals key:** `res.locals.color_id`
#### `update()` - edits a specific color
- **pg-promise method:** `db.one`
- **SQL Query:** 
```sql 
UPDATE colors SET elem1=$1, elem2=$2 WHER id=$4;
```
- **Locals key:** `res.locals.color_id`
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
DELETE FROM color WHERE id=$1;
```
- **Locals key:**  `No need`

## Exports
We export the object we have defined in the beginning
```sql
module.exports = varName
```
