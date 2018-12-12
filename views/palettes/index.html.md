# Palettes Index Page

Index pages list multiple items from our database. We can loop through our data using mustache to add html elements for each item. 

## How to loop through data:
```html
{{#palette}}
    <a href="/palette/{{id}}">
      <h3>{{palette}}</h3>
    </a>

    {{/palette}}
```