USE PALETTES AS A REFERENCE
# Palettes Show Page

Show pages give us specific details about a given item of data. We can access different attributes from the data we sent to view by using the name of the key surrounded by curly braces. 

## How to render data:
```html
PUT EXAMPLE HERE
```
  <a href="/colors">see all palettes</a>
  <h1>{{subject}}</h1>
  <p>{{content}}</p>

Generally there is also a way to delete the showed data. This requires a form:

### Method: 
  <form action="/colors/{{id}}?_method=DELETE" method="post">
### Action:
<button type="submit">Delete colors</button>

We also want to show all of the colors here. How can we do that?
```html 
```