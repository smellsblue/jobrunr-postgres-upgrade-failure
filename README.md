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

## Run part 1

From this directory, run part 1, and just Ctrl+C to stop it after it has fully started:

```
$ (cd demo-part-1 && ./mvnw spring-boot:run)
```

This should initialize the application with JobRunr 4.0.7, running the JobRunr migrations.

## Run part 2

Run part 2 similarly, but this one fails, demonstrating the problem:

```
$ (cd demo-part-2 && ./mvnw spring-boot:run)
```

This project attempts to run with JobRunr Pro 5.1.7, but fails to start up due to an exception while running the migrations.

## Extra

If you were to run part 2 from a fresh database, everything works, so it seems the migration order is the root cause of the issue.
