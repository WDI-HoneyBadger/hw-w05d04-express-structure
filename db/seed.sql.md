# Database Seeds
```sql 

- Drop Database 
DROP DATABASE color_db
- Create Database 
CREATE DATABASE 
- Connect to Database 
c/ color_db

- Create Tables

CREATE TABLE pallette
CREATE TABLE colors
- Insert data into tables 
INSERT INTO pallette (
id serial primary key,
name varchar,
description varchar)VALUE ('rainbow','all color') ('gray','just gray')( 'blues','just blue');


INSERT INTO colors (
id serial primary key,
name varchar,
bgcolor varchar,
pallette_id ,
) VALUE ('#b8bbc1', 1),
('#72767c', 1),
('#3b3f44', 1),
('#4286f4', 2),
('#204b8e', 2),
('#0e5bd6', 2),
('#7a7a7a', 0),
('#204b8e', 0),
('#0e5bd6', 0)
; 


## To run:
```
psql -f db/seed.sql 
```
```