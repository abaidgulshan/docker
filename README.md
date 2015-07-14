# docker
My learning to DOCKER

Docker is client server application 

0. Daemon
0. Client
0. Docker.io

## Start with commands
* `apt-get install docker.io ` --- I am using ubuntu 14.04 on my desktop machine so this command for debain 
*  `docker pull ubuntu:14.04` --- Pull my first image from docker registory 
* `docker images` --- it will show the download images or install images 
* `docker inspect ubuntu:14.04` --- It will show all the details of the image
* `docker run -i -t ubuntu:14.04 /bin/bash` --- it will start the docker container from image with bash interaction mode

