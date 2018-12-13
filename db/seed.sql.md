# Database Seeds

- Drop Database 
```js
DROP DATABASE IF EXISTS colors_paletteDB;
```
- Create Database
```js
CREATE DATABASE colors_paletteDB;
``` 
- Connect to Database 
```js
\c CREATE DATABASE colors_paletteDB;
```
- Create Tables 
```js
CRAETE TABLE colors (
    id SERIAL PRIMARY KEY,
    color_name VARACHAR 
)

```
- Insert data into tables 
```js
INSER INTO colors (color_name) VALUES
('Red'),
('Orange'),
('Yellow'),
('Green'),
('Light Blue'),
('Blue'),
('Purpel'),
('Pink'),

CREATE TABLE palette (
    id SERIAL PRIMARY KEY,
    palette_name VARACHA
)

INSERT INTO palette( palette_name) VALUES
(''),
```

## To run:
```
psql -f db/seed.sql 
```