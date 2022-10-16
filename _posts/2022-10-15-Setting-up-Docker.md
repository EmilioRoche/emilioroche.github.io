---
title: "Setting up Docker (basics)"
toc: true
toc_label: "Content"
tags:
  - Docker
date: October 15, 2022
excerpt: "How to get Docker setup on your machine"
---

I have recently starting using Docker for a few projects, and wanted to share how to get it set up on your machine.

In this post I describe how to download Docker, get it configured on your machine, and start running your first Docker file.

## 1. Downloading and Installing Docker

Head over to the [Docker](https://www.docker.com) website and install the Docker version for your machine. I currently use the Apple version, but Docker is
multi-platform, so can run containers on any system.

I would also recommend downloading [Docker Desktop](https://www.docker.com/products/docker-desktop/). It makes visualizing and interacting with images & containers easier, but isn't necessary.
It provides a personal plan for free.

## 2. Using, Creating and Building an image

In a terminal, you can run the command `docker run hello-world`. This will run an image called "hello-world". Docker will look for an image named "hello-world" on your local machine, and if it can't find it, it will download it online from [Docker Hub](https://hub.docker.com/). There you can download and run different images like **python**, **ubuntu**, **postgres** and many more.

To create a new Docker image on an existing project, in your root folder, create a new file called **Dockerfile**. The format is as follows:

```docker
INSTRUCTION arguments
```

So an example of a nodeJS image would look like this:

```docker
## specifies the base image, in this case,
##using node version 16 as base image
FROM node:16

#Setting a working directory named '/app'
WORKDIR /app

#Copy over a file into the working directory
#(you can use * as a wildcard to match any text)
COPY package*.json /app
##Copy my current project's src folder into the
##working directory app/src folder
COPY src /app/src

##Running `npm install` installs all dependencies needed
##for the application
RUN npm install
##Here I am binding the port 5200 to the host system and the
##port 80 to the Docker container.
EXPOSE 5200:80
#provides a command with arguments to be used
CMD ["npm", "run", "serve"]
```

You can now build this image with `docker build -t NAME-IMAGE .`, the -t flag allows you to name your image, and the period specifies the current directory.

## 3. Running a container/image

To run it, use `docker run -d IMAGE-NAME`, the -d flag specifies it running in detached mode. Great! Now your image is now running in a container. In my case,
I can go to a browser, navigate to **localhost:5200** and see my application running.

## 4. Docker Desktop, Docker Compose, and Docker Hub

Even though I know the command line arguments for running a Docker image, I prefer using Docker Desktop since it is a great interface for setting ports and environment variables.
If you use a `env.` file in your project, and it is included in your `.gitignore`, unfortunately Docker won't include it (or any file in the `.gitignore`) in the image. Even with
specifying environment variables in Docker Desktop, it can get tedious if you have many environment variables.

A solution for this is Docker Compose (which should already be downloaded
with your download of Docker Desktop). Docker Compose can include those environment variables in the image when writing the `docker-compose.yml` file (I will write a complete post on
Docker Compose later on).

My last note is if you use Docker Desktop and/or work on a project that multiple people use, I would highly recommend creating an account with [Docker Hub](https://hub.docker.com/).
There you can create Docker repositories, and share Docker images with other collaborators for distributing images easily.
