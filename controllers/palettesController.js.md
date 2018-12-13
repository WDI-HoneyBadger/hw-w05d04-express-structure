# Palettes Controller

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
var platte = requir('./model/color')
## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js 
router.method('path', middleWare1, middleWare2);
router.method('/', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 
router.get('/new', palette.getAll, renderIndex);
router.get('/:id', palette.getAll, renderIndex);

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
    plattes: res.locals.plattes
  }
  res.render('./index', mustacheVariables)
}


```

### Middleware needed for this controller:

---

USE THE FOLLOWING TEMPLATE FOR EACH RENDER:

---
#### renderIndex - renders all of the palettes
function renderIndex(req, res){
  var mustacheVariables = {
    plattes: res.locals.plattes
  }
  res.render('./index', mustacheVariables)
}

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
function redirectPalettes(req, res){
  res.redirect('/palettes/index/redirect')
}


## Exports
PUT WHAT YOU EXPORT HERE
mudoles.export= router;