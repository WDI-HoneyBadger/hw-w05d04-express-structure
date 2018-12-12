# Database Seeds

- Drop Database 

DROP DATABASE IF EXISTS color_list;

- Create Database 
CREATE DATABASE color_list;

- Connect to Database 
\c color_list
- Create Tables 

CREATE TABLE colors(
  id serial primary key, 
  name varchar, 
  description varchar, 
);


- Insert data into tables 
INSERT INTO colors(name, description ) VALUES
('',''),
('',''),
('','')


```
psql -f db/seed.sql 
```