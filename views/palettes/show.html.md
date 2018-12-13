# Palettes Show Page

Show pages give us specific details about a given item of data. We can access different attributes from the data we sent to view by using the name of the key surrounded by curly braces. 

## How to render data:
```html
PUT EXAMPLE HERE
```

Generally there is also a way to delete the showed data. This requires a form:

### Method: 
### Action:

We also want to show all of the colors here. How can we do that?
```html 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Show palette</title>
</head>
<body>
  
    <a href="/">Back to home page</a>
    <a href="/palettes">All palettes</a>
<ul>
    {{#palettes}}
  <li>{{name}}</li>
  <li>{{description}}</li>
  <form action="/palettes/{{palette_id}}?_method=DELETE" method="POST">
    <button type="submit">Delete palette</button>
  </form>
  {{/palettes}
</ul>
</body>
</html>
```