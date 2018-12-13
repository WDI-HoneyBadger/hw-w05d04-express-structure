USE THE COLOR MODEL AS REFERENCE
## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE

## Middleware
Each middleware method is added to our model. the basic structure is as follows:

```js

var palette = {};

palette.getAll = function(req, res, next){
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
SELECT * FROM palettes WHERE id=$1;
```
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** 
db.oneOrNone
- **SQL Query:**
```sql 
SELECT * FROM palettes WHERE id = $1
<!-- we will use find to get one single iteam -->
color.find = function(req, res, next) {
  db.oneOrNone("SELECT * FROM todo WHERE id = $1;", [req.params.id])
    .then(function(result){
      console.log('-------', result);
    --   - **Locals key:**  
      res.locals.palette = result;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}
```

#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
palette.create = function(req, res, next) {
  db.one("INSERT INTO color(subject, content) VALUES(yellow , green) RETURNING id;", [req.body.subject, req.body.content])
    .then(function(result){
      res.locals.palette_id = result.id;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
palette.update = function(req, res, next) {
  db.one(`UPDATE color SET subject = yellow, content = green
   WHERE id = $3 RETURNING id;`, [req.body.subject, req.body.content, req.params.id])
   .then(function(result){
     console.log(`table updated for ${result.id}`);
     res.locals.palette_id = result.id;
     next();
   })
   .catch(function(error){
    console.log(error);
    next();
  })
}
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
```

palette.delete = function(req, res, next) {
  db.none("DELETE FROM palette WHERE id=$1;", [req.params.id])
    .then(function(){
      console.log('SUCCESSFUL DELETE');
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}
- **Locals key:**  

## Exports
PUT WHAT YOU EXPORT HERE
module.exports = palette;