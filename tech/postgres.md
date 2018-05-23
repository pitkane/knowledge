# Postgres

## Articles

[Creating user, database and adding access on PostgreSQL](https://medium.com/coding-blocks/creating-user-database-and-adding-access-on-postgresql-8bfcd2f4a91e)

## pg_dump

`sudo -u postgres pg_dump database_name > postgres_db.bak`

Restore:

`psql dbname < infile`

## Basics

One nice thing about PGSQL is it comes with some utility binaries like createuser and createdb. So we will be making use of that.

As the default configuration of Postgres is, a user called postgres is made on and the user postgres has full superadmin access to entire PostgreSQL instance running on your OS.

`sudo -u postgres psql`

The above command gets you the psql command line interface in full admin mode.

In the following commands, keep in mind the < angular brackets > are to denote variables you have to set yourself. In the actual command, omit the <>

Creating user

`sudo -u postgres createuser <username>`

Creating Database

`sudo -u postgres createdb <dbname>`

Giving the user a password

`sudo -u postgres psql`

`psql=# alter user <username> with encrypted password '<password>';`

Granting privileges on database

`psql=# grant all privileges on database <dbname> to <username>;`

And yeah, that should be pretty much it !
