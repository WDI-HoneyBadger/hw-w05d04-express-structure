# Database Seeds

- Drop Database 
DROP DATABASE IF EXISTS color;
- Create Database 
CREATE DATABASE color_db;

- Connect to Database 
\c color_db 

- Create Tables 
CREATE TABLE color(
  id serial PRIMARY KEY,
  subject VARCHAR,
  content VARCHAR
);
- Insert data into tables 
INSERT INTO todo(subject, content) VALUES
('read', 'red'),
('yalo', 'yalo'),
('black', 'black'),
('white', 'white');

## To run:
```
psql -f db/seed.sql 
```



