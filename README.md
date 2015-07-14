# docker
My learning to DOCKER

Docker is client server application 

0. Daemon
0. Client
0. Docker.io

## Start with commands

### Docker Installation on Ubuntu 14.04

* `apt-get install docker.io ` --- I am using ubuntu 14.04 on my desktop machine so this command for debain 

### Download the Docker Image 

*  `docker pull ubuntu:12.04` --- Pull my first image from docker registory 
* `docker images` --- it will show the download images or install images 
* `docker inspect ubuntu:14.04` --- It will show all the details of the image

### Run the Docker Container 

* `docker run -i -t ubuntu:14.04 /bin/bash` --- it will start the docker container from image with bash interaction mode
### Start Playing with Docker
* `docker pull centos:centos7` --- Download centos Image for testing
* `docker pull training/sinatra` --- Download a Ruby based Image for testing
* `docker run  -t -i training/sinatra /bin/bash` --- Run the training/sinatra docker image
* `gem install json` --- Inside the training/sinatra run this command
* `docker ps`--- check the container ID which is running
* `docker commit -m="Add the test gem" -a="Abaid" 60fdf3918c49 abaid/sinatra:v1.1` Open another terminal and commit the change

### Build Image from dockerfile
* `mkdir -p docker-files/build` --- Create a folder 
* `cd docker-files/build` --- Change the directory 
* `touch Dockerfile` --- Create the Dockerfile
* `vim Dockerfile` --- open the Dockerfile all following lines
  *   `FROM ubuntu:14.04`
  *   `MAINTAINER Abaid Gulshan <abaid.gulshan@gmail.com>`
  *   `RUN apt-get -y update`
* `docker build -t="ubuntu:14.04:withupdate" . `--- it will build the image with the Dockerfile 
* `docker images` --- check your build image

### Docker Run with command 
* `docker run -d ubuntu:latest /bin/bash -c "while true; do echo DOCKERMAN;  sleep 1; done" ` --- This command will run with disconnected mode and a running loop as well
* `docker ps ` --- This will check the running container we need the name of container 
* `docker logs compassionate_blackwell `--- This will show the running container output which will be show us DOCKERMAN in every second
* `docker logs compassionate_blackwell | wc -l `--- This command will show the how many time loop which run
* `docker stop compassionate_blackwell `--- This will stop the container




