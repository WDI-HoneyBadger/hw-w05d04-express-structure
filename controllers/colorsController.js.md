# colors Controller

## Required Modules
```js
var express = require('express');
var router = express.Router();
var  app = require('../models/color');
``` 

## Routes 
```js 
router.method('path', middleWare1, middleWare2);
```
```js
router.get('/', color.getAll, renderIndex);
router.get('/new', renderNew);
router.get('/:id/edit',color.find , renderEdit);
router.get('/:id', color.find, renderShow);
router.post('/', color.create, redirectShow);
router.delete('/:id', color.delete, redirectIndex);
router.put('/:id',color.update , redirectShow);

```

### Routes needed for this controller:
```js 
router.get('/', color.getAll, renderIndex);
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
function renderIndex(req, res){
  var mustacheVariables = {
    key: res.locals.data
  }
  res.render('./color/index', mustacheVariables)
}

function redirectShow(req, res){
  res.redirect('./color/${res.locals.data_id}')
}

function renderNew(req, res){
    res.render('./color/new');
  }
  
```

### Middleware needed for this controller:

---
```js

  function redirectShow(req, res) {
    console.log(req.body);
    res.redirect(`/color/${res.locals.color_id}`);
  }
  
  function renderEdit(req,res){
    var mustacheVariables =  res.locals.color ;

    res.render('./color/edit',mustacheVariables);
    }
    ```

---
#### renderIndex - renders all of the palettes
- mustacheVariables: 
```js
mustacheVariables = {
  color: res.locals.color
}
```
- view: `./color/index`
```js
function renderIndex(req, res){
    mustacheVariables = {
        color: res.locals.color
    }
    res.render('./color/index', mustacheVariables);
  }
  ```
---




---
#### redirectIndex - redirects to the list of palettes 
- redirect_url: `/color`
```js
function redirectIndex(req, res){
    res.redirect('/color');
  }
  ```
---


## Exports
```js
module.exports = router;
```
