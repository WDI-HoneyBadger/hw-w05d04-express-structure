# Database Seeds

- Drop Database 
```
DROP DATABASE IF EXISTS data_db;
```
- Create Database 
```
CREATE DATABASE data_db;
```
- Connect to Database 
```
\c data_db
```
- Create Tables 
```
CREATE TABLE app(
  id serial primary key, 
  coulom1  varchar, 
  coulom2 varchar, 
  coulom3 varchar
 
);
```
- Insert data into tables 
```
INSERT INTO app(coulom1, coulom2, coulom3) VALUES
( 'row1 value 1' , 'row1 value 2','row1 value 3'),
( 'row2 value 1' , 'row2 value 2','row2 value 3'),
( 'row3 value 1' , 'row3 value 2','row3 value 3');
```
## To run:
```
psql -f db/seed.sql 
```