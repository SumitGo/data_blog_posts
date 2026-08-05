## Concetps of Data
Few terms you have heard for sure are:
- Data
- Database
- Database Management System(DBMS)
- Database Server

Before starting with SQL, let's know what they are at the surface level.

### What is Data?
- A data is any measurement related to a physical object/ entity.
(You can google for more sophisticated defination, but in short that's the definition)

### What is Database?
- A database is simply a container for storing the data.

But then how is it different from a file like notepad file, or excel file???
Well, a file like notepad file, excel file or any other file, can indeed store data, search for any data, replace data and other operations you can think of.
But the problem starts when the data becomes really big for these files to handle.

Here's the problem with these file formats:-
- File crashes

    If the data becomes too big, file might open or crash.

- Updation problem

    To view any data, you need to open a file, and if file has millions of data( rows or columns), then opening it will take some time(if it didn't crashed).
    Say data in one file is linked with data in another file. For e.g. you have an excel file which stores the details of the customers, containing a name column, there is another excel file which stores the customers payments information. Now one customer wants to make a correction in his name( maybe because he wrote it incorrectly in the first place).
    Now you have to change the name in the customers excel file, and then in the payment details file as well, isn't it a `slow` process??, And you have to `change the same information multiple times` as well.


### Whereas in Database:
- It's easy to search for the data
- perform operations like searching and filetering and more, efficiently
- handles massive amounts of data like in millions
- fast, reliable and secure

**But what does a database do to achieve all of this, that a file can't??**

Although this a question which probably takes to the Database Design, all i know for now is that a database uses multiple kinds of designs which are build specifically for these types of tasks, mentioned in ['Wheareas in Database']

**Before going ahead, let's discuss what exactly is SQL??**
- Now that we know that we use database to store massive amounts of data, but how do we know what is stored inside the database. For a file, we can click it to open it, but for database You need `SQL`.
* Structured Query Language or SQL(Pronuonced as 'as-que-el' or 'se-quel')
is a language to talk to the database, just like how programming languages are used to talk to a computer.
Let's Break Down the name first
Structured - the Statements in SQL have a proper structure/ format of how you will write
Query - the statements we write are actually called query in SQL as a Query is used to query the database
Language - yes, it's a language for humans to talk to database.

### What is a DBMS??
Data Base Management System is a Software designed to handle different queries, and keep the ACID properties in check(More about ACID will come in later chapters later), and much more.
Imagine this, 
- An app makes some queries to the database
- a web application also makes queries to the database
- an API also sends some queries to the database.
- other persons accessing and quering the database

All of this happening simultaneously. A database has the job of storing the data, not handling which queries to execute first, or even execute it or not.
This is where the need of DBMS arises.
* DBMS has the job of scheduling which query to be executed first, and also return the results of the database to the user.

You know, the Data, Database, and the DBMS need to be implemented somewhere. That's the database server.

### What is Database Server??
A Database Server, Just like any other server which has the job of serving the customers, also server the users to query the database.
This server is the physical compute on which the data, database and dbms lives.
A port is what gives access to the server in the machine.
For our local PC, we may close the server any time we want.
But for an Enterprise, this server keeps running and with much more compute power than we see in the PC.

### Database Types/Models
A database can be of different types, here, i am showing mostly popular models, there might be other models as well.
* Relational Database (`Microsoft SQL Server`, `PostgreSQL`, `Oracle SQL`, `MySQL`, and more)
- Consists of multiple tables, formed with rows and columns
- Each table can be related to each other, hence the name Relational Database.
- This type is also called the SQL database. The rest of the databases models are called NoSQL databases.
- This is the type we are going to focus on.

`Just going to brief about the rest of the types, i don't have much knowledge about them`

* Key-Value Database (`Amazon DynamoDB`, `Redis`)
- Consists of a unique key, and a related meaning of that key
- Just like in dicitonary we have a key and it's meaning, similarly, in this DB we have a Unique key mapped to a vlaue

* Column based Database (`Apache Cassandra`, `Amazon Redshift`)
- Each data is stored in a specific column
- This type of database only consists of columns
- It's an advance DB used to handle massive amounts of data, primarily for searching the data.

* Graph based Database (`Neo4j`)
- Main focus is that data elements have relations to each other.

* Document DB (`MongoDB`)
- Data is stored in a document format.
- It's not important to search the DB, but to fit all the data in one place, one document


**Database Structure**
Databases have a proper structure of organising the data.
- A single machine can run multiple Database Servers.
- A single Database Server can contain multiple databases, like databases for hr, and for sales,etc.
- A database can have multiple Schemas.
- A schema can have multiple tables, may be related to each other.
- A table contains multiple rows and columns.
- A column is any feature/attribute/field about an object/entity.
- A row contains the data about the features of the object.
- A cell is a intersection of row and column.

Schema define which columns will contain what kind of data( string, or number, or data, etc), which tables are related to which tables( using primary key and foreign key).

A table organises data into multiple columns, each column defianes a property of an object, also called fields/attributes.

Each row, also called Records, represents data about a feature/column.

Each table contains a Primary key.

A primary key is a column which contains all unique values and not null vlaues i.e. no entry in this column is left empty, every row has some value for this column which is unique, not repeated in the whole column.

Each cell contains a value of some specific datatype.

A datatype is what tells what kind of values can be filled in any column.

Various Datatypes are:
- INT - to store integer value
- DECIMAL - to store decimal/floating point values
- CHAR - to store fixed length memory for strings
- VARCHAR - to store variable length memory for any string
- DATE - store date information (yyyy-MM-dd)
- TIME - stores time information (HH-mm-ss)

Now we are ready to go in depth in SQL. See you in next chapter notes.

If you find any incorrect information, please feel free to correct me, by commenting or some other way, i will update the information here.