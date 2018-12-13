# Palettes Controller

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
 ```js 
 var express = require('express');
 var router = express.Router();
 var app = require('../models/palette')


```
## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js
router.method('path', middleWare1, middleWare2);

```
```js 
router.get('/', palette.getAll, renderIndex);//home page
router.get('/new', renderNew);
router.get('/:id/edit',palette.find, renderEdit);//edit element with specific id
router.get('/:id', palette.find , renderShow);

router.delete('/:id',palette.delete , redirectInex );
router.post('/' , palette.create , redirectShow);
router.put('/:id',palette.update , redirectshow );


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

}

function redirectNew(req, res){
  res.redirect('./palettes/new')
}
```

### Middleware needed for this controller:

---

USE THE FOLLOWING TEMPLATE FOR EACH RENDER:

---
#### renderIndex - renders all of the palettes
- mustacheVariables: 
```js
function renderIndex(req, res){
  var mustacheVariables = {
    key: res.locals.data
  }
  res.render('./palettes/index', mustacheVariables)
```
- view: `./palettes/index`

---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of palettes 
- redirect_url: `/palettes`
```js
---

function redirectIndex(req,res){
  res.redirect('/pal')
}

## Exports
PUT WHAT YOU EXPORT HERE

```js
`
module.exports=router
