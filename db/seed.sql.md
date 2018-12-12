# Database Seeds

- Drop Database 
DROP DATABASE IF EXISTS  db ;
- Create Database 
CREATE DATABASE db ;
- Connect to Database 
\c todo_db;
- Create Tables 
CREATE TABLE db (
    id SERIAL ,

- Insert data into tables 
INSERT INTO db (name, definition) VALUES
('play soccer', 'with my friends in jeddah'),
('watch movie', 'with my family'),
('visting', 'my mom');


## To run:
```
psql -f db/seed.sql 
```