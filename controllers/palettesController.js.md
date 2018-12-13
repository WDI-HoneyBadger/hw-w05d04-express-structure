# Palettes Controller

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE

## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 
router.get('/', palette.getAll, renderIndex);
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
- view: `./palettes/index`

---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of palettes 
- redirect_url: `/palettes`
---
var express = require('express');
var router = express.Router();

var palettes =  require('../models/color');


router.get('/', palettes.getAll, renderIndex);
router.get('/new', renderNew);
router.get('/:id/edit', palettes.find, renderEdit);
router.get('/:id', palettes.find, renderShow);


router.delete('/:id', palettes.delete, redirectIndex);
router.post('/', palettes.create, redirectShow);
router.put('/:id', palettes.update, redirectShow);



function redirectIndex(req, res) {
  res.redirect('/palettes');
}

function redirectShow(req, res) {
  res.redirect(`/palettes/${res.locals.data_id}`);
}

function renderEdit(req, res) {
  var mustacheVariables = res.locals.palettes

  res.render('./palettes/edit', mustacheVariables);
}


function renderIndex(req, res){
  var mustacheVariables = {
   palettes : res.locals.palettes
  }
 res.render("./palettes/index', mustacheVariables);
}

function renderShow(req, res){
  // res.send(res.locals.color);
  var mustacheVariables = res.locals.palettes
  res.render('./palettes/show', mustacheVariables);
}

function renderNew(req, res){
  res.render('./palettes/new')
}

module.exports = router;

## Exports
PUT WHAT YOU EXPORT HERE