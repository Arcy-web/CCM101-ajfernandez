## Mission Overview

In this lab activity I learned how to set up a cloud storage system using Nextcloud and Docker Compose. The setup involved two containers: one for the Nextcloud application and one for the MariaDB database.

The main goal was to see how multiple containers can work together as one application.

## Objectives

* Learn about the idea of Two-Tier Architecture.

* Set up MariaDB and Nextcloud using Docker Compose.

* Make a `docker-compose.yml` file.

* Link the Nextcloud application to a MariaDB database.

* Use environment variables, for database settings.

*. Stop several containers using Docker Compose.

* Keep a record of the setup process with pictures.

## Commands Executed

```bash

docker --version

docker-compose --version

mkdir nextcloud-deployment

cd nextcloud-deployment

nano docker-compose.yml

docker-compose up -d

docker-compose ps

docker-compose down

```

## Skills Learned

From this activity I learned how Docker Compose is used to handle containers at the same time. I also learned how a website can talk to a database container using a service name.

Another big thing I learned was how YAML files can explain an application setup. This helps with organizing deployment because the same file can be used again of setting up each container by hand.

I also got practice with Nextcloud, MariaDB, Docker networking, environment variables and multi-tier cloud setup.
