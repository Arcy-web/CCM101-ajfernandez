## Purpose

This manual explains how to set up and keep our cloud storage system. Our team used Ubuntu Server, Docker Compose, Nextcloud and MariaDB to make a place where people can get files from a web browser.

We also made a firewall rule list. Wrote a script that backs up the database automatically. This document lists the parts the safety steps and how to keep the system working.

## System Architecture

Our setup uses these pieces:

- **Host machine:** A Windows computer that runs and manages the machine.

- **Hypervisor:** Oracle VirtualBox, which runs the Ubuntu Server machine.

- **Guest operating system:** Ubuntu Server, where Docker and UFW are installed.

- **Nextcloud container:** Gives the cloud storage web interface.

- **MariaDB container:** Keeps Nextclouds database data.

- **Docker volumes:** Keep application and database data after a container restart or recreation.

- **Docker bridge network:** Lets the application and database containers talk privately.

- **UFW firewall:** Limits connections to the Ubuntu virtual machine.

Your web browser on the host talks to Nextcloud using the web port that is set up. The Nextcloud container talks to MariaDB using the Docker network so the database port is not exposed directly to the host.

Look at `architecture-diagram.png` to see the layout and network connections.

## Requirements

Before we start we need:

- Ubuntu Server with memory and disk space.

- Docker Engine and the Docker Compose plugin.

- UFW and cron.

- The project files, including `docker-compose.yml` and `automation-script.sh`.

- A.env` file that holds the required credentials.

- Network access to download the container images that we need.

## Configuration and Credentials

The `.env` file gives Docker Compose the settings it needs. It must contain these variables:

- `MYSQL_ROOT_PASSWORD`

- `MYSQL_DATABASE`

- `MYSQL_USER`

- `MYSQL_PASSWORD`

- `NEXTCLOUD_ADMIN_USER`

- `NEXTCLOUD_ADMIN_PASSWORD`

- `NEXTCLOUD_TRUSTED_DOMAINS`

Use unique passwords. Do not put the `.env` file into GitHub. Show passwords in screenshots, logs or public guides.

The `NEXTCLOUD_TRUSTED_DOMAINS` value must list the host name or IP address that you will use to reach Nextcloud. Set it to match the VM network and access method.

## Deployment and Operation

### Start the services

From the folder that holds `docker-compose.yml` and `.env` run:

```bash

docker compose config

docker compose up -d

```

The first command checks that the Compose configuration can be parsed. Look at the output carefully. Do not publish any part that shows sensitive values.

### Check the running containers

```bash

docker compose ps

```

### Review application logs

```bash

docker compose logs --tail=100 app

```

### Review database logs

```bash

docker compose logs --tail=100 db

```

### Access Nextcloud

Open a web browser. Go to:

```text

http://VM_IP_ADDRESS:8080

```

For real deployments use HTTPS and a suitable TLS setup instead of sending credentials over plain HTTP.

## Data Persistence

Our Compose file uses two named Docker volumes:

- `db_data` keeps MariaDB database files.

- `nextcloud_data` keeps Nextcloud application files.

List the volumes with:

```bash

docker volume ls

```

Recreating containers normally does not delete named volumes. However deleting a volume can permanently remove data. Avoid running `docker compose down -v` unless you want to delete the volumes and know what will happen.

Named volumes do not replace backups.

## Firewall and Network Security

Our Ubuntu server uses UFW to manage connections. The default rule is to deny all traffic and allow all outgoing traffic.

Check the firewall status with:

```bash

sudo ufw status verbose

```

In our lab environment the following ports are allowed:

- **22/tcp:** SSH administration if you need SSH.

- **8080/tcp:** Nextcloud web access, over HTTP.

Open ports that you really need. Keep SSH and web access limited to trusted networks wherever possible. Before turning on UFW while connected through a SSH session, double‑check that SSH access is still allowed or you will lose administrative control.

Keep the MariaDB service on the Docker network and do not expose a public host port.

Port 8080 offers HTTP, not HTTPS. In a deployment use HTTPS set strong credentials keep security updates on schedule limit administrative access and have a clear recovery plan written down.

## Automated Database Backup

Our `automation‑script.sh` makes a MariaDB database dump verifies the archive writes the outcome to a log file and deletes old backups according to the retention period that you set.

Run the script by yourself from the project folder:

```bash

chmod +x automation-script.sh

./automation-script.sh

```

The script needs a `.env` file and a running MariaDB service. By default it puts files into the `backups` folder.

Check the log file:

```bash

cat backups/backup.log

```

List all backup files:

```bash

ls -lh backups/

```

Verify a backup archive:

```bash

gzip -t backups/nextcloud_db_BACKUP_FILENAME.sql.gz

```

Use the real timestamped file name in place of `BACKUP_FILENAME`.

### Schedule daily backups with cron

Open your user’s crontab for editing:

```bash

crontab -e

```

Insert a schedule line that points to the path of the script:

```cron

0 2 * * * /bin/bash /absolute/path/to/automation-script.sh

```

That line tells the system to run the script at 2:00 AM on the VM’s clock. After saving the crontab confirm the entry with:

```bash

crontab -l

```

Make sure the cron daemon is active. The VM must be on. The MariaDB service must be running when the job starts. Move the backups to a secure location and test the restore process regularly in a safe test setting.

**Backup limitation:** The script only copies the MariaDB database. A full recovery plan also needs to protect Nextcloud files and settings. Without those the database backup cannot bring back every user file.

## Routine Maintenance

We recommend doing these maintenance tasks:

- Check the status of each container. Read its logs often.

- Look at how free disk space you have and how big your backups are.

- Review the UFW rules and delete any that are not needed.

- Install updates when you have scheduled maintenance windows.

- Watch the backup log for any errors.

- Store copies of backups outside the VM.

- Run a restore test before you trust the backups.

- Keep passwords and keys secret and change them if they get exposed.

- Write down every configuration change so you can rebuild the deployment later.

### Database connection fails

1. Check that the MariaDB container shows a status.

2. Read the MariaDB logs for clues.

3. Make sure the environment variables for MariaDB are the same in every service that uses it.

4. Verify the Docker network is set up correctly.

5. Do not erase the database volume to try to fix the problem.

### Backup fails

1. Make sure the MariaDB container is running.

2. Confirm that the needed variables exist in the `.env` file.

3. Look at the `backups/backup.log` file for errors.

4. Check that you have free disk space and that the backup folder has the permissions.

5. Run the script, by hand. Check that the archive looks correct.

##. Responsible Operation

We know that running a service is one part of running a cloud environment. Security, monitoring, backups, testing recovery and clear documentation are also essential.

This project is a lab proof of concept. Before you use it for university data you will need more work—add HTTPS, tighter network limits backups stored off the server restore tests, monitoring and a formal update and access‑control plan.
