USE PALETTES AS A REFERENCE
# Palettes Show Page

Show pages give us specific details about a given item of data. We can access different attributes from the data we sent to view by using the name of the key surrounded by curly braces. 

## How to render data:
```html
 {{#cp}}
    <h1>{{cp.first}}</h1>
    <h1>{{cp.last}}</h1>
    {{/cp}}
```

Generally there is also a way to delete the showed data. This requires a form:

### Method: 
### Action:
 <form action="/color/{{id}}?_method=DELETE" method="POST">
      <button type="submit">delete </button>
    </form>
We also want to show all of the colors here. How can we do that?
<a href="/palette">show all paleete </a>
```html 
```


<body>  <a href="/color">back</a>
    {{#cp}}
    <h1>{{cp.subject}}</h1>
    <h1>{{cp.last}}</h1>
    {{/cp}}
    <form action="/color/{{id}}?_method=DELETE" method="POST">
      <button type="submit">delete </button>
    </form>
  