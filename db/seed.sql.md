# Database Seeds

- Drop Database 
`DROP DATABASE IF EXISTS express_structure;`
- Create Database 
`CREATE DATABASE express_structure;`
- Connect to Database 
`\c express_structure`
- Create Tables 
```
CREATE TABLE palette (
id serial PRIMARY KEY,
name VARCHAR,
description VARCHAR
);
```
```
CREATE TABLE colors (
id serial PRIMARY KEY,
name VARCHAR,
description VARCHAR,
FOREIGN KEY (palete_id) REFERENCES palette(id)
);
```
- Insert data into tables 
```
INSERT INTO palette(name,description) VALUES('Rainbow','All tha colors of the rainbow!');
INSERT INTO colors(name,description,palete_id) VALUES('Red','#FF0000',1),
('Graen','#008000',1),
('Yellow','#FFFF00',1);
```

## To run:
```
psql -f db/seed.sql 
```