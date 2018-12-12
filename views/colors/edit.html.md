# color Edit Page

Edit pages render forms to make requests to edit data within our database.

### Method:
```
method="POST"
```
### Action:
```
action="/color/{{id}}?_method=PUT"
```
### Inputs:
```html
<label for="color">
      task: <input type="text" name="color" id="color" value="{{color}}"/>
    </label>
 ```

## Other things we want to render:
```html
<button type="submit">Submit Update</button>
```