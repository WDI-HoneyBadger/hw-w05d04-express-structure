# Palettes Controller
```js 
var express = require('express');
var router = express.Router();
```

## Required Modules
```js 
var palette = require('../models/palette');
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
#### renderShow - renders the palettes id
- mustacheVariables: 
```js
mustacheVariables = {
  palettes: res.locals.palettes
}
```
- view: `./palettes/show`
---

#### renderEdit - renders to edit the palette

- mustacheVariables: 
```js
mustacheVariables = {
  palettes: res.locals.palettes
}
```
- view: `./palettes/edit`

---

#### renderNew - add new palette

- mustacheVariables: `no need`

- view: `./palettes/new`

---

USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:

---
#### redirectIndex - redirects to the list of palettes 

- redirect_url: `/palettes`
---

#### redirectShow - redirects to the palette id

- redirect_url: `/palettes/${res.locals.palette_id}`

---

## Exports
```js 
module.exports = router;
```