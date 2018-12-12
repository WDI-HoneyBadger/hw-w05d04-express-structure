
USE THE COLOR MODEL AS REFERENCE
var db = require('../db/dbconfig');
var palette = {};
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


#### `getAllByPalette()` - gets all the pallete for a given palette 
- **pg-promise method:** `db.manyOrNone`
- **SQL Query:**
```sql 
SELECT * FROM pallete WHERE palette_id=$1;
```
- **Locals key:** `res.locals.pallete`
#### `find()` - gets a specific color
- **pg-promise method:** `db.one`
- **SQL Query:** `SELECT * FROM pallete WHERE color='red'`
```sql 
```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** `db.one`
- **SQL Query:** `INSERT INTO todo(color) VALUES($1) RETURNING id;
```sql 
```
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** `db.one`
- **SQL Query:** (`UPDATE pallete SET color = $1
   WHERE id = $2 RETURNING id;`, [req.body.color, req.params.id])
```sql 
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** `b.none`
- **SQL Query:** ("DELETE FROM pallete WHERE id=$1;", [req.params.id])
```sql 
```
module.exports = palette;