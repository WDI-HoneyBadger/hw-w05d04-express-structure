# Color Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
```js
var db = require('../db/config');
var color = {};
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
SELECT  colors.name , palettes.name FROM colors, palettes WHERE palette_id=$1 AND colors.id=$2 colors.id=palettes.id;
```
- **Locals key:**  `res.locals.colors`
#### `create()` - adds a color to our database
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
`INSERT INTO colors (palette_id,name) VALUES ($1,$2) RETURNING id;`
```
- **Locals key:**  `res.locals.color_id`
#### `update()` - edits a specific color
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
`UPDATE colors SET name = $1  WHERE id = $2 RETURNING id;`
```
- **Locals key:** `res.locals.color_id`
#### `delete()` - deletes a specific color
- **pg-promise method:** `db.none`
- **SQL Query:**
```sql
`DELETE FROM colors WHERE id=$1 ` 
```
- **Locals key:**  

## Exports
```js
module.exports = color;
```