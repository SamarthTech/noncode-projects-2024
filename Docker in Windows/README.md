# Docker in Windows  

## Table of Contents  
1. [Introduction to Docker](#1-introduction-to-docker)  
2.  [System Requirements](#2-system-requirements)  
3. [Installing Docker on Windows](#3-installing-docker-on-windows)  
    - 3.1. [Enable WSL 2](#31-enable-wsl-2)  
    - 3.2. [Install Docker Desktop](#32-install-docker-desktop)  
4. [Basic Docker Commands](#4-basic-docker-commands)  
    - 4.1. [Pull an Image](#41-pull-an-image)  
    - 4.2. [Run a Container](#42-run-a-container)  
    - 4.3. [List Running Containers](#43-list-running-containers)  
    - 4.4. [Stop a Container](#44-stop-a-container)  
    - 4.5. [Remove a Container](#45-remove-a-container)  
    - 4.6. [List Downloaded Images](#46-list-downloaded-images)  
    - 4.7. [Remove an Image](#47-remove-an-image)  
5. [Using Docker with WSL 2](#5-using-docker-with-wsl-2)  
6. [Docker Compose](#6-docker-compose)  
7. [Networking in Docker](#7-networking-in-docker)  
8. [Volumes: Persistent Storage](#8-volumes-persistent-storage)  
9. [Building Docker Images](#9-building-docker-images)  
10. [Using Docker Hub](#10-using-docker-hub)  
11. [Docker and Kubernetes](#11-docker-and-kubernetes)  
12. [Best Practices for Docker](#12-best-practices-for-docker)  
13. [Troubleshooting Common Issues](#13-troubleshooting-common-issues)  
14. [Advanced Docker Concepts](#14-advanced-docker-concepts)  
    - 14.1. [Dockerfile Best Practices](#141-dockerfile-best-practices)  
    - 14.2. [Docker Compose Advanced Usage](#142-docker-compose-advanced-usage)  
    - 14.3. [Docker Networking Advanced](#143-docker-networking-advanced)  
    - 14.4. [Security Best Practices](#144-security-best-practices)  
15. [Troubleshooting Docker](#15-troubleshooting-docker)  
    - 15.1. [Common Errors and Solutions](#151-common-errors-and-solutions)  
    - 15.2. [Checking Container Logs](#152-checking-container-logs)  
    - 15.3. [Docker System Prune](#153-docker-system-prune)  
16. [Docker Performance Optimization](#16-docker-performance-optimization)  
    - 16.1. [Reducing Image Size](#161-reducing-image-size)  
    - 16.2. [Improving Build Speed](#162-improving-build-speed)  
    - 16.3. [Resource Limits](#163-resource-limits)  
    - 16.4. [Use Multi-Stage Builds](#164-use-multi-stage-builds)  
17. [Monitoring and Logging](#17-monitoring-and-logging)  
    - 17.1. [Docker Stats](#171-docker-stats)  
    - 17.2. [Integrating with Monitoring Tools](#172-integrating-with-monitoring-tools)  
18. [Orchestration with Docker Swarm and Kubernetes](#18-orchestration-with-docker-swarm-and-kubernetes)  
    - 18.1. [Docker Swarm](#181-docker-swarm)  
    - 18.2. [Kubernetes](#182-kubernetes)  
    - 18.3. [Scaling Services](#183-scaling-services)  
19. [CI/CD with Docker](#19-cicd-with-docker)  

---

## 1. Introduction to Docker  
Docker is a platform that allows you to automate the deployment of applications inside lightweight, portable containers. Containers include everything needed to run the application, ensuring consistency across different environments.  

## 2. System Requirements  
- **Windows 10/11 64-bit:** Pro, Enterprise, or Education versions (Docker requires **Hyper-V**, which is not available in Home editions, though Docker Desktop now has support for WSL 2).  
- **WSL 2 (Windows Subsystem for Linux 2):** Recommended for better performance.  
- **4GB RAM** (minimum).  

## 3. Installing Docker on Windows  
### 3.1. Enable WSL 2  
Docker Desktop leverages WSL 2 to provide a more efficient and faster experience. Enable WSL 2 by following these steps: 
- Open PowerShell as Administrator and run:  
```bash
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```
```bash
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
- Restart your computer.  
- Install the WSL 2 Kernel by downloading the [WSL 2 Linux Kernel update package](https://learn.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package) and following the instructions.  
- Set WSL 2 as the default version:  
```bash
wsl --set-default-version 2
```
- Install a Linux distribution from the Microsoft Store (e.g., Ubuntu).  
### 3.2. Install Docker Desktop  
- Download Docker Desktop from [Docker's official website](https://www.docker.com/products/docker-desktop/).  
- Run the installer, select **WSL 2 based engine**, and follow the installation instructions.  
- Once installed, open Docker Desktop. You should see the Docker icon in your system tray.  
- Verify installation by opening a terminal (CMD or PowerShell) and typing:  
```bash
docker --version
```
You should see Docker's version information.  
## 4. Basic Docker Commands  
Here are some key Docker commands you'll use frequently:  
### 4.1. Pull an Image  
```bash
docker pull <image_name>
```
Example:  
```bash
docker pull nginx
```
### 4.2. Run a Container  
```bash
docker run -d -p <host_port>:<container_port> <image_name>
```
Example:  
```bash
docker run -d -p 80:80 nginx
```
### 4.3. List Running Containers  
```bash
docker ps
```
### 4.4. Stop a Container  
```bash
docker stop <container_id>
```
### 4.5. Remove a Container  
```bash
docker rm <container_id>
```
### 4.6. List Downloaded Images  
```bash
docker images
```
### 4.7. Remove an Image  
```bash
docker rmi <image_id>
```

## 5. Using Docker with WSL 2  
Docker Desktop integrates with WSL 2, allowing you to use Linux containers natively on Windows. Here's how you can configure Docker with WSL 2:  
- Open **Docker Desktop** and go to `Settings` > `General`. Ensure that **Use the WSL 2 based engine is checked**.  
- In `Settings` > `Resources` > `WSL Integration`, select the distributions (e.g., Ubuntu) you want Docker to integrate with.  
- Restart Docker Desktop and open your WSL 2 distribution (e.g., Ubuntu) from the terminal.  
- You can now run Docker commands directly inside WSL 2. Example:  
```bash
docker run hello-world
```
## 6. Docker Compose  
Docker Compose is a tool for defining and running multi-container Docker applications. Here's how you can use it:  
- Create a `docker-compose.yml` file for your application. Example:  
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "80:80"
```
- In the terminal, navigate to the directory containing the `docker-compose.yml` file and run:  
```bash
docker-compose up
```
- This command starts all services defined in the file. To stop them, use:  
```bash
docker-compose down
```
## 7. Networking in Docker  
Docker containers are isolated, but you can allow them to communicate with each other or the host machine:  
- **Host to container:** Map ports when starting the container:  
```bash
docker run -d -p <host_port>:<container_port> <image_name>
```
- **Container to container:** Use Docker networks to allow containers to communicate. For example, to create a bridge network:  
```bash
docker network create my-network
docker run -d --network my-network --name web nginx
docker run -d --network my-network --name db mysql
```
Now the containers `web` and `db` can communicate via the network `my-network`.  
## 8. Volumes: Persistent Storage  
Docker containers are ephemeral, meaning data inside a container is lost when the container is stopped or removed. To persist data, use **Docker volumes**.  
- Create a volume:  
```bash
docker volume create my-volume
```
- Mount the volume in a container:  
```bash
docker run -d -v my-volume:/path/in/container nginx
```
## 9. Building Docker Images  
To create your own Docker image, you need to write a `Dockerfile`:  

Example `Dockerfile`:  
```Dockerfile
# Use an official image as a base
FROM node:14

# Set the working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package.json ./
RUN npm install

# Copy the rest of the code
COPY . .

# Expose the application port
EXPOSE 3000

# Command to start the app
CMD ["npm", "start"]
```
Build the Image:  
```bash
docker build -t my-node-app .
```
Run the Image:  
```bash
docker run -p 3000:3000 my-node-app
```
## 10. Using Docker Hub  
Docker Hub is a registry where you can find and share container images:  
- Login to Docker Hub:  
```bash
docker login
```
- Push an image to Docker Hub: Tag your image and push it to Docker Hub:  
```bash
docker tag my-node-app username/my-node-app
docker push username/my-node-app
```
## 11. Docker and Kubernetes  
As you advance, you can use Docker with Kubernetes for container orchestration. Kubernetes helps manage multiple containers, scaling, and deployments in production environments. Docker Desktop has built-in Kubernetes support, which can be enabled in `Settings` > `Kubernetes`.  

## 12. Best Practices for Docker  
- Keep images small by using multi-stage builds and minimal base images.  
- Use `.dockerignore` files to avoid including unnecessary files.  
- Clean up unused images and containers with:  
```bash
docker system prune
```

## 13. Troubleshooting Common Issues  
- **WSL 2 integration issues:** Make sure your Docker Desktop is configured to use WSL 2 and that your Linux distribution is installed and running properly.  
- **Out of space:** Clear unused containers, images, and volumes using:  
```bash
docker system prune
```
- **Networking issues:** If containers can’t communicate with the host, ensure the ports are properly exposed and mapped.  

## 14. Advanced Docker Concepts
### 14.1. `Dockerfile` Best Practices  
When creating Docker images, following best practices ensures your images are lightweight, efficient, and easy to maintain.  
- Use Minimal Base Images  
    - **Alpine Linux** is a popular base image because it is very small (~5 MB). 
    ```Dockerfile
    FROM alpine
    ```
- Multi-Stage Builds  
    - **Multi-stage builds** help reduce image size by separating build dependencies from runtime dependencies:  
    ```Dockerfile
    # Stage 1: Build
    FROM golang:alpine AS build
    WORKDIR /app
    COPY . .
    RUN go build -o myapp

    # Stage 2: Runtime
    FROM alpine
    COPY --from=build /app/myapp /app/myapp
    ENTRYPOINT ["/app/myapp"]
    ```
- Layer Caching  
    - Docker caches each layer in a Dockerfile. Organize layers in a way that prevents invalidating cache unnecessarily:  
    ```Dockerfile
    # Separate frequently changing layers from the rarely changing ones
    COPY package.json /app
    RUN npm install
    COPY . /app
    ```
- Use `.dockerignore`
    - Use a `.dockerignore` file to exclude files from being copied into the Docker image, which reduces the image size:  
    ```.dockerignore
    node_modules
    .git
    ```

### 14.2. Docker Compose Advanced Usage  
- Environment Variables  
    - You can define environment variables inside the `docker-compose.yml` file or in a separate `.env` file:  

    ```yaml
    version: '3'
    services:
        app:
        image: myapp
        environment:
            - ENV_VAR=value
    ```
    - Example `.env` file:  
    ```makefile
    ENV_VAR=value
    ```
- Using Volumes for Development  
    - Mount your local code as a volume for development so changes reflect instantly:  
    ```yaml
    version: '3'
    services:
  app:
    image: myapp
    volumes:
      - ./src:/app/src
    ports:
      - "3000:3000"
    ```
### 14.3. Docker Networking Advanced  
Docker offers multiple networking options to help containers communicate with each other and the outside world:  

- **Bridge Network**  
    - The default network Docker creates. Use it to allow isolated containers to communicate.  
    ```bash
    docker network create my-bridge-network
    docker run -d --network my-bridge-network --name web nginx
    ```
- **Host Network**  
    - The host network shares the same network interface as the host machine (mainly for Linux). Useful for performance-critical applications.  
    ```bash
    docker run --network host nginx
    ```
- **Overlay Network**  
    - Used when orchestrating containers across multiple Docker hosts, usually in Docker Swarm or Kubernetes environments.  

### 14.4. Security Best Practices  
Security is a critical aspect of working with containers. Here are some key practices to follow:  
- Limit Privileges  
    - Avoid running containers as `root`. Use the `USER directive` in your `Dockerfile`:  

    ```Dockerfile
    USER nonroot
    ```
- Use Trusted Images  
    - Always pull images from trusted sources and verify the image’s integrity:  
    ```bash
    docker pull nginx:alpine
    ```
-  Use Secrets for Sensitive Data  
    - Avoid hardcoding sensitive information (e.g., API keys) in Dockerfiles or `docker-compose.yml`. Instead, use Docker secrets:  
    ```bash
    docker secret create my_secret ./secret_file
    ```
## 15. Troubleshooting Docker  
### 15.1. Common Errors and Solutions  
Error: docker: `Cannot connect to the Docker daemon`  
- Solution: Ensure Docker is running. Restart Docker Desktop or run the following command:  
```bash
sudo service docker start
```
Error: Mount denied: `The source path does not exist`  
- Solution: Ensure the source path you’re trying to mount is correct. For Windows, use the correct path format (e.g., `c/Users/username/...` instead of `C:\Users\username`).  

### 15.2. Checking Container Logs  
If a container is failing to start, check the logs to diagnose the issue:  
```bash
docker logs <container_id>
```
###  15.3. Docker System Prune  
When Docker consumes too much disk space, run the following to remove all stopped containers, unused networks, dangling images, and build caches:  
```bash
docker system prune -a
```

## 16. Docker Performance Optimization  
### 16.1. Reducing Image Size  
- Use a smaller base image like Alpine Linux or Distroless.  
- Minimize the number of layers in your Dockerfile.  
### 16.2. Improving Build Speed  
- Take advantage of Docker’s caching by ordering commands that change less frequently at the top of the Dockerfile (e.g., `COPY package.json` before copying the rest of the code).  
### 16.3. Resource Limits  
- To prevent containers from consuming all system resources, set CPU and memory limits:  
```bash
docker run -d --memory="256m" --cpus="1.5" nginx
```
### 16.4. Use Multi-Stage Builds  
- Split your builds into multiple stages to include only the necessary files in the final image.  

## 17. Monitoring and Logging  
### 17.1. Docker Stats  
You can monitor resource usage for running containers using:  
```bash
docker stats
```
### 17.2. Integrating with Monitoring Tools  
- **Prometheus** and **Grafana**: You can use these tools for advanced container monitoring and visualizing performance metrics.  
- **ELK Stack**: Combine **Elasticsearch**, **Logstash**, and **Kibana** to manage logs generated by your Docker containers.  

## 18. Orchestration with Docker Swarm and Kubernetes  
### 18.1. Docker Swarm  
Docker Swarm provides built-in orchestration for managing containers in a cluster. You can deploy your containers as services across multiple nodes:  
```bash
docker swarm init
docker service create --name my-web -p 80:80 nginx
```
### 18.2. Kubernetes  
Kubernetes is an advanced orchestration tool that is widely adopted for managing containerized applications at scale. Docker Desktop includes Kubernetes, which you can enable in `Settings` > `Kubernetes`.  
### 18.3. Scaling Services  
Scale services in Docker Swarm or Kubernetes to handle more load:  
```bash
docker service scale my-web=5
```

## 19. CI/CD with Docker  
Integrating Docker into your CI/CD pipeline automates building, testing, and deploying containerized applications. Popular CI/CD tools like **Jenkins**, **GitLab CI**, and **CircleCI** support Docker:  
- Define a Dockerfile for your application.  
- Use the Docker image to run tests.  
- Push the image to a Docker registry (**Docker Hub**, **GitHub Container Registry**).  
- Deploy the image in production via Docker Swarm or Kubernetes.  

Example CI/CD Pipeline (GitLab CI):  
```yaml
stages:
  - build
  - test
  - deploy

build:
  stage: build
  script:
    - docker build -t my-app .

test:
  stage: test
  script:
    - docker run my-app npm test

deploy:
  stage: deploy
  script:
    - docker push my-app
```
---
For  more information on Docker, visit the [Official Docker documentation](https://docs.docker.com/).

---
