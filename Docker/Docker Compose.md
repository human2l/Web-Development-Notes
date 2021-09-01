create `docker-compose.yml` to project folder

## docker-compose.yml

**Note: indentation matters!**

```yaml
version: '3.6'

services:

	# Backend API
	smart-brain-api:
		container_name: backend
		# we dont need image because we build from our own Dockerfile
		# image: node: 8.11.1
		# build: allows us to build from our own Dockerfile instead of a default image like node:8.11.1
		build: ./
		command: npm start
		working-dir: /usr/src/smart-brain-api
		environment: 
			# we use "postgres" instead of "localhost"
			POSTGRES_URI: postgres://sally:secret@postgres:5432/smart-brain-docker

# # environment variables (alternative)
		# environment:
		#	POSTGRES_USER: sally
		#	POSTGRES_PASSWORD: secret
		#	POSTGRES_DB: smart-brain-docker
		#	# The host name of database, because we cannot use localhost directly, we use the NAME of database service which is postgres
		#	POSTGRES_HOST: postgres
		
		ports:
			- "3000:3000"
		# volumes: can map the current folder on machine to the working directory. So that when we `docker-compose up` ,each time we change file and save in the machine folder, the content of correspond working directory  will be automatically update
		volumes:
			- ./:/usr/src/smart-brain-api
	# Postgres
	postgres:
		# we need to copy the environment variables (database information) from backend API service to this, because we need them to set up the user, password etc.
		environment:
			POSTGRES_USER: sally
			POSTGRES_PASSWORD: secret
			POSTGRES_DB: smart-brain-docker
			POSTGRES_HOST: postgres
		# we dont need container_name because image has the name already, uncommon will show error
		# container_name: postgres
		# use below instead of "build" if we are not using Dockerfile to init image
		# image: postgres
		build: ./postgres
		ports:
			- "5432:5432"
```

```bash
docker-compose build
```

**NOTE: everytime change the yml file, need to run `docker-compose build` to re-read that file**

<img src="Docker Compose.assets/Screen Shot 2021-08-30 at 4.02.53 PM.png" alt="Screen Shot 2021-08-30 at 4.02.53 PM" style="zoom:50%;" />

```bash
docker-compose run smart-brain-api
```

<img src="Docker Compose.assets/Screen Shot 2021-08-30 at 4.08.16 PM.png" alt="Screen Shot 2021-08-30 at 4.08.16 PM" style="zoom:50%;" />

```bash
docker-compose down
```

`docker-compose down` Bring down any containers we have, to avoid any conflicts we may have

```bash
docker-compose up --build
```

`docker-compose up --build` build and then run the container

## environment variables

because we already set the variables in service: smart-brain-api. we can use it in our code:

<img src="Docker Compose.assets/Screen Shot 2021-08-30 at 9.30.10 PM.png" alt="Screen Shot 2021-08-30 at 9.30.10 PM" style="zoom:50%;" />

Alternative:

<img src="Docker Compose.assets/Screen Shot 2021-08-30 at 9.17.00 PM.png" alt="Screen Shot 2021-08-30 at 9.17.00 PM" style="zoom:50%;" />

## Database:

In project folder, create a new folder named postgres, then create new `Dockerfile` and `deploy_schemas.sql`into this folder

Create new folders in `postgres/` named `tables` and `seed`

Create two new files in `tables/` : `login.sql` , `users.sql` and `seed.sql`

### users.sql

```sql
BEGIN TRANSACTION;

CREATE TABLE users (
	id serial PRIMARY KEY,
  name VARCHAR(100),
  email text UNIQUE NOT NULL,
  entries BIGINT DEFAULT 0,
  joined TIMESTAMP NOT NULL
);

COMMIT;
```

`BEGIN TRANSACTION` and `COMMIT` makes sure if the code between them fails, ignore all of the code already run and make everything back to before.

### login.sql

```sql
BEGIN TRANSACTION;

CREATE TABLE login (
	id serial PRIMARY KEY,
  hash varchar(100) NOT NULL,
  email text UNIQUE NOT NULL
);

COMMIT;
```

### seed.sql

Create default user for testing purpose:

```sql
BEGIN TRANSACTION;

INSERT into users (name, email, entries, joined ) values ('Jessie', 'jessie@gmail.com', 5, '2018-01-01');
INSERT into login (hash, email) values ('PASSWORD HASHED BY BCRYPED HERE', 'jessie@gmail.com');

COMMIT;
```

