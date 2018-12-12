
### Method: `POST which will be override to delete`
### Action:`/palettes/{{palette_id}}/colors/{{color_id}}?_method=DELETE`

We also want to show all of the colors here. How can we do that?
```html 
{{#color}}
  <div style="background-color:{{name}} width:100px; height:100px">
{{/color}}


```