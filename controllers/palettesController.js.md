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

router.get('/new', renderNew);

router.get('/:id/edit', palette.find, renderEdit);

router.get('/:id', palette.find, renderShow);

router.post('/', palette.create, redirectShow);

router.delete('/:id', palette.delete, redirectIndex);

router.put('/:id', palette.update, redirectShow);
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
---
#### renderShow - renders all of the palettes
- mustacheVariables: 
```js
mustacheVariables = {
  palettes: res.locals.palette
}
```
- view: `./palettes/show/`

---
---
#### renderNew - renders all of the palettes
- mustacheVariables: `N/A`

- view: `./palettes/new`

---
---
#### renderEdit- renders all of the palettes
- mustacheVariables: 
```js
mustacheVariables = {
  palettes: res.locals.palette
}
```
- view: `./palettes/edit`

---



USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of palettes 
- redirect_url: `/palettes`
---
---
#### redirectShow - redirects to the list of palettes 
- redirect_url: `/palettes/${res.locals.palette_id}`
---


## Exports
PUT WHAT YOU EXPORT HERE
`module.exports = router`