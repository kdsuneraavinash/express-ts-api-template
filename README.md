# Example API

## Cloning

```bash
$ git clone https://github.com/kdsuneraavinash/express-ts-api-template
```

## Guide

### Install Dependencies

Make sure you have yarn installed.(https://yarnpkg.com/)
Then Run `yarn` to install dependencies.

```bash
$ yarn
```

### Copy .env file

Copy the `.env.example` file to `.env` file and change the values according to your environment.

### Postgres Setup (For production)

Install [postgres](https://www.postgresql.org/download/) and setup it according to your OS instructions. Use following
command to login to the `psql` shell.

```bash
$ psql -U postgres
```

Then enter below commands.

```sql
CREATE ROLE db_user WITH LOGIN PASSWORD 'password';
CREATE
DATABASE example_db;
GRANT ALL PRIVILEGES ON DATABASE
example_db TO db_user;
\q
```

Then login to `psql` as `db_user` and check if the setup is done correctly. Password should be `password`.

```
psql -U db_user example_db
```

#### Windows specific instructions

1. Install [postgresql](https://www.postgresql.org/) in the local machine and setup correctly. **Do not change default
   port or other settings.** Give a password to `postgres` user when asked.
2. Login to `pgAdmin` using the username and password give in the setup process. From the `Browser` panel,
   select `Server>postgres>Login/Group Roles` and right click and create the role. Give `db_user` as role name and
   give `password` as the password.
3. Then right click `Server>postgres>Databases` and Create new database. Give `example_db` as the database name and
   set `db_user` as the owner.
4. Then try to login to `psql` shell using default port, server, database `example_db` and `db_user` user.

### Prisma Setup

First run the database migration and create the necessary tables. Make sure you are in the correct virtual
environment. **Whenever there is a database model change, you should re-run this.**

```bash
$ npx prisma migrate dev
```

Then add the initial seed data.

```bash
$ npx prisma db seed
```

### Run Project

The default url for the API is [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

```bash
$ yarn dev
```
