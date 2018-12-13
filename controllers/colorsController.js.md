USE THE PALETTES CONTROLLER AS REFERENCE
# Palettes Controller

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
```js
var express = require('express');
var router = express.Router();
var palettes = require('..models/color')
```
## Routes 

```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 

router.get('/new', renderNew);
router.get('/:color_id/edit', color.find, renderEdit);
router.get('/:color_id', color.find , renderShow);
router.post('/',color.create, redirectShow);
router.delete('/:color_id', color.delete , redirectIndex);
router.put('/:color_id', color.update , redirectShow)
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
#### renderIndex - renders all of the colors
- mustacheVariables: 
```js


function renderShow(req,res){
  var mustacheVaribles = {
    color : res.locals.colors
  }
  res.render(`./colors/show`,mustacheVaribles)
}

function renderEdit(req,res){
  var mustachVariables = res.locals.colors;
    res.render( `./colors/edit`, mustachVariables)
}

function renderNew(req, res){
    res.render('./colors/new');
}

```
- view: `./palettes/index`

---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of palettes 
```js
function redirectShow(req,res){
    res.redirect(`/palettes/${res.locals.palette_id}/colors/${res.locals.color_id}`);
}


function redirectIndex(req){
  res.redirect(`/palettes/palette_id`);
}

```


## Exports
```js
module.exports = router;
```