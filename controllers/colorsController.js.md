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
router.get('/new', renderNew);

router.get('/:id/edit', color.find, renderEdit);

router.get('/:id', color.find, renderShow);

router.post('/', color.create, redirectShow);

router.delete('/:id', color.delete, redirectIndex);

router.put('/:id', color.update, redirectShow);
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
mustacheVariables = {
  colors: res.locals.colors
}
```
- view: `./colors/index`

---
---
#### renderShow - renders all of the colors
- mustacheVariables: 
```js
mustacheVariables = {
  colors: res.locals.color
}
```
- view: `./colors/show/`

---
---
#### renderNew - renders all of the colors
- mustacheVariables: `N/A`

- view: `./colors/new`

---
---
#### renderEdit- renders all of the colors
- mustacheVariables: 
```js
mustacheVariables = {
  colors: res.locals.color
}
```
- view: `./colors/edit`

---



USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of colors 
- redirect_url: `/colors`
---
---
#### redirectShow - redirects to the list of colors 
- redirect_url: `/colors/${res.locals.color_id}`
---


## Exports
PUT WHAT YOU EXPORT HERE
`module.exports = router`