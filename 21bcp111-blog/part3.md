---
layout: part3
title: Tutorial - Creating a Three-Tier Application using Docker (Part 3)
permalink: /part3/
---

<!-- Content for Docker part 1 -->

# Part 3 - Setting Up the Data Tier (Database)

Welcome back to the final part of our tutorial series! In this part, we will create the data tier (database) of our three-tier application using Docker containers.

## Step 1: Choose a Database Management System

You can choose PostgreSQL, MongoDB, MySQL etc.
For our data tier, we will choose MongoDB, a powerful open-source relational database management system.

## Step 2: Dockerize the DataBase

```dockerfile
#Let's create a docker-compose.yml file to define our MongoDB database service.

# Use the official MongoDB image as the base image
FROM mongo:latest

# Set container name with roll number
ENV MONGO_CONTAINER_NAME="mongodb-21BCP111"
```

![Image](/images/Screenshot 2024-04-23 110138.png)

## Step 3: Build and Run the Docker Containers

```dockerfile
# Build the Docker image for MongoDB
docker build -t mongodb-21BCP111 .

# Run the MongoDB container
docker run -d --name mongodb-21BCP111 -p 27017:27017 mongodb-21BCP111

```
![Image](/images/Screenshot 2024-04-23 114000.png)



## Step 4: Connecting MongoDB Container to Network
```dockerfile
# Create a Docker network
docker network create my-network

# Connect MongoDB container to the network
docker network connect my-network mongodb-21BCP111
```

![Image](/images/Screenshot 2024-04-23 114134.png)

![Image](/images/Screenshot 2024-04-23 114256.png)

## Thank you for visiting the documentation

## Conclusion

Congratulations! You have successfully set up all three tiers of your application using Docker containers. The presentation tier (front end), application tier (back end), and data tier (database) are now running as separate containers.

## References:
PostgreSQL Docker Hub: Official PostgreSQL Docker image documentation.

## Thank you for following along with this tutorial series!