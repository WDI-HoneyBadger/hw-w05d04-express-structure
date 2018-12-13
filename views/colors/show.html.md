USE PALETTES AS A REFERENCE

# colors Show Page

Show pages give us specific details about a given item of data. We can access different attributes from the data we sent to view by using the name of the key surrounded by curly braces. 

## How to render data:
```html
{{#colors}}
{{name}}
{{cmyk}}
{{/colors}}
```

Generally there is also a way to delete the showed data. This requires a form:

### Method: POST
### Action: /colors/{{id}}?_method=DELETE

