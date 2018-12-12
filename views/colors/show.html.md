USE colors AS A REFERENCE

# colors Show Page

Show pages give us specific details about a given item of data. We can access different attributes from the data we sent to view by using the name of the key surrounded by curly braces. 

## How to render data:
```html
PUT EXAMPLE HERE
{{c_row1}}
{{c_row2}}
```

Generally there is also a way to delete the showed data. This requires a form:

### Method: post
### Action:/colors/{{id}}?_method=DELETE

We also want to show all of the colors here. How can we do that?
```html 
```