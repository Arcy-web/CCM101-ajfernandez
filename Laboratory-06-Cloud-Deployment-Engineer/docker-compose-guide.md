# Docker Compose Guide

##

Docker Compose is a tool that helps define and run -container applications. It uses a YAML file to describe the services. In this activity Docker Compose is used to run both Nextcloud and MariaDB

## What Does the `services:` Block Do?

The `services:` block tells Docker Compose what services to manage. This configuration includes two services: `database` which uses the MariaDB 10.6 image and `app` which uses the Nextcloud image. Each service has its settings. These include environment variables and port mappings.

## How Does Nextcloud Find the Database?

The environment variable `MYSQL_HOST=database` tells the Nextcloud container to connect to a service named `database`. Docker Compose allows containers to communicate using service names as hostnames. This is part of the project network. The other environment variables provide the database name, username and password needed to connect.

## Docker Run vs. Docker Compose Up

The `docker run` command starts a container with options given directly on the command line. Docker Compose on the hand uses a configuration file. This file defines services and how they should work together. When you run `docker-compose up -d` all the services start, at once in the background. This makes managing -container apps much easier and more consistent.

## Deployment Commands

```bash

mkdir nextcloud-deployment

cd nextcloud-deployment

nano docker-compose.yml

docker-compose up -d

docker-compose ps

docker-compose down

```

##

Docker Compose makes it easier to deploy containers. It keeps all the settings in one file. This helps cloud engineers manage applications in a clear and repeatable way.
