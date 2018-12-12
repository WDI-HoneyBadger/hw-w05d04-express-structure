# Database Seeds

INSERT INTO todo(subject, content) VALUES
('buy pickles', 'go to the fancy pickle store on the corner'),
('pet a dog', 'only if it is cute though'),
('code a todo list', 'currently working on it'),
('homework', 'they are gonna hate this');
- Drop Database 
DROP DATABASE IF EXISTS colors_db
DROP DATABASE IF EXISTS pallete_db;
- Create Database 

- Connect to Database 
\c colors_db
\c pallete_db
- Create Tables 

CREATE TABLE palette(
  id serial PRIMARY KEY,
  p_row1 VARCHAR,
  p_row2 VARCHAR
);

CREATE TABLE colors(
  id serial PRIMARY KEY,
  c_row1 VARCHAR,
  c_row2 VARCHAR,
  FOREIGN KEY(pallete_id) REFERENCES pallete(id)
);
- Insert data into tables 
INSERT INTO palette(p_row1, p_row2) VALUES
('value1','value2'),
('value3','value4'),
('value5','value6');

INSERT INTO colors(c_row1, c_row2) VALUES
('value1','value2'),
('value3','value4'),
('value5','value6');

## To run:
```
psql -f db/seed.sql 
```