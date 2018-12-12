# Database Seeds

- Drop Database
 DROP DATABASE IF EXISTS cp_db;
- Create Database 
 CREATE DATABASE cp_db;
- Connect to Database 
\c CREATE DATABASE cp_db;
- Create Tables 
CREATE TABLE cp(id serial primary key, first varchar, last varchar);
- Insert data into tables 
INSERT INTO cp (fgh, fghj) VALUES ('tttt', 'mmmm');



## To run:
```
psql -f db/seed.sql 
```