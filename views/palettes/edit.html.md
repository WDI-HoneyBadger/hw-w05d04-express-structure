# Palettes Edit Page

Edit pages render forms to make requests to edit data within our database.

### Method: `POST which will be override to PUT `
### Action: `palettes/{{palette_id}}?_method=PUT`
### Inputs:
 ```html
   <label for="name"> Palatte<input id="name" name="name" type="text" value ="{{name}}"></label>
      <label for="explanation">  <input id="explanation" type="text" name="explanation" value ="{{explanation}}"></label>
      <button type="submit">Create </button>
   ```  
## Other things we want to render:

```html
<a href="/palettes"> All palettes </a>
<a href="/palettes/new"> New palette </a>

```