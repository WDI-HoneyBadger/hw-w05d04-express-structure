USE PALETTES AS A REFERENCE
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Show color</title>
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