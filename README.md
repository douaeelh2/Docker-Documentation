# Docker-Documentation

![docker-img](https://github.com/douaeelh2/Docker-Documentation/assets/127549220/a78d7550-c788-492c-a0c8-817a3e87e1b0)

 This comprehensive guide is designed to help you understand and utilize Docker, an open platform for developing, shipping, and running applications inside containers. Whether you're a beginner getting started with containerization or an experienced user seeking advanced tips and tricks, this documentation covers everything you need to know to harness the power of Docker effectively.
 

# Table of Contents

1. [Introduction to Docker](#introduction-to-docker)
     - [What is Docker?](#what-is-docker?)
     - [What is Virtual Machine?](#what-is-virtual-machine?)
     - [Difference Between Docker Containers and Virtual Machines](#difference-between-docker-containers-and-virtual-machines)
     - [How Docker Works?](#how-docker-works)
2. [Installation](#installation)
3. [Docker Concepts](#docker-concepts)
    - [Docker Images](#docker-images)
    - [Docker Containers](#docker-containers)
    - [Docker Volumes](#docker-volumes)
    - [Parent Images](#parent-images)
    - [Dockerfile](#dockerfile)
    - [dockerignore](#dockerignore)
4. [Docker Usage](#docker-usage)
    - [Managing Images](#building-images)
    - [Managing Containers](#running-containers)
    - [Managing Volumes](#managing-volumes)
    - [Docker Compose](#docker-compose)
5. [References](#references)



# 1. Introduction to Docker

 - In software development, compatibility issues often arise when running applications due to differences in runtime environments, `dependencies`, and system configurations.
 - For example, running a `Node.js` application locally may encounter problems if the installed Node.js version differs from the one required by the application.These issues stem from missing `dependencies`, conflicting `libraries`, or differences in underlying `operating systems`. 

![what-is-docker](https://github.com/douaeelh2/Docker-Documentation/assets/127549220/e88adcee-0f8b-4914-ab35-96fd51e7e445)

  - Enter Docker – It allows developers to package applications and dependencies into portable containers, ensuring consistent execution across various systems.
  - Specifically in the Node.js scenario, Docker permits the creation of a containerized environment with the exact Node.js `version` and `dependencies` needed. By defining instructions in a `Dockerfile`, developers can specify the required environment and streamline development, mitigating compatibility issues and enhancing productivity.
   

![what-is-docker2](https://github.com/douaeelh2/Docker-Documentation/assets/127549220/870f54d7-bf87-481e-bc57-95bd947e1ea0)
    

  # What is Virtual Machine ?
  
  - A virtual machine or VM is a fully virtualized environment that runs on a physical machine. It runs its own operating system (OS) and benefits from the same equipment as a physical machine: CPU, RAM memory, hard drive and network card. Several virtual machines with different OS can coexist on the same physical server: Linux, MacOS, Windows, etc.
  - The sharing of different virtual environments is managed by the hypervisor generally hosted in a public cloud, private cloud or hybrid cloud. It performs resource partitioning and allocates a partition to each VM. This is done using software installed on the physical machine. In general, the latter has what is called a shared pool of physical resources.
   

  # What is Docker ?
  
  - Docker is an open-source platform designed to automate the deployment of applications inside containers. Containers are lightweight and portable environments that package an application and its dependencies, enabling it to run consistently across various computing environments, such as development, testing, and production.
  
  - Docker provides a standardized way to package, distribute, and manage applications, making it easier for developers to build, ship, and run their software across different systems and cloud environments. With Docker, developers can create containers containing all the necessary libraries, dependencies, and configurations needed to run their applications, without worrying about compatibility issues or differences in the underlying infrastructure.


  # Difference Between Docker Containers and Virtual Machines

  ![container-vs-vm](https://github.com/douaeelh2/Docker-Documentation/assets/127549220/a8e7f3d5-7a87-41ce-a94b-1d9dd8b17366)

| Aspect                   | Docker Containers                                                                                                  | Virtual Machines (VMs)                                                                                                |
|-------------------------|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Content                 | Contain binaries, libraries, and configuration files along with the application itself.                          | Each VM has its own copy of an operating system along with the application and necessary binaries.                      |
| Execution               | Run on a shared host operating system, utilizing the kernel of the underlying operating system.                   | Run on hypervisors, allowing multiple virtual machines to run on a single host machine.                                |
| Size and Resources      | Lightweight as they do not contain a guest OS for each container.                                                  | Larger as each VM has its own copy of an operating system, requiring more resources.                                    |
| Process Isolation       | OS-level process isolation.                                                                                        | Hardware-level process isolation.                                                                                       |
| Boot Time               | Quick boot time due to lightweight nature and resource sharing.                                                     | Slow boot time due to the need to boot up a complete operating system for each VM.                                       |



  ![container-vs-vm2](https://github.com/douaeelh2/Docker-Documentation/assets/127549220/231adc53-b67b-4af2-8a04-9e45ff5a8c9d)

 

 # Docker Architecture:
   Docker uses a `client-server` architecture. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers. The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon. The Docker client and daemon communicate using a REST API, over UNIX sockets or a network interface. Another Docker client is Docker Compose, that lets you work with applications consisting of a set of containers.

  ![docker-architecture](https://github.com/douaeelh2/Docker-Documentation/assets/127549220/498bfc3e-ccfd-4570-81a0-58be4083f01c)

   - `Docker Client:` The Docker Client is a command-line interface (CLI) tool that allows users to interact with the Docker Engine. Users can use commands such as docker build, docker run, docker pull, and docker push to build, run, and manage Docker containers.
   
   - `Docker Daemon:` The Docker Daemon is a background process that runs on the host machine and manages Docker objects such as images, containers, networks, and volumes. It listens for Docker API requests from the Docker Client and executes them.
   
   - `Docker Images:` Docker images are read-only templates used to create Docker containers. They contain everything needed to run an application, including the code, runtime, libraries, and dependencies.
   
   - `Docker Containers:` Docker containers are lightweight, portable, and isolated environments that run instances of applications. Each container is created from a Docker image and has its own filesystem, networking, and processes.
   
   - `Docker Registry:` Docker registries are repositories for storing and distributing Docker images. Docker Hub is the default public registry, but users can also set up private registries to store and share their own images.
   
   - `Docker Volumes:` Docker volumes are a way to persist data generated by Docker containers. They provide a mechanism for storing and sharing data between containers and the host machine.
   
   - `Docker Networks:` Docker networks allow containers to communicate with each other and with other network resources. They provide isolation and security by default, allowing users to define custom network configurations for their containers.

     

In Docker's client-server architecture, the process goes as follows:

  - `Docker client:` The process starts when the user uses the Docker client, which can be the Docker CLI command line or a Docker graphical user interface (GUI). The Docker client can be run on any Docker-enabled system, whether it is the same system as the Docker server or a remote system.
    
  - `Docker server:` Docker Server, also known as Docker Daemon, runs on a host system. It is the component responsible for managing Docker container operations. The Docker Daemon listens for requests from the Docker client.

  - `Client-server communication:` When the user sends a Docker command via the Docker client, it is transmitted to the Docker server via a communications protocol, often HTTPS or a Unix socket.
  - The Docker server receives the command, processes it, and returns the results to the Docker client.
  
  - `Operations management:`The Docker server handles operations such as building Docker images, starting and stopping containers, managing network and storage, etc.
  For example, if the user sends a command to run a container from a specific Docker image, the Docker server will check if the image is available locally. If it is not, it will download it from a Docker registry such as Docker Hub. Then it will create and start the container based on the parameters specified in the command.

  - `Response to client:` After the Docker server processes the command, it sends a response to the Docker client. This response may include information about the success or failure of the operation, additional details about the affected containers or images, etc.

# 2. Installation 
- [Docker Installation Crash Course](https://www.youtube.com/watch?v=8Ev1aXl7TGY&list=PL4cUxeGkcC9hxjeEtdHFNYMtCpjNBm3h7&index=2)

# 3. Docker Concepts

# Docker Images 
   - A Docker image is a lightweight, standalone, executable package that includes everything needed to `run` a piece of software, including the `code`, `runtime`, `libraries`, `environment variables`, and `configuration files`. It's essentially a snapshot of a Docker container. Docker images are built using a `Dockerfile` and can be stored in `registries`, such as `Docker Hub` or a private registry, for easy distribution and sharing among developers and systems.
   -  It's important to note that Docker images are `immutable`, meaning they do not change once created. To introduce changes, a new image needs to be created based on the desired modifications.
 
 ![docker-images](https://github.com/douaeelh2/Docker-Documentation/assets/127549220/0ebcd5e5-b17a-4fca-9cd6-f621ae7ff3e7)
 
# Docker Containers
 - A Docker container is a runtime `instance` of a Docker image. It encapsulates an application along with its dependencies and runs in isolated environments called containers.

    ![docker-containers](https://github.com/douaeelh2/Docker-Documentation/assets/127549220/28c4b633-971a-472e-8141-d7fc907b60ca)
 
 - Containers are lightweight, portable, and provide consistent environments across different deployment environments, ensuring that applications run consistently regardless of the underlying infrastructure.
 -  `Multiple containers` can run on the `same host` without interfering with each other, making them an ideal choice for microservices architectures and containerized applications.

   ![docker-containers2](https://github.com/douaeelh2/Docker-Documentation/assets/127549220/b9277bc8-c654-4e3f-9a23-732e8b029856)

# Parent Images

- In Docker, a parent image is an image from which another image is created. Each `Docker image` is made up of `layers`, which are `read-only` layers stacked on top of each other to form the complete image. These layers are created from the `Dockerfile` instructions when building the image.
  
  ![parent-image](https://github.com/douaeelh2/Docker-Documentation/assets/127549220/0f17b1a5-0fc9-469d-8b24-c64ad0f9369f)

- Parent images can be official images provided by Docker, such as those for popular programming languages like Python or Node.js, or they can be custom images created by users or organizations. These parent images often come pre-installed with certain dependencies, libraries, or configurations specific to a particular runtime environment.
  
  ![parent-image2](https://github.com/douaeelh2/Docker-Documentation/assets/127549220/f1906606-5fdc-4919-b6f9-c4587f9b7abb)

- Here are some examples of commonly used parent images in Docker:
   - `Python:` Used for Python applications, e.g., `python:3.8`, `python:3.9-alpine`.
   - `Node.js:` For Node.js applications, e.g., `node:14`, `node:alpine`.
   - `MySQL:` Database server, e.g., `mysql:8.0`.
     
# Dockerfile
   - A Dockerfile is a text file that contains a series of `instructions` used to build a `Docker image`. A Docker image is a lightweight, portable package that contains everything needed to run an application, including `code`, `libraries`, `dependencies`, and `environment variables`.
   
   - The Dockerfile defines the environment in which an application will run inside a Docker container. It specifies the steps needed to create the Docker image, such as which base to use, which `dependencies to install`, which `files to add`, which `commands to run`, etc.
   
   - Once the Dockerfile is written, it is used with the `docker build` command to build the Docker image. Once the image is created, it can be used to run containers, which are running instances of that image.
   - Here are Dockerfile examples for a React application and a Spring Boot application:

   ### Dockerfile for a React application

   ```dockerfile
     
       my-react-app/
       ├── node_modules/
       ├── public/
       │   ├── index.html
       │   └── ...
       ├── src/
       │   ├── components/
       │   │   ├── App.js
       │   │   └── ...
       │   ├── index.js
       │   └── ...
       ├── package.json
       └── .Dockerfile

   ```
     
   ```dockerfile
     
      # Use a Node.js image as the base
       FROM node:14-alpine
       
       # Set the working directory inside the container
       WORKDIR /app
       
       # Copy files from the host's current directory into the container
       COPY . .
       
       # Install dependencies
       RUN npm install
       
       # Build the React application
       RUN npm run build
       
       # Expose port 3000
       EXPOSE 3000
       
       # Default command to run the application when a container starts
       CMD ["npm", "start"]

   ```

 - The Dockerfile for the React application uses a `Node.js image` as the base, copies the application files into the `container`, installs `dependencies`, builds the application, and sets the default `command` to start the application.


   ### Dockerfile for a Spring Boot application

   ```
       your-spring-boot-app/
       ├── src/
       │   ├── main/
       │   │   ├── java/
       │   │   │   └── com/
       │   │   │       └── example/
       │   │   │           └── YourSpringBootApplication.java
       │   │   └── resources/
       │   │       └── application.properties
       │   └── test/
       │       └── java/
       │           └── com/
       │               └── example/
       │                   └── YourSpringBootApplicationTests.java
       ├── target/
       │   └── your-spring-boot-app.jar
       ├── pom.xml
       └── Dockerfile
   ```

   ```dockerfile
      # Use an OpenJDK image as the base
      FROM openjdk:11-jre-slim
      
      # Set the working directory inside the container
      WORKDIR /app
      
      # Copy the Spring Boot application JAR file into the container
      COPY target/your-spring-boot-app.jar .
      
      # Default command to run the application when a container starts
      CMD ["java", "-jar", "your-spring-boot-app.jar"]
   ```

   
    - The Dockerfile for the Spring Boot application uses an `OpenJDK image` as the base, copies the Spring Boot application `JAR file` into the `container`, and sets the default `command` to run the application.

# dockerignore
      
A `.dockerignore` file is used in Docker to specify files and directories that should be ignored when building a Docker image. Much like how a `.gitignore` file tells Git which files and directories to ignore when pushing code to a repository, a `.dockerignore` file specifies what Docker should ignore when building an image.

This is useful for excluding unnecessary files and directories from being included in the Docker image, which can help reduce the image size and improve build times. Common examples of files and directories that are often included in a `.dockerignore` file are temporary files, build artifacts, and `dependencies` that are not required for the application to run in a Docker container.

   ### dockerignore for a React application

   ```    
       my-react-app/
       ├── node_modules/
       ├── public/
       │   ├── index.html
       │   └── ...
       ├── src/
       │   ├── components/
       │   │   ├── App.js
       │   │   └── ...
       │   ├── index.js
       │   └── ...
       ├── package.json
       └── .dockerignore

   ```

   ```
      node_modules
       /build
       .DS_Store
   ```
   
   - `node_modules:` Excluded because dependencies are installed during the image build process.
   - `/build:` React typically generates a build directory when you build your project for production. This directory contains optimized production-ready files. Since you don't need these files in your development environment, they can be excluded.
   - `.DS_Store:` Excluded as it's a macOS-specific file.

# Docker Volumes
- In Docker, `volume` refers to a way to persist data generated by and used by Docker containers. Essentially, it allows you to share data between a container and the Docker host or between multiple containers. Volumes are often used for storing databases, configuration files, and other important data that needs to persist beyond the lifecycle of a single container.

### Volumes Advantages
- `Data persistence:` Volumes allow you to store data persistently, which is crucial for applications that require persistent storage, such as databases.

- `Sharing data between containers:` Volumes allow multiple Docker containers to share data efficiently. This facilitates communication and collaboration between the different components of an application.

- `Data isolation:` Docker volumes provide a way to isolate data from containers. This helps maintain container portability while ensuring sensitive data remains secure.

- `Performance:` Docker volumes generally offer good performance, making them a suitable choice for performance-demanding applications.

# 4. Docker Usage
# Managing Images

 ## 1. Building Images
- You build Docker images using a `Dockerfile`. The Dockerfile contains instructions on how to assemble the image. You can use the docker build command to build an image.

- Here's a basic example of a Dockerfile for a Node.js application:
  
   ```dockerfile
     FROM node:latest
     WORKDIR /app
     COPY package.json package-lock.json ./
     RUN npm install
     COPY . .
     EXPOSE 3000
     CMD ["node", "app.js"]
   ```
 
   ```bash
      $ docker build -t my-node-app .
      Sending build context to Docker daemon  3.072kB
      Step 1/5 : FROM node:14
      ...
      Successfully built ccb86e7a9d33
      Successfully tagged my-node-app:latest
   ```
   
- This command builds a Docker image named `my-node-app` using the Dockerfile in the current directory `./`.

 ## 2. Tagging an Image
- Tagging helps you identify specific versions of your image. You can tag images with version numbers, labels, or any other meaningful identifier. To tag the image you just built:

- Let's take the same example for a Node.js application:
  
 ```bash
    $ docker tag my-node-app:latest my-registry/my-node-app:v1.0
 ```
- This command tags the `my-node-app` image with the version `v1.0`, ready to be pushed to your Docker registry (replace `my-registry` with your actual Docker registry URL).


## 3. Pushing an Image
Once you've tagged your image, you can push it to a Docker registry to make it accessible to other users or servers:
    
   ```bash
      $ docker push my-registry/my-node-app:v1.0
   ```
- This command pushes the tagged image `my-node-app:v1.0` to your Docker `registry`.

## 4. Pulling an Image
To pull an image from a registry, you can use the docker pull command:
    
  ```bash
     $ docker pull node:14
     14: Pulling from library/node
     ...
     Digest: sha256:3e5e8b3d930f004c7a5cb0f11e8db58f3f5a8d89b2de898e386998b97cd18864
     Status: Downloaded newer image for node:14
  ```

  ```bash
     $ docker pull mysql
  ```
 - This command pulls the latest `MySQL image` from Docker Hub. By default, it pulls the `latest` version. If you want to specify a particular version, you can do so by appending the version tag after the image name, like `docker pull mysql:8.0`.

## 5. Remove an Image

   ```bash
      $ docker rmi my-node-app
      Untagged: my-node-app:latest
      Deleted: sha256:ccb86e7a9d33f97d75a4c06a5bde028e45e586a38b242e5be1a57b55c7f87851
  ```
## 5. Listing images

  ```
  $ docker images
  REPOSITORY                TAG       IMAGE ID       CREATED       SIZE
  my-node-app               latest    ccb86e7a9d33   2 hours ago   944MB
  my-registry/my-node-app   v1.0      ccb86e7a9d33   2 hours ago   944MB
  node                      14        56d8f5a52c2a   3 days ago    944MB
  ```

# Managing Containers
## 1. Creating a container

  ```bash
     docker run --name my-node-container my-node-app
  ```
- This command creates and starts a new container named `my-node-container` from the `my-node-app` image.

## 2. Starting a container

  ```bash
     $ docker start my-node-container
     my-node-container
  ```

## 3. Stopping a container

  ```bash
     $ docker stop my-node-container
     my-node-container
  ```
  
## 4. Restarting a container

  ```bash
     $ docker restart my-node-container
     my-node-container
  ```

## 5. Pausing a container

  ```bash
     $ docker pause my-node-container
     my-node-container
  ```

## 6. Resuming a container

  ```bash
     $ docker unpause my-node-container
     my-node-container
  ```
## 7. Removing a container

  ```bash
     $ docker rm my-node-container
     my-node-container
  ```
## 6. Listing containers
- The `docker ps` command lists only running containers. If no containers are running, it will output nothing.
   
  ```bash
     $ docker ps
     CONTAINER ID   IMAGE            COMMAND                  CREATED          STATUS        PORTS      NAMES
     35b9a383ff6f   my-node-app     "node server.js"         2 minutes ago     Up 1 minute             my-node-container
     c3abf8d84f2c   nginx:latest    "/docker-entrypoint.."   3 hours ago       Up 3 hours    80/tcp    my-nginx-container
  ```
  
- The `docker ps -a` command lists all containers, including those that have exited. Each row represents a container and includes information such as the container ID, image used to create the container, command executed in the container, creation time, status, exposed ports, and container name.
  
  ```bash
   $ docker ps -a
   CONTAINER ID   IMAGE             COMMAND                  CREATED         STATUS                      PORTS     NAMES
   35b9a383ff6f   my-node-app       "node server.js"        2 minutes ago   Exited (0) 1 minute ago               my-node-container
   c3abf8d84f2c   nginx:latest      "/docker-entrypoint...."   3 hours ago     Up 3 hours               80/tcp    my-nginx-container
   e7b6f198d82a   ubuntu:latest     "/bin/bash"              3 hours ago     Exited (0) 3 hours ago               my-ubuntu-container
  ```

# Managing Volumes

## 1. Creating a Volume
 - create a Docker volume named `mysql_data` using the docker volume create command
   
  ```bash
     docker volume create mysql_data
  ```

## 2. Running MySQL Container with a Volume
  - run a Docker container for MySQL and mount the `mysql_data` volume to the directory where MySQL stores its data (typically `/var/lib/mysql`). You also specify the MySQL root password using the `MYSQL_ROOT_PASSWORD` environment variable
    
 ```bash
    docker run -d --name mysql-db -e MYSQL_ROOT_PASSWORD=my-secret-password -v mysql_data:/var/lib/mysql mysql:latest
  ```

## 3. Remove Volume

  ```bash
    docker volume rm mysql_data
  ```

## 4. List Volumes
    
  ```bash
    docker volume ls
  ```

## 5. Inspect Volume 
- If you want to inspect the details of the `mysql_data` volume, you can use the docker volume inspect command followed by the volume name:

  ```bash
     docker volume inspect mysql_data
  ```

## 6. Prune Unused Volumes 
- If you have `unused volumes` taking up disk `space`, you can prune them using the docker volume prune command:
  
  ```bash
     docker volume prune
  ```

# Docker Compose
- `Docker Compose` is a tool used for defining and running `multi-container` Docker applications. It allows you to define the `services`, `networks`, and `volumes` required for your application in a single `YAML` file. With Docker Compose, you can configure the different services that make up your application, set their dependencies and relationships, specify environment variables, expose ports, and more. Once the configuration is set up in the `docker-compose.yml` file, you can use simple commands to start, stop, and manage your entire application stack with a single command. This makes it easier to manage complex applications that consist of multiple interconnected containers.

- Here's an example of a Docker Compose setup for a multi-container application with React frontend, Spring backend, and MySQL database
  
  ```bash
     project/
     ├── frontend/
     │   └── Dockerfile
     ├── backend/
     │   └── Dockerfile
     ├── docker-compose.yml
     └── ...
  ```
- ## frontend/Dockerfile

  ```dockerfile
     # Use an official Node runtime as the base image
     FROM node:14
     
     # Set the working directory in the container
     WORKDIR /app
     
     # Copy package.json and package-lock.json to the container
     COPY package*.json ./
     
     # Install dependencies
     RUN npm install
     
     # Copy the rest of the application code
     COPY . .
     
     # Expose port 3000 to the outside world
     EXPOSE 3000
     
     # Command to run the application
     CMD ["npm", "start"]
  ```

- ## backend/Dockerfile
  
  ```dockerfile
     # Use an official OpenJDK runtime as the base image
     FROM openjdk:11
     
     # Set the working directory in the container
     WORKDIR /app
     
     # Copy the jar file into the container
     COPY target/backend.jar .
     
     # Expose port 8080 to the outside world
     EXPOSE 8080
     
     # Command to run the application
     CMD ["java", "-jar", "backend.jar"]
  ```

- ## docker-compose.yml


  ```yml
    version: '3.8'
    services:
      frontend:
        container_name: frontend_c
        build: ./frontend
        ports:
          - "3000:3000"
        depends_on:
          - backend
    
      backend:
        container_name: backend_c
        build: ./backend
        ports:
          - "8080:8080"
        depends_on:
          - database
    
      database:
        container_name: database_c
        image: mysql:latest
        restart: always
        environment:
          MYSQL_ROOT_PASSWORD: example
          MYSQL_DATABASE: mydatabase
          MYSQL_USER: myuser
          MYSQL_PASSWORD: example
        ports:
          - "3306:3306"

  ```
  
- The `docker-compose.yml` file defines three services: frontend, backend, and database.
- Each service specifies its build context (where the `Dockerfile` is located), any ports to expose, and any dependencies it has on other services.
- Dependencies are managed by Docker `Compose`, ensuring that services start in the correct order.
- The `docker-compose up` command will spin up all three containers, networking them together as specified in the YAML file.




# 5. References 
- [GeeksforGeeks](https://www.geeksforgeeks.org/)
- [Docs.Docker](https://docs.docker.com/)
- [Docker Crash Course](https://www.youtube.com/watch?v=31ieHmcTUOk&list=PL4cUxeGkcC9hxjeEtdHFNYMtCpjNBm3h7&index=1)
