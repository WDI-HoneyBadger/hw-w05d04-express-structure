# Palettes Index Page

Index pages list multiple items from our database. We can loop through our data using mustache to add html elements for each item. 

## How to loop through data:
```html

<body>
    <h1> LIST </h1>
    {{#cp}}
    <ul>
            <li>id: {{id}}</li>
            <li>first: {{first}}</li>       
             <li>last: {{last}}</li>                
    </ul>
  {{/cp}}

 <a href="/cp/new">  new palette  </a>
 <a href="./palettes/index"> all palette  </a>
```