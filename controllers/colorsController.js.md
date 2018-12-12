# color Controller
```js 
var express = require('express');
var router = express.Router();
```
## Required Modules
```js 
var  color = require('../models/color');
``` 

## Routes 

```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 
router.get('/', color.getAll, renderIndex);
router.get('/new', renderNew);
router.get('/:color_id/edit', color.find, renderEdit);
router.get('/:color_id', color.find , renderShow);
router.post('/',color.create, redirectShow);
router.delete('/:color_id', color.delete , redirectIndex);
router.put('/:color_id', color.update , redirectShow)
```




### Middleware needed for this controller:

#### renderIndex - renders all of the color

- mustacheVariables: 
```js
mustacheVariables = {
 color: res.locals.colors
}
```
- view: `./palettes/show`

---

#### renderShow - renders the color id

- mustacheVariables: 
```js
mustacheVariables = {
  color: res.locals.colors
}
```
- view: `./colors/show`
---

#### renderEdit - renders to edit the color

- mustacheVariables: 
```js
mustacheVariables = {
    color: res.locals.colors
}
```
- view: `./colors/edit`

---

#### renderNew - add new color

- mustacheVariables: `no need`

- view: `./colors/new`


---
#### redirectIndex - redirects to the list of colors

- redirect_url: `/colors`
---

#### redirectShow - redirects to the color id

- redirect_url: `/color/${res.locals.color_id}`

---

## Exports
```js 
module.exports = router;
```