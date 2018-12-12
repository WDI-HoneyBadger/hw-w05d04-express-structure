USE PALETTES AS A REFERENCE
# Colors Show Page

Show pages give us specific details about a given item of data. We can access different attributes from the data we sent to view by using the name of the key surrounded by curly braces. 

## How to render data:
```html
{{keyValue}}
```

Generally there is also a way to delete the showed data. This requires a form:

### Method: 
- `GET`
### Action:
- `/palette/:plaette_id/colors/:color_id/delete`

We also want to show all of the colors here. How can we do that?
```html 
{{#propertyName}}
    {{keyValue}}
{{/propertyName}}
```