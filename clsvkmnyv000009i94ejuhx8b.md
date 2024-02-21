---
title: "Demystifying Docker: A Comprehensive Guide to Containerization 🐳"
datePublished: Wed Feb 21 2024 09:07:32 GMT+0000 (Coordinated Universal Time)
cuid: clsvkmnyv000009i94ejuhx8b
slug: demystifying-docker-a-comprehensive-guide-to-containerization
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708506327498/6229ecd1-699c-4a09-8cd5-e5d7f07a48a1.jpeg
tags: linux, docker, aws, devops, 90daysofdevops

---

**What is Docker?** 🐳 Docker is a containerization platform that simplifies the process of containerizing applications. It allows you to build container images and run them to create containers.

**What is Docker Daemon?** 🔧 The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. It can also communicate with other daemons to manage Docker services.

**Docker Architecture** 🏗️ Docker follows a Client-Server architecture with three main components:

* **Docker Client**: Uses commands and REST APIs to communicate with the Docker Daemon.
    

```plaintext
docker build
docker pull
docker run
```

* **Docker Host**: Provides an environment to execute and run applications, containing the Docker daemon, images, containers, networks, and storage.
    
* **Docker Registry**: Manages and stores Docker images, including public (Docker Hub) and private registries.
    

1. Pubic Registry - Public Registry is also called as Docker hub.
    
2. Private Registry - It is used to share images within the enterprise
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708502642763/8008d8ad-3528-4e1a-9a0f-53c8c3291c83.jpeg align="center")

**Docker Images** 🖼️ Docker images are read-only templates with instructions to create Docker Containers. They can be shared within an enterprise using private registries or globally via public registries.

**Docker Containers** 📦 Containers are the units used to run applications, containing all necessary components. They are lightweight and require minimal resources.

**Docker Networking** 🌐 Docker offers various network drivers, including:

* Bridge: Default for communication between multiple containers on the same host.
    

```plaintext
docker network create -d bridge my_bridge
docker run -d --net=my_bridge --name db training/postgres
```

* Host: For no network isolation between container and host.
    

```plaintext
docker run --network="host" <image_name> <command>
```

* None: Disables all networking.
    
* Overlay: Enables containers to run on different Docker hosts in a Swarm.
    
* Macvlan: Assigns MAC addresses to containers.
    

**Docker Storage** 💾 Docker Storage options include:

* Data Volume: Provides persistence storage and allows naming and listing volumes.
    

```plaintext
docker volume create my-vol
docker run -d --mount source=my-vol,target=/app -- name my-cont2 nginx
cat /var/lib/docker/volumes/my-vol/
```

* Directory Mounts: Mounts a host's directory into a container.
    

```plaintext
# Create a directory on the host
mkdir /path/on/host
docker run -v /path/on/host:/path/in/container some-image
```

* Storage Plugins: Connects to external storage platforms.
    

**What is a Container?** 🛡️ A container is a standardized unit of software that packages code and its dependencies for quick and reliable application deployment across different environments.

**Why are Containers Lightweight?** 🏋️‍♂️ Containers are lightweight because they include only necessary components, avoiding operating system images present in traditional virtualization approaches.

Let's try to understand this with an example:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708503206128/fc7eecde-0e49-4861-84a1-63864c33fc08.png align="center")

*ubuntu base image which you can use for your container. It's just ~ 22 MB, official ubuntu VM image it will be close to ~ 2.3 GB*

**Docker Lifecycle** 🔄 Docker lifecycle involves building images from Docker files, running containers from images, and pushing images to public/private registries for sharing.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708503501741/3fc32408-e53d-4e9d-9a9b-ae5e9cced3e5.png align="center")

**Install Docker** 🔧 Install Docker on an Ubuntu EC2 Instance using commands, start Docker daemon, and grant access to users.

```plaintext
sudo apt update
sudo apt install docker.io –y
```

**Start Docker and Grant Access**

Docker installation is by running the below command

```plaintext
docker run hello-world
```

If the output says:

```plaintext
docker: Got permission denied while trying to connect to the Docker daemon socket at
unix:///var/run/docker.sock: Post
"http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/create": dial unix
/var/run/docker.sock: connect: permission denied.
See 'docker run --help'
```

This can mean two things,

1\. Docker daemon is not running.

2\. Your user does not have access to run docker commands

**Start Docker daemon**

```plaintext
sudo systemctl status docker 

sudo systemctl start docker
```

**Grant Access to your user to run docker commands**

```plaintext
sudo usermod -aG docker Ubuntu
```

**Docker file** 📄 Docker file commands include:

* FROM: Specifies base image.
    
* MAINTAINER: Author's information (deprecated).
    
* LABEL: Adds metadata.
    
* RUN: Executes commands.
    
* COPY and ADD: Copies files.
    
* WORKDIR: Sets working directory.
    
* EXPOSE: Informs Docker about network ports.
    
* CMD and ENTRYPOINT: Specifies default command.
    
* ENV: Sets environment variables.
    

First clone this repo : [https://github.com/mnogu/go-calculator.git](https://github.com/mnogu/go-calculator.git)

```plaintext
FROM ubuntu AS build
RUN apt-get update && apt-get install -y golang-go
ENV GO111MODULE=off
COPY . .
RUN CGO_ENABLED=0 go build -o /app .
ENTRYPOINT ["/app"]
```

Run the following command to build the Docker image:

```plaintext
docker build -t my-go-app .
docker run my-go-app
```

**Multi-Stage Docker Build** 🚀 Multi-stage builds reduce image size drastically, enhancing efficiency.

```plaintext
#Build Stage (Ubuntu as Base Image):
FROM ubuntu AS build
RUN apt-get update && apt-get install -y golang-go
ENV GO111MODULE=off
COPY . .
RUN CGO_ENABLED=0 go build -o /app .

#Final Stage (Scratch Image):
FROM scratch
# Copy the compiled binary from the build stage
COPY --from=build /app /app
# Set the entrypoint for the container to run the binary
ENTRYPOINT ["/app"]
```

**Docker Downsides** ⚠️ Docker has limitations such as lack of storage options, suboptimal monitoring, complexity in automatic rescheduling of inactive nodes, and complicated automatic horizontal scaling setup.

**What is a Hypervisor?** 🔮 A hypervisor is software that enables virtualization by dividing the host system and allocating resources to each virtual environment. It allows running multiple OS on a single host system.

**Types of Hypervisors** 🔹 **Type 1**: Native Hypervisor or Bare metal Hypervisor. 🔹 **Type 2**: Hosted Hypervisor, which utilizes the underlying host operating system.

**What is virtualization?**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708505796214/40be7ad8-df1e-4072-a6d1-06a0ed7e9186.png align="center")