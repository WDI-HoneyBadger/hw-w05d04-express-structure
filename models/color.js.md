# Color Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
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



#### `getAllByPalette()` - gets all the colors for a given palette 
- **pg-promise method:** `db.manyOrNone`
- **SQL Query:**
```sql 
SELECT * FROM colors WHERE palette_id=$1;
```
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
```

```js
color.find = function (req, res, next) {
    var id = req.params.id;
    db.oneOrNone("SELECT * FROM table WHERE id = $1;", [id])
      .then(function(result){
        res.locals.todo = result;
        next();
      })
      .catch(function(error){
        console.log(error);
        next();
      })
    }

      
```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
```js
color.create = function(req, res, next){

      console.log("body\n\n\n\n",req.body)
        var colorData = {
            key1: req.body.coulom1,
            key2: req.body.coulom2 ,
            key3:req.body.coulom3
          
        }
        db.one(
          `INSERT INTO color
          (coulom1, coulom2 , coulom3)
          VALUES ($1, $2 ,$3) RETURNING id;`,
          [colorData.coulom1, colorData.coulom2 , colorData.coulom3])
          .then(function (result) {
            console.log(result)
            res.locals.color_id = result.id;
            next();
          })
          .catch(function (error) {
            console.log(error);
            next();
          })
      }
      ```
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
```js
color.update = function(req, res, next){
        var colorData = {
            key1: req.body.coulom1,
            key2: req.body.coulom2 ,
            key3:req.body.coulom3
        }
        console.log(req.body)

        db.one("UPDATE color SET coulom1 = $1, coulom12= $2  , coulom3 =$3 WHERE id = $4 RETURNING id;",
          [colorData.coulom1, colorData.coulom2 , colorData.coulom3, req.params.id ])
          .then(function (result) {
            console.log(result)
            res.locals.color_id = result.id;
            next();
          })
          .catch(function (error) {
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
```js
color.delete = function(req, res, next){
        db.none('DELETE FROM color WHERE id=$1;', [req.params.id])
          .then(function(){
            console.log('successful delete');
            next();
          })
          .catch(function(error){
            console.log(error);
            next();
          })
      }
```
- **Locals key:**  

## Exports
```js
module.exports = color;
```