<img src="Database Scaling.assets/Screen Shot 2021-09-30 at 8.49.44 PM.png" alt="Screen Shot 2021-09-30 at 8.49.44 PM" style="zoom:50%;" />

# Identify Inefficient Queries

Most **IMPORTANT** item in database scaling

Only request when we absolutely need and use indexes to improve query of data

#### Indexing:

is a way of sorting a number of records on multiple fields

<img src="Database Scaling.assets/Screen Shot 2021-09-30 at 8.55.18 PM.png" alt="Screen Shot 2021-09-30 at 8.55.18 PM" style="zoom:50%;" />

## Create index

```sql
CREATE INDEX idx_name ON table_name (column_name);
```

# Vertical Scaling

Add another service like Redis for system to use resouces better. 

i.e. before check some frequently used data in database, we can check if it exist in Redis first, if Redis does not have it, then check it in database. And Redis can store the data from database before send it to user. (like CDNs)

# Sharding

extremely hard to do, and it's a very tough problem that raises a lot of issues

breaking down the website into different pieces

i.e. divide users into two databases (age<30 and age>30). When request user with age 23, we only need to query the first database.

# More Databases

clone one database to multiple databases, so that we don't need to send all queries to one same database, instead, we can divide large amount of queries into small amount of queries and send to each database.

# Database type

<img src="Database Scaling.assets/Screen Shot 2021-09-30 at 9.16.07 PM.png" alt="Screen Shot 2021-09-30 at 9.16.07 PM" style="zoom:50%;" />

Decide which database is best for our usecase