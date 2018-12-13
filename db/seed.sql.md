# Database Seeds

- Drop Database 
DROP DATABASE IF EXISTS db_color;
- Create Database
CREATE DATABASE db_color;
- Connect to Database 
\c db_color
- Create Tables 
CREATE TABLE colors(
  id SERIAL PRIMARY KEY,
  name VARCHAR,
  cmyk VARCHAR(9),
  palette_id
);

CREATE TABLE palettes(
  id SERIAL PRIMARY KEY,
  name VARCHAR,
  description VARCHAR
);


- Insert data into tables 

INSERT INTO colors(name, cmyk) VALUES ('firebrick','#b22222'),
('white','#ffffff');

INSERT INTO palettes(name, description) VALUES ('grey','#greish colors'), ('rainbow','rinbow colors');




## To run:
```
psql -f db/seed.sql 
```

