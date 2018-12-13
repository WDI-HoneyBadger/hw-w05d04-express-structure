# Database Seeds

- Drop Database 
DROP DATABASE IF EXISTS data_db;

- Create Database 
CREATE DATABASE data_db;

- Connect to Database 
\c data_db 

- Create Tables 
CREATE TABLE data(
  id serial PRIMARY KEY,
  name VARCHAR,
  color VARCHAR
);
- Insert data into tables 
INSERT INTO data(name, color) VALUES
('grey', 'just grey'),
('pet a dog', 'only if it is cute though'),
('blue', 'colors of the sky and sea'),
('yellow', 'colors of the snow');
- Create Tables 
CREATE TABLE data(
  id serial PRIMARY KEY,
  name VARCHAR,
  color VARCHAR
);
- Insert data into tables 
INSERT INTO data(name, color) VALUES
('grey', 'just grey'),
('pet a dog', 'only if it is cute though'),
('blue', 'colors of the sky and sea'),
('yellow', 'colors of the snow');
## To run:
```
psql -f db/seed.sql 
```