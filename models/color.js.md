# Color Model
Models contain middleware functions that are used to talk to our database. 
```js
var db = require('../db/config');
var colors = {};
```
## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
```js
var colors = {};
```
## Middleware
Each middleware method is added to our model. the basic structure is as follows:

```js
colors.getAll = function(req, res, next){
   var palette_id = req.params.palette_id;
  db.manyOrNone(`SELECT * FROM colors WHERE palette_id = $1;`,[palette_id])
    .then(function(result){
      res.locals.colors = result;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}

colors.find = function(req,res,next){
    var palette_id = req.params.palette_id;
    var color_id = req.params.color_id;
    db.oneOrNone("SELECT * FROM colors WHERE color_id=$1 AND palette_id =$2;" ,[palette_id,color_id])
    .then(function(result){
        res.locals.colors =result;
        console.log(result);
        next();
    })
    .catch(function(error){
        console.log(error);
        next();
    })
}


colors.create = function(req,res,next){
    var colors = {
        name: req.body.name,
        bgcolor: req.body.bgcolor,
    }

    db.one(`INSERT INTO colors (name , bgcolor) VALUES ($1,$2)  WHERE palette_id = $3 RETURNING color_id;`, [colors.name,colors.bgcolor,req.params.palette_id,req.params.color_id])
    .then(function(result){
        res.locals.color_id=result.id;
        next();
    })
    .catch(function(error){
        console.log(error);
        next();
    })
}


colors.update = function (req,res,next){
    var colors = {
        name: req.body.name,
        bgcolor: req.body.bgcolor,
       
    }

    db.one(`UPDATE colors SET name = $1 , bgcolor = $2 WHERE id = $3 RETURNING color_id;`,[colors.name, colors.bgcolor,req.params.palette_id,req.params.color_id]])
.then(function (result){
    res.locals.colors_id=result.id;
    next();
})
.catch(function(error){
    console.log(error);
    next();
})
    
}



colors.delete = function (req,res,next){
    db.none(`DELETE FROM colors WHERE color_id=$1 AND palette_id =$2 `, [req.params.color_id,req.params.palette_id])
    .then(function (){
        console.log('success delete');
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
"SELECT * FROM colors WHERE palette_id=$1;"
```
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
"SELECT * FROM colors WHERE color_id=$1 AND palette_id =$2;"
```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql 
`INSERT INTO colors (name , bgcolor) VALUES ($1,$2)  WHERE palette_id = $3 RETURNING color_id;`
```
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
(`UPDATE colors SET name = $1 , bgcolor = $2 WHERE id = $4 RETURNING color_id;`
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
`DELETE FROM colors WHERE color_id=$1 AND palette_id =$2 `
```
- **Locals key:**  
```js
module.exports = colors;
```
## Exports
PUT WHAT YOU EXPORT HERE
