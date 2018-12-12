# Database Seeds

- Drop Database 
- Create Database 
- Connect to Database 
- Create Tables 
- Insert data into tables 

DROP DATABASE IF EXISTS database_name;

CREATE DATABASE database_name;
\c database_name

CREATE TABLE table_name (id serial primary key, name varchar, name2 varchar, name3 varchar, phone_number integer);


INSERT INTO cheeses (name, color, origin, stink_level) VALUES
(),
(),
(),
();


## To run:
```
psql -f db/seed.sql 
```