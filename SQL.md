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
  postaal_code VARCHAR(20),
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
