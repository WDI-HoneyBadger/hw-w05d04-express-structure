# Database Seeds

- Drop Database DROP DATABASE IF EXISIST color-list;
- Create Database CREATE DATABASE color-list;
- Connect to Database \c color-list
- Create Tables CREATE TABLE colors(id SERIAL PRIMARY KEY, name VARCHAR(10),description VARCHAR(255));
- Insert data into tables INSERT INTO colors (name,description) VALUES (" "," ");

## To run:
```
SELECT * FROM colors;
psql -f db/seed.sql 
```