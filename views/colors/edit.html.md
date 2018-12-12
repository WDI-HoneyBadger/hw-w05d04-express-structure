USE PALETTE EDIT AS A REFERENCE

uswing the method PUT wit haction and form and label

<form action="/platte/{{id}}?_method=PUT" method="post">
<label for="subject">
      subject: <input type="text" name="subject" id="subject" value="{{subject}}">
</label>
<label for="content">
      content: <input type="text" name="content" id="content" value="{{content}}">
 </label>
 <button type="submit">submit</button>
