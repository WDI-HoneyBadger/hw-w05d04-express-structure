USE THE PALETTES CONTROLLER AS REFERENCE
var express = require('express');
var router = express.Router();

var colors =  require('../models/color');


router.get('/', colors.getAll, renderIndex);
router.get('/new', renderNew);
router.get('/:id/edit', colors.find, renderEdit);
router.get('/:id', colors.find, renderShow);


router.delete('/:id', colors.delete, redirectIndex);
router.post('/', colors.create, redirectShow);
router.put('/:id', colors.update, redirectShow);


function redirectIndex(req, res) {
  res.redirect('/colors');
}

function redirectShow(req, res) {
  res.redirect(`/colors/${res.locals.data_id}`);
}

function renderEdit(req, res) {
  var mustacheVariables = res.locals.color

  res.render('./colors/edit', mustacheVariables);
}


function renderIndex(req, res){
  var mustacheVariables = {
    color: res.locals.color
  }
 res.render("./palettes/index', mustacheVariables);
}

function renderShow(req, res){
  // res.send(res.locals.color);
  var mustacheVariables = res.locals.color
  res.render('./colors/show', mustacheVariables);
}

function renderNew(req, res){
  res.render('./colors/new')
}

module.exports = router;