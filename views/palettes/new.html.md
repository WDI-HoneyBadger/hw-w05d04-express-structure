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
  <title>Document</title>
</head>
<body>
  <h1>Enter a New palettes</h1>
  <form action="/palettes" method="post">
    <label for="subject">
      subject: <input type="text" name="subject" id="subject">
    </label>
    <label for="content">
      content: <input type="text" name="content" id="content">
    </label>
    <button type="submit">submit new palettes</button>
  </form>
</body>
</html>