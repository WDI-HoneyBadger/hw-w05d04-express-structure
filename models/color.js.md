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
- **pg-promise method:**  `db.oneOrNone`
- **SQL Query:**
```sql
SELECT * FROM colors WHERE id=$1
```
- **Locals key:**  `res.locals.color`

#### `create()` - adds a color to our database
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
INSERT INTO colors (bla, blabla) VALUES ($1, $2) RETURNING id;
```
- **Locals key:**  `res.locals.color_id`

#### `update()` - edits a specific color
- **pg-promise method:** `db.one`
- **SQL Query:**
```sql 
UPDATE colors SET bla = $1, blabla = $2 WHERE id = $3 RETURNING id;
```
- **Locals key:** `res.locals.color_id`

#### `delete()` - deletes a specific color
- **pg-promise method:** `db.none`
- **SQL Query:**
```sql 
DELETE FROM colors where id=$1;
```
- **Locals key:**  `N/A`


## Exports
PUT WHAT YOU EXPORT HERE
`module.exports = model`