USE THE PALETTES CONTROLLER AS REFERENCE
# Palettes Controller

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
var express = require('express');
var router = express.Router();
 var color = require('../models/color');

## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 
router.get('/', palette.getAll, renderIndex);
router.get('./new', renderNew);
 router.get('/:id/edit', color.find, renderEdit);
 router.get('./:id', color.find, renderShow);
 router.post('/', color.create, redirectShow);
 router.delete('/:id', color.delete, redirectIndex);
 router.put('/:id', color.update, redirectShow);
```
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

---
#### renderIndex - renders all of the palettes


- mustacheVariables: 
```js
mustacheVariables = {
  palettes: res.locals.palettes
}
```
 res.render(`./colors/index`,mustacheVariables);

- view: `./palettes/index`

---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of palettes 

function redirectIndex(req,res){
   res.redirect(`/palletes/:pallete_id/colors`);
}
function redirectShow(req,res){
   res.redirect(`/plattes/:palette_id/colors/:colors_id`);
}


## Exports
module.exports = router