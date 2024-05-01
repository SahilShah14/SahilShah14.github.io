---
layout: part1
title: Tutorial - Creating a Three-Tier Application using Docker
permalink: /part1/
---

<!-- Content for Docker part 3 -->

# Part 1 - Setting Up the Presentation Tier (Front End)

In this part of the tutorial, we will set up the frontend tier using React.js. 

## Step 1: Create the Front End Application 

For our presentation tier, we will create a simple web application using react. Let's name it "MyApp".

## Step 2: Dockerize theFront End

Create a Dockerfile for the front end to containerize the application.

```dockerfile
# Use the official Node.js image as the base image for building React app
FROM node:latest as build

# Set container name with roll number
ENV REACT_CONTAINER_NAME="myapp-frontend-21BCP111"

# Create and set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy frontend source code
COPY . .

# Build React app
RUN npm run build

# Use NGINX for serving React app
FROM nginx:alpine

# Copy build files from build stage
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Command to start NGINX
CMD ["nginx", "-g", "daemon off;"]
```
![Image](/images/image.png)

## Step 3: Build and Run the Docker Image

 ``` dockerfile
# Build the Docker image for front end
docker build -t myapp-frontend-21BCP111 .

# Run the Docker container
docker run -d --name react-frontend-21BCP107 -p 80:80 --network my-network react-frontend-21BCP107
```

![Image](/images/Screenshot 2024-04-23 115003.png)


![Image](/images/Screenshot 2024-04-23 115136.png)

## Step 4: Verify the Application

Open a web browser and navigate to http://localhost:8080 to see your application running.

## Conclusion

In this part of the tutorial, we successfully set up the presentation tier (front end) of our three-tier application using Docker. In the next part, we will proceed to create the application tier (back end) using Docker containers.

## Stay tuned for Part 2!
where we will create the application tier (back end) using Docker containers. 

## References:

Nginx Docker Hub: Official Nginx Docker image documentation.