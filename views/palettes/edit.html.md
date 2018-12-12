# Palettes Edit Page

Edit pages render forms to make requests to edit data within our database.

### Method:
### Action:
### Inputs:

## Other things we want to render:

uswing the method PUT wit haction and form and label

<form action="/tasks/{{id}}?_method=PUT" method="post">
<label for="subject">
      subject: <input type="text" name="subject" id="subject" value="{{subject}}">
</label>
<label for="content">
      content: <input type="text" name="content" id="content" value="{{content}}">
 </label>
 <button type="submit">submit changes</button>
