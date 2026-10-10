# Two-Tier Architecture

## What Is a Two-Tier Architecture?

A two-tier architecture is an application design where the application layer and the database layer work separately and talk to each other. In this case Nextcloud acts as the web application while MariaDB holds the database information for the application.

## The Web/Application Tier

The web/application tier uses Nextcloud to create the user interface and deal with requests from users through a web browser. It takes in HTTP requests. Gives the applications features.

## The Database Tier

The database tier uses MariaDB to keep the applications information, like user account details and file metadata. It lets Nextcloud save and get database records.

## Why Separate Them?

Putting the web application and database in containers makes the system simpler to handle and fix. Each part can be set up. Managed on its own and splitting their jobs helps divide the application into clear parts. Docker Compose helps to set up and run both containers together.
