<!-- USE THE PALETTES CONTROLLER AS REFERENCE -->

var express = require('express');
var router = express.Router();
var colors = require('./models/palette');

router.get('/new', renderNew);
router.get('/:id/edit', colors.find, renderEdit);
router.get('/:id', colors.find, renderShow);
router.get('/', colors.getAll, renderIndex);
router.delete('/:id', color.delete, redirectIndex);
router.post('/palletes/:pallete_id/colors', color.create, redirectShow);
router.put('/:id', color.update, redirectShow);


var colorsController = require('./colorsController');
router.use('/:palette_id/colors', palette.find, colorsController);

function renderSomething(req, res){
  var mustacheVariables = {
    key: res.locals.data
  }
  res.render('./something', mustacheVariables)
}

function redirectSomewhere(req, res){
  res.redirect('path/to/redirect')
}
renderShow(req,res){
  var mustacheVariables = res.locals.color
  res.render('./color/show', mustacheVariables);

unction renderIndex(req,res){
- mustacheVariables: 

mustacheVariables = {
  colors: res.locals.colors

module.exports= router;