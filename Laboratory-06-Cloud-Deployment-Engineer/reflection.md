# Mission 6 Reflection

This lab helped me see how Docker Compose makes it easier to set up a -container app. Of starting each container one by one and setting them up separately I used a YAML file to define Nextcloud and MariaDB. Having everything in one file made the setup cleaner and more organized. I could start both services with a single command.

I also found out that YAML indentation matters a lot. If I use tabs of spaces or if the spacing is off Docker Compose can’t read the file right. That leads to errors. Stops the app from starting. Because of this I now check the file’s structure. Formatting carefully before running any commands.

Environment variables like MYSQL_PASSWORD MYSQL_DATABASE. Give the containers the info they need to connect to the database. The MYSQL_HOST variable tells Nextcloud which database service to talk to.. I also learned that putting passwords directly in the Compose file is okay only for learning in class. In projects we need to handle passwords more safely.

Setting up Nextcloud was an experience. It showed me how different containers can work together to run a cloud storage app. I saw that the web app and the database each do their job but they still talk to each other as part of one system. When I opened the Nextcloud setup page in the browser I could see how a service inside a container can be reached from outside thanks to port mapping.

Since Mission 1 my understanding of cloud computing has grown. I started with ideas and now I’m actually building things. I’ve learned more about automation, containerization and Infrastructure as Code. This lab also taught me to test things fix problems when they come up write down commands and keep records. These are skills that will help me manage cloud apps better, in the future.
