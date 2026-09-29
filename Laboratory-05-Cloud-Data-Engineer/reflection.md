# Mission Reflection

## 1.	Why is object storage better suited for storing millions of photos compared to a traditional block storage hard drive?
This lab helped me understand why object storage is useful for applications that manage a large number of files, such as photos. Object storage is a good fit for millions of photos because it is designed for unstructured data and can store a very large number of files. It also makes organization easier by using buckets and objects.

## 2.	How did using Docker make it easier to deploy the MinIO storage server?
Using Docker made deploying MinIO simpler for me. Instead of setting everything up manually, I was able to run MinIO in a Docker container using a single command. I also learned how port mapping and environment variables work when running a container.

## 3.	What is a "bucket" in the context of cloud storage?
A bucket is basically a container where objects are stored in an object storage system. In this activity, I created a bucket named client-photos and used it to store my sample uploaded file. This helped me better understand how object storage organizes files.

## 4.	How do you think large enterprise companies ensure their object storage data is not lost if the physical server crashes?
Large companies can reduce the risk of data loss by keeping backups and storing multiple copies of important data. They can also use replication and redundant storage, so if one physical server fails, the data can still be retrieved from another copy or location.

## 5.	How is your confidence in navigating the Linux command line growing?
My confidence with the Linux command line is growing as well. At first, the Docker commands seemed complicated because they included many options and settings. After practicing commands like docker run and docker ps, I felt more comfortable working in the terminal. I also learned that if an image doesn’t work, I should review the Docker output and confirm which images are available instead of assuming Docker is broken right away.


