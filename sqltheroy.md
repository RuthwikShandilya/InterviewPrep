Clustered vs Non Clustered Index:
https://www.youtube.com/watch?v=xeoLwQmTO4o

https://www.youtube.com/watch?v=ITcOiLSfVJQ

Clustered Index vs Non Clustered Index :

The main difference between clustered and non clustered index is in clustered index the values are sorted in the order in which the data is stored for SQL SERVER but in postgres we have to manually sort the 
rows using CLUSTER keyword and this locks the database.
Non Clustered index contains pointers to the location to which data is stored so this is better when we use it for queires where we do frequent whers

Postgres supports differnt types of Indexes :
BTree index => best sued for range and = >= ,<=
Hash index => best used for exact matches (=)
CREATE INDEX idx_employees_department ON employees USING btree(department);

USING hash(email);
