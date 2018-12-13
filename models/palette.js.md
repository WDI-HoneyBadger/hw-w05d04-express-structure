# Palette Model
Models contain middleware functions that are used to talk to our database. 

## Required Modules 
PUT YOUR REQUIRED MODULES AND PACKAGES HERE

## Middleware
Each middleware method is added to our model. the basic structure is as follows:

```js
palette.getAll = function(req, res, next){
  db.manyOrNone(`SELECT * FROM palettes;`)
    .then(function(result){
      res.locals.palette = result;
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
- **Locals key:** `res.locals.palettes`
`
#### `find()` - gets a specific palette
- **pg-promise method:**   `db.oneOrNone`
- **SQL Query:**
```sql 
SELECT * FROM palettes WHERE id=$1;
```
- **Locals key:**  `res.locals.palettes`

#### `create()` - adds a palette to our database
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
INSERT INTO palettes (name, description) VALUES ($1, $2) RETURNING id;
```
- **Locals key:**   `res.locals.palette_id`

#### `update()` - edits a specific palette
- **pg-promise method:**  `db.one`
- **SQL Query:**
```sql 
UPDATE palettes SET name = $1, description = $2 WHERE id = $3 RETURNING id;
```
- **Locals key:** 
#### `delete()` - deletes a specific color
- **pg-promise method:** `db.none`
- **SQL Query:**
```sql 
DELETE FROM palettes WHERE id=$1;
```
- **Locals key:**  

## Exports
PUT WHAT YOU EXPORT HERE
module.exports = palettes