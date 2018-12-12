# Color Model
Models contain middleware functions that are used to talk to our database. 


-	set up my model to communicate with controller 
 

 
## Required Modules 

var db = require('../db/dbconfig');
var color = {}; // dont understand this line 


## Middleware
Each middlew are method is added to our model. the basic structure is as follows:
2
```js
model.getAll = function(req, res, next){
  db.manyOrNone(`SELECT * FROM color;`)
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


#### `getAllBycolor()` - gets all the colors for a given color
- **pg-promise method:** `db.manyOrNone`
- **SQL Query:**
```sql 
SELECT * FROM color WHERE color_id=$1;
```
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
SELECT * FROM color WHERE id=$1


```


// we use this for show AND for the edit GET route
color.find = function(req, res, next) {
  db.oneOrNone("SELECT * FROM palette WHERE id = $1;", [req.params.id])
    .then(function(result){
      console.log('$$$$$$$$$', result);
      res.locals.task = result;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
INSERT INTO colors (blue, green) VALUES ($1, $2) RETURNING id;

- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
UPDATE colors SET blue= $1, green= $2 WHERE id = $3 RETURNING id;

```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 

DELETE FROM colors where id=$1;
```
- **Locals key:**  

## Exports
module.exports = color;