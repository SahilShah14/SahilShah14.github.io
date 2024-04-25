---
layout: part1
title: Part 1 - Setting Up the Database Tier
permalink: /part1/
---

<!-- Content for Docker part 1 -->

# Part 1 - Setting Up the Database Tier with MongoDB

In this part of the tutorial, we will set up the database tier using MongoDB.

## Step 1: Dockerfile for MongoDB

```dockerfile
# Use the official MongoDB image as the base image
FROM mongo:latest

# Set container name with roll number
ENV MONGO_CONTAINER_NAME="mongodb-21BCP107"
```

![Image](/images/Screenshot 2024-04-23 110138.png)

## Step 2: building and running the database

```dockerfile
# Build the Docker image for MongoDB
docker build -t mongodb-21BCP107 .

# Run the MongoDB container
docker run -d --name mongodb-21BCP107 -p 27017:27017 mongodb-21BCP107

```
![Image](/images/Screenshot 2024-04-23 114000.png)



## Step 3: Connecting MongoDB Container to Network
```dockerfile
# Create a Docker network
docker network create my-network

# Connect MongoDB container to the network
docker network connect my-network mongodb-21BCP107
```

![Image](/images/Screenshot 2024-04-23 114134.png)

![Image](/images/Screenshot 2024-04-23 114256.png)