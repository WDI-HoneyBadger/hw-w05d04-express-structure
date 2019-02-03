# colorss New Page


### Method: `POST`
### Action: `/palettes/{{palette_id}}/colors`
### Inputs: 
input fields for each of the columns in the table except id
```html
    <label for="name"> Color<input id="name" name="name" type="text"></label>
    <button type="submit">Save Color </button>
    <a href="/palattes"><button type="submit">Cancel </button></a>
```
## Other things we want to render:
```html
<a href="/palettes"> All palettes </a>
<a href="/palettes/new"> New palette </a>
```