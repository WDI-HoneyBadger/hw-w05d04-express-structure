USE THE PALETTES CONTROLLER AS REFERENCE# Palettes Controller

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE

var express = require('express');
var router = express.Router();
var Color = require('../models/color');

## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 

router.get('/new', renderNew);
router.get('/:id', Color.find, renderShow);
router.get('/:id/edit', Color.find, renderEdit);
router.post('/', Color.create, redirectShow);
router.delete('/:id', Color.delete, renderShow);
router.put('/:id', Color.update, renderShow);
```
You can also import other controllers that go off of the same paths. For this controller the base is `/Colors` The colors controller is going to have a base of `/Colors/:Color_id/colors` we can therefore do the following:
```js
var colorsController = require('./colorsController');
router.use('/:Color_id/colors', Color.find, colorsController);
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
  mustacheVariables = res.locals.Color;
  res.render('./Color/show', mustacheVariables);
}

function renderNew(req, res){
  res.render('./Color/new');
}


function renderEdit(req, res){
    mustacheVariables = {
      Color: res.locals.Color
    }
    console.log(mustacheVariables)
    res.render('./Color/edit', mustacheVariables);
  }


---
#### renderIndex - renders all of the Colors
- mustacheVariables: 
```js

function renderIndex(req, res){
  mustacheVariables = {
    Color: res.locals.Color
  }
  console.log(mustacheVariables)
  res.render('./Color/index', mustacheVariables);
}

```
- view: `./colors/index`

---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---

#### redirectIndex - redirects to the list of Colors 
- redirect_url: `/colors`
function redirectShow(req, res) {
  console.log(req.body);
  res.redirect(`/colors/${res.locals.color_id}`);
}
---


## Exports
PUT WHAT YOU EXPORT HERE

module.exports = router;