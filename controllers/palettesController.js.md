# Palettes Controller

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
```
var express = require('express');
var router = express.Router();

var palette = require('../models/palette');
```
## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 
router.get('/', palette.getAll, renderIndex);
router.get('/new', renderNew);
router.get('/:id/edit', palette.find, renderEdit);
router.get('/:id', palette.find, renderShow);

router.delete('/:id', pallete.delete, redirectIndex);
router.post('/', pallete.create, redirectShow);
router.put('/:id', pallete.update, redirectShow);
PUT THE ROUTES NEEDED FOR THIS CONTROLLER HERE
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
renderShow(req,res){
  var mustacheVariables = res.locals.palette
  res.render('./palette/show', mustacheVariables);
}
---

USE THE FOLLOWING TEMPLATE FOR EACH RENDER:

---
#### renderIndex - renders all of the palettes
function renderIndex(req,res){
- mustacheVariables: 
```js
mustacheVariables = {
  palettes: res.locals.palettes
}
```
- res.render(`./palettes/index`,mustacheVariables);
}
---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of palettes 
function redirectIndex(req,res){
   res.redirect(`/palettes`);
}

---


## Exports
exports = router;