# Palettes Index Page

Index pages list multiple items from our database. We can loop through our data using mustache to add html elements for each item. 

## How to loop through data:
```html
```{{#tpalettes}}
    <a href="/palettes/{{id}}">
      <h2>{{subject}}</h2>
    </a>  
    <p>{{content}}</p>
  {{/palettes}}