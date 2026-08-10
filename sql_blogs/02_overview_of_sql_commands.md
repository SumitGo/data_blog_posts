## SQL Commands

In the [previous](https://datanengineering.hashnode.dev/1-sql-basics) blog, we explored some basic concepts related to data, database, and SQL.

Now we are going to get our hands dirty on SQL commands.

But before making any talk to the database(which, if you remember, stores data), we first need to fill the database with data. And even before that we need to create database.

Well, we don't need to create databases, there are already plenty of them like:

1.  PostgreSQL( we are going to use this)
    
2.  Oracle SQL
    
3.  Microsoft's SQL Server
    
4.  MySQL
    

And many more.

### Why PostgreSQL?

Honestly you could pick any of the database mentioned above or of your choice. I am using Postgres because its Free and Open Source, and i am a fan of FOSS. Also, PostgreSQL is :-

*   used in real industry projects
    
*   easy to setup
    
*   no cost of licenses(just like MySQL)  
    Oracle and MS SQL costs license fees for enterprise usage.
    

Now head over to postgres website and download it, if feel lost in installing, then ask chatgpt. It will help you get things running.

I personally use postgreSQL terminal, called `psql`. You can use `PgAdmin`( A GUI way of working with Postgre) as well.

Here are few commands that i use most often in `psql`.

*   \\c <database\_name> - connect to a database  
    For e.g. *\\c myDatabase* - connects to the database called myDatabase.
    
*   \\l - Lists all the databases in the DB server
    
*   \\dt - shows all the tables inside a database, use it after connecting to the database
    
*   \\d - shows the schema of the table.
    
*   \\q - to quit the terminal
    

### Commands/

Before doing anything in the database, we need data inside the DB.

To create a database, we use Data Definition Language(DDL) commands.

#### DDL Commands:-

*   CREATE - To create database or table
    
*   ALTER - To change the Schema(how data is stored inside a table)
    
*   DROP - Delete a Database or table
    

Let's Practice them a bit and fill our empty database with some data.

We want to create a table named `customers` in our database with the following data:-

```sql
 id | first_name | country | score 
----+------------+---------+-------
  1 | Maria      | Germany |   350
  2 |  John      | USA     |   900
  3 | Georg      | UK      |   750
  4 | Martin     | Germany |   500
  5 | Peter      | USA     |     0
```

***How do we do this??***

*If you are in* `psql` terminal, then just write this query and hit enter to run this query.

*If using* `PGAdmin`*, then you will find a run button, just click it to run this query.*

```sql
CREATE Table customers (
    id INT NOT NULL,
    first_name VARCHAR(50) NOT NULL,
    country VARCHAR(30),
    score INT,
    CONSTRAINT pk_cust PRIMARY KEY(id)
    );
    
```

Breakdown of this query:

*   `CREATE Table customers` - creates a table named customers
    
*   `id INT NOT NULL,` - defines name of a column ( `id`), what type of value it will store(Integer values in this case), and any constraints( `NOT NULL` means value can't be empty for this column, in any row).
    
*   `first_name VARCHAR(50) NOT NULL,` - a column named `first_name`, stores value of character type(50 characters at max can be stored), value in this column cannot be null.
    
*   `country VARCHAR(30),` - a country column, where values can be NULL.
    
*   `score INT` - score column which stores integer values, and values can be Null.
    
*   `CONSTRAINT pk_cust PRIMARY KEY(id)` - defines a constraint of primary key, every table must have a primary key, here we declared `id` column to be primary key. `pk_cust` is a name which is used internally by postgre and we need not worry about it.
    

But do you think just defining `Schema` (what kind of data we are going to store in a table, which column is primary key, what are the constraints of the columns) is enough.

You can run this query to see that our table is actually empty right now.

```sql
SELECT * FROM customers;
```

Let's fill in the values.

```sql
INSERT INTO customers VALUES (1, MARIA, Germany, 350),
(2, John, USA, 900),
(3, Georg, UK, 750),
(4, Martin, Germany, 500),
(5, Peter, USA, 0);
```

After running this command, now run the SELECT command again, and voilaa, you are seeing data in your table.Nice...

> **NOTE:** We are terminating each query with a `;`. Otherwise SQL don't know when a query ends. This might not be needed in PGAdmin, but i am not sure about it, But it's a good practice to include a semi-colon after each query.

YOU did it!! Very Good, now you have some data to work with. If you find it difficult to follow, just take a break, or you might need to watch this [SQL Tutorial by Data with Baraa](https://youtu.be/SSKVgrwhzus?si=b3FlWrd_mRaCvBVL), which i am still following.

Now, just as a practice, try to make `orders` table for yourself:

```sql
 order_id | customer_id | order_date | sales 
----------+-------------+------------+-------
     1001 |           1 | 2021-01-11 |    35
     1002 |           2 | 2021-04-05 |    15
     1003 |           3 | 2021-06-18 |    20
     1004 |           6 | 2021-08-31 |    10
```

Let me tell you some additional details you will need while creating this table.

```sql
mydatabase=# \d orders --remember this command from above
                 Table "public.orders"
   Column    |  Type   | Collation | Nullable | Default 
-------------+---------+-----------+----------+---------
 order_id    | integer |           | not null | 
 customer_id | integer |           | not null | 
 order_date  | date    |           |          | 
 sales       | integer |           |          | 
Indexes:
    "pk_orders" PRIMARY KEY, btree (order_id)
```

For interger - use `INT` while declaring the datatype of the column

For date - use `DATE`

> FUN : Try to run the `\d` command for customers table as well.

I really hope you was able to make it, if not, then move to the end of this blog, you will find query to create this table.

#### DML Commands:-

Data Manipulation Language commands are used to work with data inside the table, be it inserting new data, updating existing data, or deleting the data.

*   INSERT - used to insert values into the table, we just used it above.
    
*   UPDATE - used to update the values inside rows
    
*   DELETE - used to delete rows from the table
    

And in the End...

#### DQL Commands:-

Data Query Language is used to talk to the database and ask for the data from the table.

*   SELECT - used to fetch/retrieve data from a table
    

Yes, DQL is that short. But this is the command we will be using a lot, You already saw it being used once above.

Run this command, right now...

```sql
SELECT * FROM orders;
```

You should get data from \`orders\` table, ONLY if you made it, and not skipped the task.

But if YOu aRE LOOkiNG FoR AnsWeR,

Here it is:

```sql
-- First Create the schema for the table.
Create TAble orders ('order_id' INT NOT null,
customer_id InT NOT Null,
order_date DATE,
sales integer,
Constraint 'pk_orders' prImary key(order_id)
);
-- Notice, i didn't played with the actual names of the table or columns.
-- Now we fill the data inside the table
INSERT INTO orders Values (1001, 1, '2021-01-11', 35),
(1002, 2, '2021-04-05', 15),
(1003, 3, '2021-06-18', 20);
```

If you look carefully i only filled three values, Last one is for you, Sorry for Trouble, but please do just one insert.

> Look in the query, it looks strange, Will it Work even?? Well try it, and see for yourself. Yes it works.

In Coming blogs, i will tell why this strange looking query works fine( its actually case insensitivity of SQL). Next we will dive into each of the Languages(DDL, DML, DQL) one by one.

See you in next Blog.