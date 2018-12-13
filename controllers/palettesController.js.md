# Palettes Controller

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
```js
var express = require('express');
var router = express.Router();
var palettes = require('..models/palettes')
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
router.get('/:palette_id/edit', palette.find, renderEdit);
router.get('/:palette_id', palette.find , renderShow);
router.post('/',palette.create, redirectShow);
router.delete('/:palette_id', palette.delete , redirectIndex);
router.put('/:palette_id', palette.update , redirectShow)
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
function renderIndex(req,res){
var mustacheVariables = {
  palettes: res.locals.palettes
}
res.render('.palettes/index',mustacheVaribles)
}

function renderShow(req,res){
  var mustacheVaribles = {
    palettes : res.locals.palettes
  }
  res.render(`./palettes/show`,mustacheVaribles)
}

function renderEdit(req,res){
  var mustachVariables = res.locals.list;
    res.render( `./palettes/edit`, mustachVariables)
}

function renderNew(req, res){
    res.render('./palettes/new');
}

```
- view: `./palettes/index`

---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of palettes 
```js
function redirectShow(req,res){
    res.redirect(`/palettes/${res.locals.palette_id}`);
}


function redirectIndex(req){
  res.redirect(`/palettes`);
}

```
- redirect_url: `/palettes`
---


## Exports
```js
module.exports = router;
```