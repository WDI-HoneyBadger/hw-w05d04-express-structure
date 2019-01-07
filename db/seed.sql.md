# Database Seeds

- Drop Database ```js DROP DATABASE IF EXISTS express_structure;```
- Create Database 
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


## To run:
```
psql -f db/seed.sql 
```