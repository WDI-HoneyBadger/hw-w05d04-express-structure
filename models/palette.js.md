USE THE COLOR MODEL AS REFERENCE

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
SELECT * FROM todo WHERE id=$1
```
- **Locals key:**  
#### `create()` - adds a color to our database
- **pg-promise method:** 
- **SQL Query:**
```sql 
INSERT INTO todo(subject, content) VALUES($1, $2) RETURNING id
```
- **Locals key:**  
#### `update()` - edits a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
UPDATE todo SET subject = $1, content = $2
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** 
- **SQL Query:**
```sql 
DELETE FROM todo WHERE id=$1;
```
- **Locals key:**  

## Exports
PUT WHAT YOU EXPORT HERE

module.exports = color module;
