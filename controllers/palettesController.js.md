# Palettes Controller

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE

var express = require('express');
var router = express.Router();
var Palette = require('../models/palette');

## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 
router.get('/', Palette.getAll, renderIndex);
router.get('/new', renderNew);
router.get('/:id', Palette.find, renderShow);
router.get('/:id/edit', Palette.find, renderEdit);
router.post('/', Palette.create, redirectShow);
router.delete('/:id', Palette.delete, renderShow);
router.put('/:id', Palette.update, renderShow);
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



function renderShow(req,res){
  mustacheVariables = res.locals.Palette;
  res.render('./Palette/show', mustacheVariables);
}

function renderNew(req, res){
  res.render('./Palette/new');
}


function renderEdit(req, res){
    mustacheVariables = {
      Palette: res.locals.Palette
    }
    console.log(mustacheVariables)
    res.render('./Palette/edit', mustacheVariables);
  }


---
#### renderIndex - renders all of the Palettes
- mustacheVariables: 
```js

function renderIndex(req, res){
  mustacheVariables = {
    Palette: res.locals.Palette
  }
  console.log(mustacheVariables)
  res.render('./Palette/index', mustacheVariables);
}

```
- view: `./Palettes/index`

---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---

#### redirectIndex - redirects to the list of palettes 
- redirect_url: `/Palettes`
function redirectShow(req, res) {
  console.log(req.body);
  res.redirect(`/Palette/${res.locals.Palette_id}`);
}
---


## Exports
PUT WHAT YOU EXPORT HERE

module.exports = router;