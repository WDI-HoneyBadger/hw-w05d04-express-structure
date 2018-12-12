# Palettes Index Page

Index pages list multiple items from our database. We can loop through our data using mustache to add html elements for each item. 

## How to loop through data:
```html
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  {{#palettes}}
    <a href="/palettes/{{id}}">
      <h2>{{subject}}</h2>
    </a>  
    <p>{{content}}</p>
  {{/palettes}}
</body>
</html>