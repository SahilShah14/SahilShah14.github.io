---
layout: part2
title: Tutorial - Creating a Three-Tier Application using Docker (Part 2)
permalink: /part2/
---

<!-- Content for Docker part 2 -->

# Part 2 - Setting Up the Application Tier (Back End)

Welcome back to the continuation of our tutorial series! In this part, we will proceed to create the application tier (back end) of our three-tier application using Docker containers.

## Step 1: Choose a Backend Framework

For our application tier, we will choose a backend framework to handle business logic and interact with the database. You can use Flask, a lightweight Python web framework or node.js which is commonly used for server-side programming.

## Step 2: Dockerize for Application

```dockerfile
# Use the official Node.js image as the base image
FROM node:latest

# Set container name with roll number
ENV NODE_CONTAINER_NAME="myapp-backend-21BCP111"

# Create and set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy backend source code
COPY . .

# Expose port 5000
EXPOSE 5000

# Command to run the backend server
CMD ["node", "server.js"]
```

![Image](/images/Screenshot 2024-04-23 114417.png)


## Step 3: Define Dependencies (if Using Flask)

Create a requirements.txt file listing the dependencies for our Flask application.

```requirements.txt
Flask==2.0.2
```

## Step 4: Build and Run the Docker Image

``` dockerfile

# Build the Docker image for the application tier
docker build -t myapp-backend-21BCP111 .

# Run the Docker container
docker run -d -p 5000:5000 myapp-backend-21BCP111

```
![Image](/images/Screenshot 2024-04-23 114557.png)

## Step 5: Verify the Application

You can verify that the Flask application is running by navigating to http://localhost:5000 in your web browser.

## Conclusion

In this part of the tutorial, we successfully set up the application tier (back end) of our three-tier application using Docker containers. In the next part, we will proceed to create the data tier (database) using Docker containers.

## Stay tuned for Part 3!
where we will create the data tier (database) using Docker containers.

GitHub Repository Link for Dockerfiles: Link to GitHub Repository