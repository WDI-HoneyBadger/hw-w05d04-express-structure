# Palettes Edit Page

Edit pages render forms to make requests to edit data within our database.

### Method:
```
method="POST"
```
### Action:
```
action="/palette/{{id}}?_method=PUT"
```
### Inputs:
```html
<label for="palette">
      task: <input type="text" name="palette" id="palette" value="{{palette}}"/>
    </label>
 ```

## Other things we want to render:
```html
<button type="submit">Submit Update</button>
```