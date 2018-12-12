# Database Seeds

- Drop Database 
DROP DATABASE IF EXISTS color_db;

- Create Database 
CREATE DATABASE color_db;

- Connect to Database 
\c color_db
- Create Tables 

CREATE TABLE table(
  id serial primary key, 
  color1  varchar, 
  color2 varchar, 
  color3 varchar,
  color4 varchar
);

CREATE TABLE color(
  id serial primary key, 
  color1  varchar, 
  color2 varchar, 
  color3 varchar,
  color4 varchar
);


- Insert data into tables 
INSERT INTO table(color1, color2, color3, color4) VALUES('red', 'blue', black', 'white');
INSERT INTO color(color1, color2, color3, color4) VALUES('red', 'blue', black', 'white');


## To run:
```
psql -f db/seed.sql 
```