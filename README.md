# What is this?

This is a demo application demonstrating a migration issue with JobRunr.

# Setup

## Create the database

```
$ psql postgres
# CREATE ROLE jobrunr_upgrade_demo WITH LOGIN PASSWORD 'example123' CREATEDB;
# \q
$ psql postgres -U jobrunr_upgrade_demo
> CREATE DATABASE jobrunr_upgrade_demo;
> GRANT ALL PRIVILEGES ON DATABASE jobrunr_upgrade_demo TO jobrunr_upgrade_demo;
> \q
```
