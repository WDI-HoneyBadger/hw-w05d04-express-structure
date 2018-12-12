## Required Modules
PUT YOUR REQUIRED MODULES AND PACKAGES HERE
 var express = require('express');
var router = express.Router();
var Palette = require('../models/palette');
 ## Routes 
Routes tell our app what to do when a request is made to a certain path. The basic structure of a route is as follows:
```js 
router.method('path', middleWare1, middleWare2);
```
### Routes needed for this controller:
```js 
router.get('/', palette.getAll, renderIndex);
PUT THE ROUTES NEEDED FOR THIS CONTROLLER HERE
router.get('/', Palette.getAll, renderIndex);
router.get('/new', renderNew);
router.get('/:id', Palette.find, renderShow);
router.get('/:id/edit', Palette.find, renderEdit);
router.post('/', Palette.create,redirectShow;
router.delete('/:id', Palette.deleterenderShow);
router.put('/:id', Palette.update,renderShow;
```
You can also import other controllers that go off of the same paths. For this controller the base is `/palettes` The colors controller is going to have a base of `/palettes/:palette_id/colors` we can therefore do the following:
```js
 function redirectSomewhere(req, res){
 USE THE FOLLOWING TEMPLATE FOR EACH RENDER:
 function renderShow(req,res){
  mustacheVariables = res.locals.Palette;
  res.render('./Palette/show', mustacheVariables);
}
 function renderNew(req, res){
  res.render('./Palette/new');
}
 function renderEdit(req, res){
    mustacheVariables = {
      Palette: res.locals.Palette
    }
    console.log(mustacheVariables)
    res.render('./Palette/edit', mustacheVariables);
  }
 ---
#### renderIndex - renders all of the palettes
#### renderIndex - renders all of the Palettes
- mustacheVariables: 
```js
mustacheVariables = {
  palettes: res.locals.palettes
 function renderIndex(req, res){
  mustacheVariables = {
    Palette: res.locals.Palette
  }
  console.log(mustacheVariables)
  res.render('./Palette/index', mustacheVariables);
}
 ```
- view: `./palettes/index`
- view: `./Palettes/index`
 ---
 USE THE FOLLOWING TEMPLATE FOR EACH REDIRECT:
 ---
 
---

 module.exports = router;