# Palettes Show Page

Show pages give us specific details about a given item of data. We can access different attributes from the data we sent to view by using the name of the key surrounded by curly braces. 

## How to render data:
```html

{{#palettes}}
   <h2> {{name}}<h2>
   <p> {{explanation}}</p>
{{/palettes}}
```

Generally there is also a way to delete the showed data. This requires a form:

### Method: `POST which will be override to delete`
### Action:`/palettes/{{palette_id}}?_method=DELETE`

We also want to show all of the colors here. How can we do that?
```html 

{{#color}}
  <div style="background-color:{{name}} width:100px; height:100px">
{{/color}}

```