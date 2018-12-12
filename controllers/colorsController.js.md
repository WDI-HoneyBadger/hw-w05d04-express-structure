USE THE colors CONTROLLER AS REFERENCE

# colors Controller

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
```
var express = require('express');
var router = express.Router();

var color = require('../models/color');
```
## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 
router.get('/', color.getAll, renderIndex);
router.get('palletes/:pallate_id/colors/new', renderNew);
router.get('/:id/edit', color.find, renderEdit);
router.get('/:id', color.find, renderShow);

router.delete('/:id', color.delete, redirectIndex);
router.post('/palletes/:pallete_id/colors', color.create, redirectShow);
router.put('/:id', color.update, redirectShow);
PUT THE ROUTES NEEDED FOR THIS CONTROLLER HERE
```
You can also import other controllers that go off of the same paths. For this controller the base is `/colors` The colors controller is going to have a base of `/colors/:color_id/colors` we can therefore do the following:
```js
var colorsController = require('./colorsController');
router.use('/:color_id/colors', color.find, colorsController);
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
renderShow(req,res){
  var mustacheVariables = res.locals.color
  res.render('./color/show', mustacheVariables);
}
---

USE THE FOLLOWING TEMPLATE FOR EACH RENDER:

---
#### renderIndex - renders all of the colors
function renderIndex(req,res){
- mustacheVariables: 
```js
mustacheVariables = {
  colors: res.locals.colors
}
```
- res.render(`./colors/index`,mustacheVariables);
}
---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of colors 
function redirectIndex(req,res){
   res.redirect(`/palletes/:pallete_id/colors`);
}
function redirectShow(req,res){
   res.redirect(`/plattes/:palette_id/colors/:colors_id`);
}

---


## Exports
exports = router;