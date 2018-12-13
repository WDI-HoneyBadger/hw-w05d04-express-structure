# Color Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
```js
var db = require('../db/config');
var color = {}//why

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


- **SQL Query:**

```sql

colors.getAll = function(req,res,next){
db.manyOrNone("SELECT * FROM colors WHERE palette_id=$1")
.then (function(error){
  res.locals.color=result;
  next();
})
}
```

```sql
color.find =function(req,res,next){
  db.oneOrNone("SELECT  FROM colors WHERE id=1$;",[req.params.id]);
  .then(function(result){
    res.locals.colors = result;
    next();
  })
}
```

```sql 
```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
- **Locals key:**  

## Exports
PUT WHAT YOU EXPORT HERE
```js
module.exports = color;
```