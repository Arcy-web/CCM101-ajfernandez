## Our Learning Experience

Our group studied cloud computing deeply. We saw how it works in IT settings. At first we learned the basic ideas of cloud services, deployment models and different cloud platforms. As we did lab work we began to use tools that helped us see how cloud infrastructure really runs.

One key lesson was that cloud computing is not about storing files online. It also covers managing servers, networks, applications, databases, security and backups. Each lab gave us a picture of how these parts fit together.

## Skills We Developed

During the activities we practiced GitHub documentation Linux commands, Docker containers and cloud storage ideas. We also learned the differences between block, file and object storage. Why picking the right type depends on what the project needs.

In the lab we set up Nextcloud with MariaDB using Docker Compose. We made volumes so that data stayed after a container stopped. We also set up UFW to limit connections and wrote a Bash script that makes compressed database backups.

These tasks showed us how important it is to plan a deployment not just to get the application running.

## Challenges We Encountered

One challenge was figuring out how the different parts talk to each other. We had to watch the Docker Compose file database environment variables, network settings and how the virtual machine talks to the host computer.

We also discovered that a working application still needs security and maintenance. Firewall rules must allow needed connections credentials must stay private and backups must be checked, not just assumed to work.

These challenges taught us to read logs check configuration files test commands carefully and solve problems step by step.

## Importance of Security and Maintenance

Our project made us realize that deploying a private cloud system is only the start. It also needs monitoring, updates, secure access, persistent storage and a solid recovery plan.

We learned that database backups alone do not bring back a Nextcloud environment because uploaded files and settings also need protection. In a deployment we would add HTTPS keep backups outside the virtual machine, test restoration often and limit access to trusted networks.

## Application to Future Projects

The knowledge we gained from these missions can help us in system administration, backend development and cloud infrastructure work. Knowing containers, databases, networking and automation also helps us troubleshoot better.

As IT students we learned that a successful deployment needs patience, good documentation, teamwork and constant testing. We still have more to learn. These activities gave us a stronger base, for working with cloud technologies.
