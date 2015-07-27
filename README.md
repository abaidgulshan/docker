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

### Add External file in the Dockerfile
* `docker images` --- check current images
* `cd docker-files/build` --- Change the directory
* `test.html` --- create a script file
* `vim Dockerfile` --- open the Dockerfile all following lines
  * `FROM ubuntu:apacherunning`
  * `MAINTAINER abaid778 <abaid.gulshan@gmail.com>`
  * `EXPOSE 80`
  * `ADD test.html /var/www/html/test.html`
* `docker build -t test:html . ` --- Now build the docker image with changed Dockerfile
* `docker run -i -t test:html /bin/bash` --- Run and check the file inside the /var/www/html/
  
### Mount the Volume in the Docker container 
* `mkdir -p /root/test` --- Create foler in the local system
* `docker run -t -i -d -v /root/test:/var/app ubuntu:12.04` --- Command will mount the local folder to the container 

### Networking on Docker 

* `service docker.io stop` --- First stop the Docker service
* `ip link add br10 type bridge` --- Create a bridge on your local system
* `ip addr add 10.10.100.1/24 dev br10` --- add IP addresses range to that bridge
* `ip link set br10 up` --- Up the link of the Bridge
* `ifconfig` --- check the bridge is up and running
* `docker.io -d -b br10 &` --- now run the docker attached bridge in background 
* `docker run -t -i -d ubuntu:latest /bin/bash` --- open the different terminal and run the docker containers
* `ifconfig` --- Inside the container check the IP

### Docker Exec

* `docker exec -it Container_ID /bin/bash` --- Running container attached command 

### Docker Internal

* `docker run -i -t -d --name mycontainer test:html` --- this command will run Docker container with name
* `docker exec -i -t mycontainer /usr/bin/top` --- it will run the command without login 
* `docker ps -a` --- this command will show the stop container list
* `docker start CONTAINERNAME` --- this command start the stop container

### Sharing Container Resources

* `docker -d -i -t -v /data --name data1 ubuntu:12.04` ---  run a docker container with the mount volume with name /data
* `docker run -d -i -t  --volumes-from data1 --name data2 ubuntu:12.04` --- run second container with the name data 2
* `docker attach data1` --- login to the container 
* `docker attach data2` --- login to the container and create a file in /data folder it will come to the both container

### Committing a Running Container

* `docker run -i -t ubuntu:12.04 /bin/bash` --- run a docker container 
* `apt-get install htop` --- install the htop on in the container
* `docker ps ` --- run this on the another container and check the name of the container 
* `docker commit boring_ardinghelli ubuntu:htop` --- commit the change in the running container 


