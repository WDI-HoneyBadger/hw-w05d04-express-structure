# Palettes Index Page

Index pages list multiple items from our database. We can loop through our data using mustache to add html elements for each item. 

## How to loop through data:
```html
{{#palette}}
    {{p_row1}}
    {{p_row2}}
{{/palette}}
```