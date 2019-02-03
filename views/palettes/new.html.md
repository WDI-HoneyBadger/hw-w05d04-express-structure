# Palettes New Page

New pages render forms to make requests to create new data within our database.

### Method: `POST`
### Action: `/palettes`
### Inputs: 
input fields for each of the columns in the table except id
```html
    <label for="name"> palatte<input id="name" name="name" type="text"></label>
    <label for="explanation"> Explanation <input id="explanation" type="text" name="explanation"></label>
    <button type="submit">Create</button>
```
## Other things we want to render:
```html
<a href="/palettes"> All palettes </a>
<a href="/palettes/new"> New palette </a>
```