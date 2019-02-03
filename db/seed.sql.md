# Database Seeds

- Drop Database 
```js
DROP DATABASE IF EXISTS colorsPalettes_db;
```
- Create Database 
```js
CREATE DATABASE colorsPalettes_db;
```
- Connect to Database 
\c colorsPalettes_db
- Create Tables 
```js
CREATE TABLE palettes(id serial primary key, name varchar, explanation text);
CREATE TABLE  colors(id serial primary key, name varchar, palette_id INT, FOREIGN KEY ( palette_id)
```
- Insert data into tables 
```js
INSERT INTO palettes (name, explanation) VALUES ('Rainbow', 'All colors of the rainbow') ;
INSERT INTO palettes (name, explanation) VALUES ('Grey', 'just greys') ;
INSERT INTO palettes (name, explanation) VALUES ('Blues', 'Colors of the sky and sea') ;

INSERT INTO colors (name) VALUES ('red') ;
INSERT INTO colors (name) VALUES ('blue');
INSERT INTO colors (name) VALUES ('yellow');
```
## To run:
```
psql -f db/seed.sql 
```


