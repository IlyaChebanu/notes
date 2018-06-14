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
