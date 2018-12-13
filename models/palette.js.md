USE THE COLOR MODEL AS REFERENCE

# Color Model
Models contain middleware functions that are used to talk to our database. 
```js
var db = require('../db/config');
```
## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
```js
var palettes = {};
```
## Middleware
Each middleware method is added to our model. the basic structure is as follows:

```js
palettes.getAll = function(req, res, next){
   var palette_id = req.params.palette_id;
  db.manyOrNone(`SELECT * FROM palettes;`])
    .then(function(result){
      res.locals.colors = result;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
}

palettes.find = function(req,res,next){
    var palette_id = req.params.palette_id;
    db.oneOrNone("SELECT * FROM palettes WHERE palette_id =$1;" ,[palette_id])
    .then(function(result){
        res.locals.palettes =result;
        console.log(result);
        next();
    })
    .catch(function(error){
        console.log(error);
        next();
    })
}


palettes.create = function(req,res,next){
    var palettes = {
        name: req.body.name,
        description: req.body.description
    }

    db.one(`INSERT INTO palettes (name , descrption) VALUES ($1,$2)  WHERE palette_id = $3 RETURNING  palette_id;`, [palettes.name,paletees.description])
    .then(function(result){
        res.locals.palette_id=result.id;
        next();
    })
    .catch(function(error){
        console.log(error);
        next();
    })
}


palettes.update = function (req,res,next){
   var palettes = {
        name: req.body.name,
        description: req.body.description
    }
    db.one(`UPDATE palettes SET name = $1 , description = $2 WHERE palette_id = $3 RETURNING  palette_id;`,[colors.name, colors.bgcolor , colors.description])
.then(function (result){
    res.locals.palette_id=result.id;
    next();
})
.catch(function(error){
    console.log(error);
    next();
})
    
}



palettes.delete = function (req,res,next){
    db.none(`DELETE FROM palettes WHERE  palette_id =$2 `, [req.params.palette_id])
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
`SELECT * FROM palettes;`
```
- **Locals key:** `res.locals.colors`
#### `find()` - gets a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
"SELECT * FROM palettes WHERE palette_id =$1;"
```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql 
`INSERT INTO palettes (name , descrption) VALUES ($1,$2)  WHERE palette_id = $3 RETURNING  palette_id;`
```
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
`UPDATE palettes SET name = $1 , description = $2 WHERE palette_id = $3 RETURNING  palette_id;`
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
`DELETE FROM palettes WHERE  palette_id =$2 `
```
- **Locals key:**  
```js
module.exports = palettes;
```
## Exports
PUT WHAT YOU EXPORT HERE