USE THE COLORS CONTROLLER AS REFERENCE
# Colors Controller

## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE

## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 
router.get('/', color.getAll, renderIndex);
PUT THE ROUTES NEEDED FOR THIS CONTROLLER HERE
router.get('/new', renderNew);
router.get('/:id', color.find, renderShow);
router.post('/', color.create, redirectShow);
router.post('/:id', color.delete, redirectShow);
router.get('/:id/edit', color.find, renderShow);
router.post('/:id', color.update, redirectShow);

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
#### renderIndex - renders all of the Colors
- mustacheVariables: 
```js
mustacheVariables = {
  colors: res.locals.colors
}
```
- view: `./colors/show`

---


USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of Colors 
- redirect_url: `palettes/:palette_id/Colors`
---


## Exports
PUT WHAT YOU EXPORT HERE
- `module.exports = router;`