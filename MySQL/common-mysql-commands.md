# Common MySQL Commands

Below are some common MySQL commands from the Command Line.

Create a database

```
CREATE DATABASE databasename;
```

Usa a database

```
USE databasename;
```

Review all databases on server

```
SHOW databases;
```

Create a new user on localhost

```
CREATE USER 'username'@'localhost' IDENTIFIED BY 'userpassword';
```

Remove a user 

```
DROP USER 'jeffrey'@'localhost';
```

Grant user all priveleges

```
GRANT ALL ON databasename.* TO 'username'@'localhost';
```

Rename a user

```
RENAME USER 'username'@'localhost' TO 'newusername'@'127.0.0.1';
```