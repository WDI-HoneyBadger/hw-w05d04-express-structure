# Palettes Edit Page

Edit pages render forms to make requests to edit data within our database.

### Method:
### Action:
### Inputs:

## Other things we want to render:


<body>
        <a href="/"> Home</a>
        <a href="/palette"> palette list </a>
      </div>
      <form class="create" action="/palette/{{id}}?_method=PUT" method="POST" >
        <label for="name">
          first: <input type="text" name="first" id="first" value="{{first}}"/>
        </label>
        <label for="type1">
          last: <input type="text" name="last" id="last" value="{{last}}"/>
        </label>
        <button type="submit">Submit Update</button>
        </form>
</body>
</html>