# Apartment lab

- Create a database called apartmentlab 
``` 
CREATE DATABASE apartmentlab;
``` 
- Using this database, create two tables, one for owners and one for properties
``` 
CREATE TABLE owners(owner_id SERIAL PRIMARY KEY, name VARCHAR(10), age INTEGER NOT NULL);

CREATE TABLE properties(property_id SERIAL PRIMARY KEY, name VARCHAR(10), units INTEGER NOT NULL, owner_id INTEGER NOT NULL);

ALTER TABLE properties ADD CONSTRAINT owner_fk FOREIGN KEY (owner_id) REFERENCES owners (owner_id) ON DELETE NO ACTION;
``` 
- Keep this relationship in mind when designing your schema:
  + **One owner can have many properties**

###Tables

- The owners table should consist of: 
  + owner_id (this should be the primary key as well as a unique number that increments automatically)
  + name
  + age
- The properties table should consist of:
  + property_id (this should be the primary key as well as a unique number that increments automatically)
  + name
  + number of units
  + owner_id (this should have the constraint NOT NULL)
    + There should be also be a foreign key that references the owners table

###Questions
Write down the following sql statements that are required to solve the following tasks.

  
Show all the tables.
```  
SELECT * FROM owners, properties;
```  
```
/dt
```

Show all the users. 

```
/dg
```
```
/du
```

Show all the data in the owners table.
```
SELECT * FROM owners;
```
Show the names of all owners. 
```
SELECT * FROM owners;
```

Show the ages of all of the owners in ascending order. 
```
SELECT * FROM owners ORDER BY first_name ASC;
```

Show the name of an owner whose name is Donald. 
```
SELECT * FROM owners WHERE name='Donald';
```

Show the age of all owners who are older than 30.
```
SELECT * FROM owners WHERE age > 30;
```

Show the name of all owners whose name starts with an E.
```
SELECT * FROM owners WHERE name='E%';
```

Add an owner named John who is 33 years old to the owners table.
```
INSERT INTO owners (name, age) VALUES ('John', 33); 
```

Add an owner named Jane who is 43 years old to the owners table. 
```
INSERT INTO owners (name, age) VALUES ('Jane', 33); 
```

Change Jane's age to 30. 
```
UPDATE owners SET age='30' WHERE age='43';
```

Change Jane's name to Janet. 
```
UPDATE owners SET name='Janet' WHERE name='Jane';
```

Add a property named Archstone that has 20 units. 
```
INSERT INTO properties (name, units, owner_id) VALUES ('Archstone', 20, 1);
```

Delete the owner named Jane.
```
DELETE FROM owners WHERE name='Jane';
```

Show all of the properties in alphabetical order that are not named Archstone and do not have an id of 3 or 5.
```
SELECT * FROM properties WHERE name NOT LIKE 'Archstone'AND property_id NOT IN (3,5) ORDER BY name ASC;
```

 
Count the total number of rows in the properties table.
```
SELECT COUNT(*) properties;
```


Show the highest age of all owners.
```
SELECT MAX(age) FROM owners;
```


Show the names of the first three owners in your owners table.
```
SELECT * FROM owners LIMIT 3 OFFSET 1;
```


Create a foreign key that references the owner_id in the owners table and forces the constraint ON DELETE NO ACTION.
```
ALTER TABLE properties ADD CONSTRAINT owner_fk FOREIGN KEY (owner_id) REFERENCES owners (owner_id) ON DELETE NO ACTION;
```

Show all of the information from the owners table and the properties table in one joined table.  
```
SELECT * FROM owners JOIN properties ON owners.owner_id=properties.owner_id;
```



###Bonus

In the properties table change the name of the column "name" to "property_name". 
```
ALTER TABLE properties RENAME COLUMN name to property_name;
```

Count the total number of properties where the owner_id is between 1 and 3.
```
SELECT COUNT(*) FROM properties WHERE owner_id > 0 AND owner_id < 4;
```
