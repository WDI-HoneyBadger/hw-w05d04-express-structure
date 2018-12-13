# Palettes New Page

New pages render forms to make requests to create new data within our database.

### Method:
### Action:
### Inputs:

## Other things we want to render:
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>New palette</title>
</head>
<body>
  <h1>Create new palette</h1>
  <form action="/palettes" method="POST">
    <label for="name"> Name<input id="name" name="name" type="text"></label>
    <label for="description">  <input id="description" type="text" name="description"></label>
    <button type="submit">Submit</button>
  </form>
</body>
</html> 