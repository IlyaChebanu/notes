## Setting up bank database

```
$ mysql -u root -p
CREATE DATABASE bank;
CREATE USER 'lrngsql'@'localhost' IDENTIFIED BY 'password';
GRANT ALL ON bank.* TO 'lrngsql'@'localhost';
QUIT;
$ mysql -u lrngsql -p
USE bank;
```
