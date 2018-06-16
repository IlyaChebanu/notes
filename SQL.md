### Setting up bank database

```sql
$ mysql -u root -p
CREATE DATABASE bank;
CREATE USER 'lrngsql'@'localhost' IDENTIFIED BY 'password';
GRANT ALL ON bank.* TO 'lrngsql'@'localhost';
quit;
$ mysql -u lrngsql -p
use bank;
```

### Opening a file
```sql
source c:\...\*.sql
```

### Data types
char(n) - if every string is the same length (255 bytes max)

varchar(n) - variable length strings (65535 bytes max)

tinytext - 255 bytes max

text - 65535 bytes max

mediumtext - 16777215 bytes max

longtext - 4294967295 bytes max

### Listing character sets
```sql
show character set;
```

### Choosing character sets
```sql
varchar(20) character set utf8
```

### Setting default character set
```sql
create database foreign_sales character set utf8;
```

## Schema
### Person table
```sql
CREATE TABLE person
  (person_id SMALLINT UNSIGNED,
  fname VARCHAR(20),
  lname VARCHAR(20),
  gender ENUM('M','F'), /* gender CHAR(1) CHECK (gender IN ('M', 'F')), */
  birth_date DATE,
  street VARCHAR(30),
  city VARCHAR(20),
  state VARCHAR(20),
  country VARCHAR(20),
  postal_code VARCHAR(20),
  CONSTRAINT pk_person PRIMARY KEY (person_id)
  );
```
### Food table
```sql
CREATE TABLE favourite_food
  (person_id SMALLINT UNSIGNED,
  food VARCHAR(20),
  CONSTRAINT pk_favourite_food PRIMARY KEY (person_id, food),
  CONSTRAINT fk_fav_food_person_id FOREIGN KEY (person_id) 
    REFERENCES person (person_id)
  );
```
Foreign key contrains the values of person_id column in favourite_food table to include only values found in the person table.
### Update person_id PK
Must drop favourite_food foreign key else
```ERROR 1833 (HY000): Cannot change column 'person_id': used in a foreign key constraint 'fk_fav_food_person_id' of table 'bank.favourite_food'``` appears trying to alter person table to add auto_increment
```sql
LOCK TABLES
  favourite_food WRITE,
  person WRITE;
  
ALTER TABLE favourite_food 
  DROP FOREIGN KEY fk_fav_food_person_id;

ALTER TABLE person
  MODIFY person_id SMALLINT UNSIGNED AUTO_INCREMENT; /* Adding auto_increment */
  
ALTER TABLE favourite_food
  ADD CONSTRAINT fk_fav_food_person_id FOREIGN KEY (person_id)
    REFERENCES person (person_id);

UNLOCK TABLES;
```
### Renaming column
```sql
ALTER TABLE person
  RENAME COLUMN postaal_code TO postal_code;
```
## Data
### INSERT
```sql
INSERT INTO person
  (person_id, fname, lname, gender, birth_date)
  VALUES (null, 'William', 'Turner', 'M', '1972-05-27');
  
INSERT INTO favourite_food
  (person_id, food)
  VALUES (1, 'pizza');


INSERT INTO favourite_food
  (person_id, food)
  VALUES (1, 'cookies');


INSERT INTO favourite_food
  (person_id, food)
  VALUES (1, 'nachos');
  
INSERT INTO person
  (person_id, fname, lname, gender, birth_date, street, city, state, country, postal_code)
  VALUES (null, 'Susan', 'Smith', 'F', '1975-11-02', '23 Maple St.', 'Arlington', 'VA', 'USA', '20220');
```
### SELECT
```sql
SELECT food
  FROM favourite_food
  WHERE person_id = 1
  ORDER BY food;
  
SELECT person_id, fname, lname, birth_date FROM person;
```
### UPDATE
```sql
UPDATE person
  SET street = '1225 Tremont St.',
    city = 'Boston',
    state = 'MA',
    country = 'USA',
    postal_code = '02138'
  WHERE person_id = 1;
```
### DELETE
```sql
DELETE FROM person
  WHERE person_id = 2;  
```
### str_to_date function
```sql
UPDATE person
  SET birth_date = str_to_date('DEC-21-1980', '%b-%d-%Y')
  WHERE person_id = 1;
```
| Formatters | Description |
| ---------- | ----------- |
| %a | Short weekday eg. Sun, Mon.. |
| %b | Short month eg. Jan, Feb... |
| %c | Numeric month (0..12) |
| %d | Numeric day (0..31) |
| %f | Number of microseconds (000000..999999) |
| %H | Hour 24h format (00..23) |
| %h | Hour 12h format (01..12) |
| %i | Minutes within hour (00..59) |
| %j | Day of the year (001..365) |
| %M | Full month name (January..December) |
| %m | Numeric month |
| %p | AM / PM |
| %s | Number of seconds (00..59) |
| %W | Full weekday name (Sunday..Saturday) |
| %w | Numeric day of the week (0=Sunday..6=Saturday) |
| %Y | Four digit year (YYYY) |

