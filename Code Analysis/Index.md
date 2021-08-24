When we are taking over someone and trying to deal with an exist project:

### 1.Fork the project

For further code updating, use pull request

### 2. open two terminal, one for client, one for server

<img src="Index.assets/Screen Shot 2021-08-24 at 1.47.44 PM.png" alt="Screen Shot 2021-08-24 at 1.47.44 PM" style="zoom:50%;" />

### 3. Look at package.json

To see what dependencies they are using

Do `npm install` to both client and server code

Do `npm start` on both to see if they both work fine<img src="Index.assets/Screen Shot 2021-08-24 at 1.50.46 PM.png" alt="Screen Shot 2021-08-24 at 1.50.46 PM" style="zoom:50%;" />

Look at package.json again to see what database it uses. Dive into the server code to see database parameters i.e.: 

<img src="Index.assets/Screen Shot 2021-08-24 at 1.55.58 PM.png" alt="Screen Shot 2021-08-24 at 1.55.58 PM" style="zoom:50%;" />

We can see the `pg`means it is a postgre database.

### 4. Setting up the local database

```shell
brew install postgresql
```

```shell
brew services start postgresql
```

```shell
createdb 'smart-brain'
```

```shell
createuser aneagoie
```

Use a GUI tool to connect to the database. i.e. psquel or DBeaver

```sql
create table users (
	id serial primary key,
	name varchar(100),
	email text unique not null,
	entries bigint default 0,
	joined timestamp not null
);

create table login (
	id serial primary key,
	hash varchar(100) not null,
	email text unique not null
)
```

serial: automatically incremental key

varchar: variable character

### 5. Check API key used in app

<img src="Index.assets/Screen Shot 2021-08-24 at 3.05.31 PM.png" alt="Screen Shot 2021-08-24 at 3.05.31 PM" style="zoom:50%;" />

