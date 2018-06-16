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

## Queries
### Query caluses
| Clause name | Purpose |
| --- | --- |
| Select | Determines what columns to include in the result |
| From | Identifies the tables from which to draw data and how the tables are joined |
| Where | Filters unwanted data |
| Group by | Groups rows together by common column value |
| Having | Filters out unwanted groups |
| Order by | Sorts resulting rows by one or more columns |

Select clause can include:
- Literals.
- Expressions.
- Function calls.
### Select clause
#### eg:
```sql
SELECT emp_id, 'ACTIVE', emp_id * 3.14159, UPPER(lname)
  FROM employee;
```
| emp_id | ACTIVE | emp_id * 3.14159 | UPPER(lname) |
| ------ | ------ | ---------------- | ------------ |
|      1 | ACTIVE |          3.14159 | SMITH        |
|      2 | ACTIVE |          6.28318 | BARKER       |
|      3 | ACTIVE |          9.42477 | TYLER        |
|      4 | ACTIVE |         12.56636 | HAWTHORNE    |
|      5 | ACTIVE |         15.70795 | GOODING      |
|      6 | ACTIVE |         18.84954 | FLEMING      |
|      7 | ACTIVE |         21.99113 | TUCKER       |
|      8 | ACTIVE |         25.13272 | PARKER       |
|      9 | ACTIVE |         28.27431 | GROSSMAN     |
|     10 | ACTIVE |         31.41590 | ROBERTS      |
|     11 | ACTIVE |         34.55749 | ZIEGLER      |
|     12 | ACTIVE |         37.69908 | JAMESON      |
|     13 | ACTIVE |         40.84067 | BLAKE        |
|     14 | ACTIVE |         43.98226 | MASON        |
|     15 | ACTIVE |         47.12385 | PORTMAN      |
|     16 | ACTIVE |         50.26544 | MARKHAM      |
|     17 | ACTIVE |         53.40703 | FOWLER       |
|     18 | ACTIVE |         56.54862 | TULMAN       |

#### Using functions we can skip the from clause
```sql
SELECT VERSION(), USER(), DATABASE();
```
| VERSION() | USER()            | DATABASE() |
| - | - | - |
| 8.0.11    | lrngsql@localhost | bank       |

#### Aliasing column names
```sql
SELECT emp_id AS ID, 'ACTIVE' AS status, emp_id * 3.14159 AS IDxPI, UPPER(lname) AS last_name
  FROM employee;
```
| ID | status | IDxPI    | last_name |
| - | - | - | - |
|  1 | ACTIVE |  3.14159 | SMITH     |
|  2 | ACTIVE |  6.28318 | BARKER    |
|  3 | ACTIVE |  9.42477 | TYLER     |
|  4 | ACTIVE | 12.56636 | HAWTHORNE |
|  5 | ACTIVE | 15.70795 | GOODING   |
|  6 | ACTIVE | 18.84954 | FLEMING   |
|  7 | ACTIVE | 21.99113 | TUCKER    |
|  8 | ACTIVE | 25.13272 | PARKER    |
|  9 | ACTIVE | 28.27431 | GROSSMAN  |
| 10 | ACTIVE | 31.41590 | ROBERTS   |
| 11 | ACTIVE | 34.55749 | ZIEGLER   |
| 12 | ACTIVE | 37.69908 | JAMESON   |
| 13 | ACTIVE | 40.84067 | BLAKE     |
| 14 | ACTIVE | 43.98226 | MASON     |
| 15 | ACTIVE | 47.12385 | PORTMAN   |
| 16 | ACTIVE | 50.26544 | MARKHAM   |
| 17 | ACTIVE | 53.40703 | FOWLER    |
| 18 | ACTIVE | 56.54862 | TULMAN    |

**AS** keyword can be omitted.

#### Removing duplicates
```sql
SELECT DISTINCT cust_id
  FROM account;
```
### From clause
#### Subquery-generated tables
```sql
SELECT e.emp_id, e.fname, e.lname
  FROM (SELECT emp_id, fname, lname, start_date, title
        FROM employee) e;
```
| emp_id | fname    | lname     |
| - | - | - |
|      1 | Michael  | Smith     |
|      2 | Susan    | Barker    |
|      3 | Robert   | Tyler     |
|      4 | Susan    | Hawthorne |
|      5 | John     | Gooding   |
|      6 | Helen    | Fleming   |
|      7 | Chris    | Tucker    |
|      8 | Sarah    | Parker    |
|      9 | Jane     | Grossman  |
|     10 | Paula    | Roberts   |
|     11 | Thomas   | Ziegler   |
|     12 | Samantha | Jameson   |
|     13 | John     | Blake     |
|     14 | Cindy    | Mason     |
|     15 | Frank    | Portman   |
|     16 | Theresa  | Markham   |
|     17 | Beth     | Fowler    |
|     18 | Rick     | Tulman    |

#### Views
Virtual tables with no data associated.
```sql
CREATE VIEW employee_vw AS
  SELECT emp_id, fname, lname, YEAR(start_date) start_year
  FROM employee;
```
Can be viewed as an aliased SELECT statement.
```sql
SELECT emp_id, start_year
  FROM employee_vw;
```
| emp_id | start_year |
| - | - |
|      1 |       2001 |
|      2 |       2002 |
|      3 |       2000 |
|      4 |       2002 |
|      5 |       2003 |
|      6 |       2004 |
|      7 |       2004 |
|      8 |       2002 |
|      9 |       2002 |
|     10 |       2002 |
|     11 |       2000 |
|     12 |       2003 |
|     13 |       2000 |
|     14 |       2002 |
|     15 |       2003 |
|     16 |       2001 |
|     17 |       2002 |
|     18 |       2002 |

#### Table links
