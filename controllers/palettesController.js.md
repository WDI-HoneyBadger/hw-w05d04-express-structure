# Palettes Controller

## Required Modules
var express = require('express');
var router = express.Router();
var app = require('../models/palette');

## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 
router.get('/', palette.getAll, renderIndex);
router.get('/:id', palette.find, renderShow);
```
You can also import other controllers that go off of the same paths. For this controller the base is `/palettes` The colors controller is going to have a base of `/palettes/:palette_id/colors` we can therefore do the following:
```js
var colorsController = require('./colorsController');
router.use('/:palette_id/colors', palette.find, colorsController);
```

## Middleware
Controller middleware is used to send back a response to the client. This can be by either rendering a html page or by redirecting to another route. The basic structure for controller middleware is as follows:
```js
function renderSomething(req, res){
  var mustacheVariables = {
    key: res.locals.data
  }
  res.render('./something', mustacheVariables)
}

function redirectSomewhere(req, res){
  res.redirect('path/to/redirect')
}
```

### Middleware needed for this controller:

---

USE THE FOLLOWING TEMPLATE FOR EACH RENDER:

function renderIndex(req, res){
  var mustacheVariable = {
    dataList: res.locals.app
  };
  res.render('./palettes/index', mustacheVariable);
};


---
#### renderIndex - renders all of the palettes
- mustacheVariables: 
```js
mustacheVariables = {
  palettes: res.locals.palettes
}
```
- view: `./palettes/index`

---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of palettes 
- redirect_url: `/palettes`
---


## Exports
module.exports = router;