# Entry Point of Application
This is where all the config for our application goes 

-	Index.js is a configuration and initialisation file where we configure our server to use things - It’s the entry file of our app 


## Required Packages and Config

### express 
```js
var express = require('express');
var app = express();
var port = 3000;
```
### mustache-express 
```js
var mustache = require('mustache-express');
app.engine('html', mustache());
app.set('view engine', 'html');
app.set('views', __dirname + '/views');
```
### body-parser 
```js
var bodyParser = require('body-parser');
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: false }));
```
### method-override 
```js
var methodOverride = require('method-override');
app.use(methodOverride('_method'));
```
### morgan 
```js
var logger = require('morgan');
app.use(logger('dev'));
```

## To set up a public directory 
Setting up a public directory allows us to add styles to our views. We are telling express to make the files within this directory accessable.
```js
app.use('/static', express.static(__dirname + '/public'));
```
From our views we can now link our css by linking files to `/static/styles/style.css`

## Routing and Controllers
We want to give instructions to our application of how to handle incoming requests. We do this with routes. To set up our homepage: 
```js
// We are giving instructions to our app for when someone is making a get request to `/`
app.get('/', function(req, res){
  // Here we are saying that our server should render the view: /views/index.html
  res.render('./index');
})
```

We can also set up routes outside of our index.js (in a controller) and tell our app how to use them. For example our palettes controller:

```js 
var palettesController = require('./controllers/palettesController');

// any time someone makes a request to `/palettes` look in the palettesController for what to do
app.use('/palettes', palettesController);
```

## Accepting requests
Finally we want to tell our server to accept requests. We do this by using the `listen` method on our `app`
```js
app.listen(port, function(){
  console.log(`App is listening on port ${port}`)
})
```