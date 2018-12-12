var db = require('../db/config');
var palette = {};


palette.getAll = function(req, res, next){
  db.manyOrNone(`SELECT * FROM table;`)
    .then(function(result){
      res.locals.palette = result;
      next();
    })
    .catch(function(error){
      console.log(error);
      next();
    })
};

palette.find = function (req, res, next) {
    db.oneOrNone("SELECT * FROM table WHERE id = $1;", [req.params.id])
      .then(function(result){
        res.locals.palette = result;
        next();
      })
      .catch(function(error){
        console.log(error);
        next();
      });
};

palette.create = function(req, res, next){
    connection.one("INSERT INTO table(color1, color2, color3, color4) VALUES($1, $2, $3, $4) RETURNING id;", [req.body.color1, req.body.color2, req.body.color3, req.body.color4])
    .then(function(result){
        res.locals.palette_id = result.id;
        next();
    }).catch(function(error){
        console.log(error);
        next();
    })
};

palette.delete = function(req, res, next){
    connection.none("DELETE FROM table WHERE id=$1;", [req.params.id])
    .then(function(){
        next();
    }).catch(function(error){
        console.log(error);
    });
};

palette.update = function(req, res, next){
    connection.one("UPDATE table SET color1=$1, color2=$2, color3=$3, color4=$4 WHERE id=$5 RETURNING id;", [req.body.color1, req.body.color2, req.body.color3, req.body.color4, req.params.id])
    .then(function(result){
        res.locals.palette_id = result.id;
        next();
    }).catch(function(error){
        console.log(error);
    });
};

module.exports = palette;