### deploy_schemas.sql

```sql
-- Deploy fresh database tables
-- \i means to run scripts
\i '/docker-entrypoint-initdb.d/tables/users.sql'
\i '/docker-entrypoint-initdb.d/tables/login.sql'

\i '/docker-entrypoint-initdb.d/seed/seed.sql'
```

#### Dockerfile

```dockerfile
FROM postgres: 10.3

# Standard naming of postgres to extend this image according to postgres image documentation
ADD /tables/ /docker-entrypoint-initdb.d/tables/
ADD /seed/ /docker-entrypoint-initdb.d/seed/
ADD deploy_schemas.sql /docker-entrypoint-initdb.d/tables/
```

## Note:

After once we `docker-compose up --build` and no more changes of docker, we can use just `docker-compose up` to fast run the build.

# Resources:

[docker-compose build](https://docs.docker.com/compose/reference/build/)

[docker-compose run](https://docs.docker.com/compose/reference/run/)

[docker-compose up](https://docs.docker.com/compose/reference/up/)

### Volumes: 

https://stackoverflow.com/questions/34809646/what-is-the-purpose-of-volume-in-dockerfile
https://www.linux.com/learn/docker-volumes-and-networks-compose



\1. How we set up the database with username and password: (see the environment variables section) https://hub.docker.com/_/postgres/

\2. `psql ` command: https://www.postgresql.org/docs/9.2/static/app-psql.html

\3. Finally, if you haven't done so already, see if you can install PostgreSQL on your machine and use a GUI like I do in the video to make sure your docker-compose file is working: 

### PostgreSQL With Docker

To install PostgreSQL on your computer, follow the below steps: 

**Mac:** Follow my previous video for instructions. You will need [homebrew](https://brew.sh/) for the easiest way to set up. keep in mind you may have to run with the 'sudo' command. Or you can follow [this tutorial](https://www.codementor.io/engineerapart/getting-started-with-postgresql-on-mac-osx-are8jcopb).

[PSequel GUI](http://www.psequel.com/) 

**Windows:** Follow [this tutorial](http://www.postgresqltutorial.com/install-postgresql/)

**Linux: Thanks to fellow student Dimitris for this great guide:**

For any of the Linux users following the course and interested in installing PostgreSQL along with a GUI (eg. pgAdmin), [their website has wonderful instructions](https://www.postgresql.org/download/), and so does their wiki (for example, [this link is for Debian and Ubuntu based distros](https://wiki.postgresql.org/wiki/Apt)). 

Also, one way to issue the commands you typed in the video to start, stop, restart PostgreSQL in Linux is: 

```
sudo systemctl start postgresql     # starts the serversudo systemctl stop postgresql      # stops itsudo systemctl restart postgresql   # restart itsudo systemctl status postgresql    # check the server's status
```

The "`createdb test` " command and the "`psql 'test'` " command are the same (at least for Debian/Ubuntu systems) from what I saw. 

When it's first installed, PostgreSQL just has the 'postgres' user, and the way to initially enter PostgreSQL is by typing `sudo su - postgres` , and then `psql` . After Andrei creates the 'test' database, we can create a user with the same name as our current logged in user, to be a database administrator. This way we can just type in `psql 'test'` from the command line and enter the database without the need of logging in as the 'postgres' user, just like Andrei does in the lecture. This can be done with `CREATE USER your-user-name-here WITH SUPERUSER;` , and we can verify that he was created with `\du` . Now we can exit by typing `\q` and then `exit` , and enter our database just like Andrei does, with `psql 'test'` . 

Lastly, with pgAdmin4 we need to create a connection with the server the first time we use it, and this is done by right-clicking 'Servers' on the left pane, and choosing 'Create' > 'Server'. We give our server a name, and in the 'Connection' tab we type in 'localhost' as the host, just like Andrei shows in the lecture, and press 'Save'. 

### init.db File

If you would like to learn more about creating tables in SQL, you can read up [this excellent post](http://joshualande.com/create-tables-sql).

You can learn more about the` /docker-entrypoint-initdb.d ` which we used in the previous video in the official [library/postgres image documentation here.](https://hub.docker.com/_/postgres/)

