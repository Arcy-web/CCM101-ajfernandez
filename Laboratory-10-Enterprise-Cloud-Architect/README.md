# Laboratory 10: Enterprise Cloud Architect

## Project Overview

For our laboratory our group designed and deployed a private cloud storage system using Nextcloud and MariaDB. The goal of this project is to understand how different parts of an environment work together from the virtual machine and network configuration to the application and database containers.

We used Ubuntu Server as the operating system and Docker Compose to manage the services. Additionally we set up a firewall. Built an automated database backup script to boost the security and maintenance of our deployment.

## Project Objectives

- Deploy Nextcloud as a cloud storage application.

- Connect Nextcloud to a MariaDB database using Docker Compose.

- Use persistent volumes to retain application and database data.

- Configure a firewall to control incoming network connections.

- Automate database backups using a Bash script and cron.

- Document the architecture, deployment, security settings and maintenance procedures.

## Technology Stack

- **Operating System:** Ubuntu Server

- **Virtualization:** Oracle VirtualBox

- **Container Platform:** Docker

- **Container Management:** Docker Compose

- **Cloud Storage Application:** Nextcloud

- **Database:** MariaDB

- **Firewall:** UFW

- **Automation:** Bash and cron

- **Repository:** GitHub

## Project Files

| File | Description |

|---|---|

README.md` | Project overview, objectives and technology stack |

| `architecture-diagram.png` | Architecture and network topology diagram |

| `docker-compose.yml` | Configuration for the Nextcloud and MariaDB containers |

| `automation-script.sh` | Script for automated database backups |

| `operational-manual.md` | Deployment, security, maintenance and troubleshooting documentation |

| `final-reflection.md` | Our groups reflection on the cloud computing activities |

## Security and Data Persistence

Our deployment uses environment variables for sensitive configuration and persistent Docker volumes for application and database data. We set UFW to deny connections by default and allow the ports needed for SSH and web access.

The database backup script creates compressed files writes its results to a log and deletes older backups based on the configured retention period. The.env file holds credentials and must not be uploaded to this public repository.

## Learning Outcome

Through this activity our group gained experience, in container deployment database connectivity, network security, persistent storage and automated backup operations. This project also helped us see why documenting and maintaining an environment matters not just getting the application to run.

## Deployment Verification

The deployment was tested on Ubuntu Server using Docker Compose. Both the Nextcloud application and MariaDB database containers ran successfully. We accessed the Nextcloud login page through the Windows host browser. Confirmed that existing files stayed available after restarting the application container.

We also checked the Docker volumes reviewed the UFW firewall rules and tested the database backup archive. The backup log showed successful backup operations and cron was set to run the backup script at 2:00 AM following the Ubuntu system time.
