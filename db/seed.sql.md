# Database Seeds


Seed.sql initialize the database and gives it data – reseed data 


- Drop Database 

DROP DATABASE IF EXISTS palette;
- Create Database 

CREATE DATABASE palette;


CREATE DATABASE palette;
 
- Connect to Database 

\c todo_db 

- Create Tables 


CREATE TABLE pelettes(
  id serial PRIMARY KEY,
  color VARCHAR,
  content VARCHAR
);


- Insert data into tables 


INSERT INTO tablename (color, content) VALUES
('grey', 'this is the colorrrrrt'),


## To run:
```
psql -f db/seed.sql 
```


