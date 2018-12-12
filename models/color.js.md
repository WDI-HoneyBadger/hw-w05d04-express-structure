# Color Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE

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
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
SELECT * FROM colors WHERE id=$1
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
INSERT INTO colors (color1, color2, color3, color4) VALUES ($1, $2, $3, $4) RETURNING id;
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
UPDATE colors SET color1 = $1, color2 = $2, color3 = $3, color4 = $4 WHERE id = $5 RETURNING id;
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
```
DELETE FROM colors where id=$1;
- **Locals key:**  

## Exports
PUT WHAT YOU EXPORT HERE