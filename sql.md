### what is sql ?
- it stands for structured query language , it is used to add , modify or delete data from databases.
- RDBMS stands for relational database management system , it is basis for sql.
- it stores info in databases objects called tables
- there are many versions of sql like mysql , postgresql , ms access , etc
### basic commands
- syntax - commands ; 
- show databases ; // to display all the databases available 

- create database name ;    
    - create database test ; // this will create database name test and then we can use that database 
- use databasename ; 
    - use test ; // use to enter into databse and use it
- drop databasename ; // to delete database 
    - drop test ;
- create table tablename(column name , value);
    - used to create table

``` sql 
 create table student (name VARCHAR(20) NOT NULL, class INT , id INT);
```
- constraints are used for conditions while creating tables
    - NOT NULL;
    - unique
    - check - used to check input value 
    - default
    - primary key
    - value 

- here student is table name , name is column name with data type variable character with max length 20 and its value cannot be null , and one column with name class and data type int , and id column with type int

- drop table tablename ; 
    - drop table student ; // to delete table 

- one example 
``` sql 
create table products (product_id INT NOT NULL AUTO_INCREMENT , product_name VARCHAR(100) NOT NULL ,product_menu VARCHAR(40), PRIMARY KEY (product));
```

- auto_increment means this will automatically increase and in this we need to add primary key at the end 

### querying table
- inserting query we use insert command to insert the data into table
    - insert into tablename(colum name ) VALUES (value);
```sql 
insert into products(product_id , product_name,product_manufacturer) VALUES (10 , "mi phone" , "redmi");
```

- select query 
    - select field1, field 2  ,etc from tablename ;
    - select * from tablename ;  // to select all columns
    - select distinct column 1 from table ; // select unique columns 
    - select count(distinct Column) from table; // tells number of different values in this column , this wont work in ms access
    - select Count(*) AS DistinctCountries
from (select distinct Country from Customers);

``` sql
select product_name , product_id from products ; 
```
- where clause = it act as if statement with commands like select , udpate, delete and insert .
    - select field from table where condition;

``` sql 
select product_id from products where product_name ="redmi" ;
```
- keywords with where - like and between
- like is used to get multiple results using wildcards 
- between is used to set range 
- where clause can use operators also like < , > or != 
- it also uses AND , OR 
- in operator 
``` sql 
select product_id from products where product_name like redmi% ;
select product_id from products where product_id between 10 and 20 ;
```
- select top - used to specify the number of records to return;

- it is not supported in MySQL , supports the LIMIT clause to select a limited number of records, while Oracle uses ROWNUM.
- sql and ms access


``` sql 
SELECT TOP number|percent column_name(s)
FROM table_name
WHERE condition;
```
- mysql
``` sql
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```
- oracle
``` sql
SELECT column_name(s)
FROM table_name
WHERE ROWNUM <= number;
```

- select into - it is used to copy data from one table into a new table

``` sql
select * into table1 from table2 ;
```
- insert into select is used copy data from one table and insert it into another table

``` sql
insert into table2 select * from table1 where condition;
```

- update command = used to update values in column
    - update tablename set field = new value , field 2 = new value 2 ---- where condition ; // we can also use where to change only specific field
``` sql 
update products set product_name="nokia" where product_id="redmi";
```

- delete command = use to delete value from tables
    - delete from tablename where condition;
``` sql 
delete from products where product_id=12;
```
- order by - it used to sort the result in ascending or decending order 
    - select field from tablename order by field 1 , field 2 (asc  or desc)

``` sql 
select product_name from products order by product_id ASC ;
```

- union operator - it is used to combine the result set of two or more select statements 
- it removes duplicates to get duplicates we use unionall

``` sql
select column from table1
union
select column from table2 ;
```

- join - merge two or more tables into single object 
```sql
select column from table1 inner join table 2 on table1.cplumn = table2.column ; 
```
- we have inner join = matching values , left join = left table all values and matched values form right table , right join = right table all values and matched values form left table 

