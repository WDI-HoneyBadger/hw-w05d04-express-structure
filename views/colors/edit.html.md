
<body>
        <a href="/"> Home</a>
        <a href="/color"> color list </a>
      </div>
      <form class="create" action="/color/{{id}}?_method=PUT" method="POST" >
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