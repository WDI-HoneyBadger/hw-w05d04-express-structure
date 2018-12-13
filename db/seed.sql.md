# Database Seeds

- Drop Database 
- Create Database 
- Connect to Database 
- Create Tables 
- Insert data into tables 

## To run:
```
psql -f db/seed.sql 

```

```sql

DROP DATABASE IF EXISTS palettes_db;
CREATE DATABASE palettes_db;
\c palettes_db
CREATE TABLE palettes(palette_id serial primary key, name varchar, description text);
CREATE TABLE colors(color_id serial primary key, name varchar, bgcolor text);
INSERT INTO palettes(name, description) VALUES  ('Rainbow', 'All colors of the rainbow') ; 
INSERT INTO palettes(name, description) VALUES ('Blues', 'Colors of the sky and sea') ;
INSERT INTO palettes(name, description) VALUES  ('Grey', 'just greys') ;
INSERT INTO colors(name, bgcolor) VALUES ('yellow','#FFFF00') ; 
```