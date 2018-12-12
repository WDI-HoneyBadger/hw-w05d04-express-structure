# Colors Edit Page

Edit pages render forms to make requests to edit data within our database.

### Method: `POST which will be override to PUT `
### Action: `palette/{{pallete_id}}/colors/{{color_id}}?_method=PUT`
### Inputs:
 ```html
   <label for="name"> Color<input id="name" name="name" type="text" value ="{{name}}"></label>
   <button type="submit">Edit Color </button>
   ```  
## Other things we want to render:

```html
<a href="/palettes"> All palettes </a>
<a href="/palettes/new"> New palette </a>
```