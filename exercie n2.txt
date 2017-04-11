mysql-ctl start
mysql -u nickoog

source data/import-table-structure.sql

show databases;

use decodemtl_addressbook_import;

INSERT INTO Account(email, password, createdOn, modifiedOn)
VALUES
("nico.h@gmail.com", "0000", "04-04-2017", "10-04-2017");

INSERT INTO AddressBook(accountId, name, createdOn, modifiedOn)
VALUES
("1", "jojo", "04-04-2017", "10-04-2017");

INSERT INTO Entry(addressBookId, firstName, lastName, birthday, type, subtype)
VALUES
("1", "jojo", "leterrible", "23-09-1956", "1", "2");
    
UPDATE Account 
SET createdOn = "2017-04-01"
WHERE ID = 1;

UPDATE AddressBook
SET modifiedOn = "2017-04-10"
WHERE ID = 1;
    
UPDATE Entry
SET addressBookId = "1", firstName = "Nono", lastName = "pastresterrible"
WHERE ID = 1;

TRUNCATE Entry;

DROP TABLE Account;

SOURCE data/import-table-structure.sql;
SOURCE data/import-account.sql;
SOURCE data/import-addressbook.sql;
SOURCE data/import-entry.sql;

USE decodemtl_addressbook_import

SELECT email 
FROM Account 
WHERE id=63;

SELECT name
FROM AddressBook
WHERE accountId=3;

SELECT createdOn 
FROM AddressBook 
WHERE name = "Lorem Foundation";

SELECT COUNT(*)
FROM Account;

SELECT COUNT(*)
FROM AddressBook;

SELECT COUNT(*)
FROM Entry;

SELECT COUNT(*) 
FROM Entry 
WHERE birthday < '1982-12-02';

SELECT COUNT(*)
FROM Entry
WHERE birthday >= '1965-01-01';

SELECT *
FROM Entry
WHERE (SELECT MIN(birthday) FROM Entry);

SELECT * 
FROM Entry 
ORDER BY birthday LIMIT 1;

SELECT COUNT(*) 
FROM Entry 
WHERE type != "other";

SELECT COUNT(*) 
FROM Entry 
WHERE type != "home" OR "work";

SELECT COUNT(*)
FROM Entry
WHERE subtype = 'phone';
