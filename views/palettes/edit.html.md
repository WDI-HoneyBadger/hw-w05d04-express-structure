# Palettes Edit Page

Edit pages render forms to make requests to edit data within our database.

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
  <title>Edit palette</title>
</head>
<body>
    <h1>Edit palette</h1>
    <form action="/palettes/{{palette_id}}?_method=PUT" method="POST">
      <label for="name"> Name<input id="name" name="name" type="text" value ="{{name}}"></label>
      <label for="descriptipn">  <input id="descriptipn" type="text" name="descriptipn" value ="{{descriptipn}}"></label>
      <button type="submit">Edit</button>
    </form>
</body>
</html> 