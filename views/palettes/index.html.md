# Palettes Index Page

Index pages list multiple items from our database. We can loop through our data using mustache to add html elements for each item. 

## How to loop through data:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>All palettes</title>
</head>
<body>
  
  <h1>All palettes/h1>

  <a href="/">Back to home page</a>
  {{#palettes}}
<ul>
  <a href="/palettes/{{palette_id}}"><li>{{name}}</li></a>
  <li>{{description}}</li>
</ul>
  {{/palettes}}
</body>
</html> 
```
