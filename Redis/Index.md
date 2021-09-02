<img src="Index.assets/Screen Shot 2021-09-02 at 6.01.39 PM.png" alt="Screen Shot 2021-09-02 at 6.01.39 PM" style="zoom:50%;" />

Schema: relation between tables and field

<img src="Index.assets/Screen Shot 2021-09-02 at 5.48.14 PM.png" alt="Screen Shot 2021-09-02 at 5.48.14 PM" style="zoom:50%;" />

Document-like database: Linkedin profile

Graph: social media(graph-like connections between users)

Key-Value: similar to how we handle object in JS

<img src="Index.assets/Screen Shot 2021-09-02 at 6.09.15 PM.png" alt="Screen Shot 2021-09-02 at 6.09.15 PM" style="zoom:50%;" />

# Redis

NoSQL In-memory database (means we dont have large data sets, easy to access), which makes it really fast. used for short lived data. Sessions, web page headcounts. We can use Redis if we don't care if we lose some data.

Redis save a snapshot every once in a while to save database contents onto the disk. When there is unexpected shutdowns, we only lose a last few minutes of information.

Fast, Scalable

## Installation

https://redis.io/download

## Redis Commands

To run the server:

```shell
src/redis-server
```

To run redis CLI

```shell
src/redis-cli
```

<img src="Index.assets/Screen Shot 2021-09-02 at 7.37.23 PM.png" alt="Screen Shot 2021-09-02 at 7.37.23 PM" style="zoom:50%;" />

Below will delete sessiion:"Jenny" after 10 seconds

<img src="Index.assets/Screen Shot 2021-09-02 at 7.39.33 PM.png" alt="Screen Shot 2021-09-02 at 7.39.33 PM" style="zoom:50%;" />

DECR can only decrement by 1

<img src="Index.assets/Screen Shot 2021-09-02 at 7.41.27 PM.png" alt="Screen Shot 2021-09-02 at 7.41.27 PM" style="zoom:50%;" />

MSET/MGET: multiple set/get:

<img src="Index.assets/Screen Shot 2021-09-02 at 7.43.21 PM.png" alt="Screen Shot 2021-09-02 at 7.43.21 PM" style="zoom:50%;" />

## Data Types

5 data types: strings, hashes, lists, sets and sorted sets

### Hashes

hashes are maps between string fields and string values. Like JS object

<img src="Index.assets/Screen Shot 2021-09-02 at 7.48.28 PM.png" alt="Screen Shot 2021-09-02 at 7.48.28 PM" style="zoom:50%;" />

### Lists

Lists are linked lists

<img src="Index.assets/Screen Shot 2021-09-02 at 7.53.14 PM.png" alt="Screen Shot 2021-09-02 at 7.53.14 PM" style="zoom:50%;" />

<img src="Index.assets/Screen Shot 2021-09-02 at 7.53.57 PM.png" alt="Screen Shot 2021-09-02 at 7.53.57 PM" style="zoom:50%;" />

### Sets

Sets are unordered collection of strings. Not allowing reapeted value.

<img src="Index.assets/Screen Shot 2021-09-02 at 8.20.55 PM.png" alt="Screen Shot 2021-09-02 at 8.20.55 PM" style="zoom:50%;" />

<img src="Index.assets/Screen Shot 2021-09-02 at 8.22.34 PM.png" alt="Screen Shot 2021-09-02 at 8.22.34 PM" style="zoom:50%;" />

### Sorted Sets

each member has a score which can be sorted

<img src="Index.assets/Screen Shot 2021-09-02 at 8.25.39 PM.png" alt="Screen Shot 2021-09-02 at 8.25.39 PM" style="zoom:50%;" />