# Colors Show Page

Show pages give us specific details about a given item of data. We can access different attributes from the data we sent to view by using the name of the key surrounded by curly braces. 

## How to render data:
```html
<h1>{{something}}</h1>
```

Generally there is also a way to delete the showed data. This requires a form:

### Method: DELETE
### Action: "/palettes/{{palette_id}}/colors/{{color_id}}?_method=DELETE"

We also want to show the color here. How can we do that?
```html 
 {{hexVal}} <!--  <- assuming thats a column in the colors table -->
```