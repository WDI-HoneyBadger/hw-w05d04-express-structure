# Database Seeds

- Drop Database 
DROP DATABASE IF EXISTS colorPalettes_db;
- Create Database
CREATE DATABASE colorPalettes_db;
- Connect to Database 
\c colorPalettes_db 
- Create Tables 

CREATE TABLE color(
  id serial PRIMARY KEY,
  subject VARCHAR,
  content VARCHAR
);
 CREATE TABLE palettes(
  id serial PRIMARY KEY,
  subject VARCHAR,
  content VARCHAR
);

- Insert data into tables 

INSERT INTO color(subject, content) VALUES
('ranibow', 'all the colors of the rainbow'),
('gey', 'just'),
('blue', 'colors of the sky and sea'),


<!-- 
INSERT INTO palettes(subject, content) VALUES
('****************', '£££££££££££ '),
('****************', '£££££££££££ '),
('****************', '£££££££££££ '),
('****************', '£££££££££££ '),

## To run:
```
psql -f db/seed.sql 
```