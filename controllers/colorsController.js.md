USE THE PALETTES CONTROLLER AS REFERENC

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
var express = require('express');
var router = express.Router();

var color = require('../models/colors');


## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 
router.get('/', color.getAll, renderIndex);
router.get('/', colors.getAll, renderIndex);
router.get('/new', renderNew);
router.get('/:id/edit', colr.find, renderEdit);
router.get('/:id', color.find, renderShow);
```
You can also import other controllers that go off of the same paths. For this controller the base is `/color` The colors controller is going to have a base of `/color/:clor_id/colors` we can therefore do the following:
```js
var colorsController = require('./colorsController');
router.use('/:color_id/colors', color.find, colorsController);

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
function renderShow(req, res){
  // res.send(res.locals.color);
  var mustacheVariables = res.locals.color
  res.render('./color/show', mustacheVariables);

---

USE THE FOLLOWING TEMPLATE FOR EACH RENDER:

#### renderIndex - renders all of the palettes
- mustacheVariables: 
```js
mustacheVariables = {
  color: res.locals.color
}
```
- view: `res.render('./color/index', mustacheVariables);`

---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:
function redirectIndex(req, res) {
  res.redirect('/color');
}

function redirectShow(req, res) {
  res.redirect(`/color/${res.locals.color_id}`);
}

---
#### redirectIndex - redirects to the list of color
- redirect_url: `res.redirect('/color');`

---


## Exports
module.exports = router;