![img](https://github.com/nitishsaini706/references-images/blob/master/sql/sql%20joins%20guide%20and%20syntax.jpg)

- indexes = there are 4 types of indexes 
    -   primary 
    - unique
    - plain
    - full-text
- create [type] index index-name on tablename column;
``` sql
create uniques index top-seller on products product-id;
drop index index-name on tablename;
show index from tablename;
alter table tablename drop index indexname , ADD index new_index_name;
```

- alter - used to modify exisiting table , works with pairs 
    - alter-drop = removes column ;
    - alter-add = add column 

``` sql 
alter table tablename drop column;
alter table tablename add column;
alter table tablename rename to newtablename;
alter table tablename alter columnname set default value; // to set default value for table
```
- create users in sql 
- create user username@lhostname identified by 'psw' ;;
- select host,user,password from user where user='username';

``` sql
create user nitish@root identified by '9878' ;
select host,user,password from products where user='nitish';
```

- grant permissions 
- grant select,update,insert on databse.table to user@hostl
- for all permisions 
    - ALL PRIVILEGES on *.* ;

- to remove permission , we use revoke
    - same as grant = revoke select on database.table to user@host
```sql 
show grants for nitish;
drop user ; // to drop user
flush privileges ; // reload privileges
```
- two privileges we use global and crud 
- global means all 
- crud = create read update delete 

### wildcard 
- % - repersent 0 or more characters
- _  = represent single characters
- in ms access we uses an astrick  * instead of % and ? instead of _

```
a%    - start with a 
%a    - ends with a 
%a%   - in any position
_r%   - r in second position
a__%  - start with a with 2 characters length
a%o   - start with a and end with o

(in ms access we replace * with % and ? in _ )

```

|  ms | sql  |                         |
|-----|------|-------------------------|
| *   |  %   |   zero or more characters  |
| ?   |  _   |    single character  |
|  [] | [ ]  |    ang single within brackets |
|  !  |  ^   |  not in brackets |
| -   |   -  |  range eg a-z |
|  #  |      |    single numeric|

### regular expressions
- select column from table where colum regex 'patter' ;

- ^ - start of string 
- . - single charecter
- $ - end of string
- [...] - any in bracket
- [^..] - not in bracket
-  (star) * - 0 or more occurence 
- (plus) + - 1 or more occurence 
- {n} - n preceeding 
- {m,n} - m to n preceeding 

``` sql 
select name from products where name REGEXP '^pr';
```
- [aeiou] - any vowel
- ^[aeiou] - starting with any vowel
- na$ - end with na , karna etc 


### sql injections 

![img](https://github.com/nitishsaini706/references-images/blob/master/sql/sql1.png)
![img](https://github.com/nitishsaini706/references-images/blob/master/sql/Screenshot_20200426-112258.png)
![img](https://github.com/nitishsaini706/references-images/blob/master/sql/Screenshot_20200426-112754.png)
![img](https://github.com/nitishsaini706/references-images/blob/master/sql/Screenshot_20200426-112818.png)
![img](https://github.com/nitishsaini706/references-images/blob/master/sql/Screenshot_20200426-113017.png)
![img](https://github.com/nitishsaini706/references-images/blob/master/sql/Screenshot_20200426-113141.png)
![img](https://github.com/nitishsaini706/references-images/blob/master/sql/Screenshot_20200426-113355.png)
![img](https://github.com/nitishsaini706/references-images/blob/master/sql/Screenshot_20200426-113442.png)
![img](https://github.com/nitishsaini706/references-images/blob/master/sql/Screenshot_20200426-114438.png)
![img](https://github.com/nitishsaini706/references-images/blob/master/sql/Screenshot_20200426-121553.png)
![img](https://github.com/nitishsaini706/references-images/blob/master/sql/Screenshot_20200426-121829.png)
![img](https://github.com/nitishsaini706/references-images/blob/master/sql/Screenshot_20200426-125724.png)

