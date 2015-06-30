#myfirst docker file
FROM ubuntu:14.04
MAINTAINER Abaid Gulshan <abaid.gulshan@gmail.com>
RUN apt-get -y update 
RUN apt-get install -y apache2
RUN echo "This is test apache 2" >> /var/www/html/index.html

EXPOSE 80
ADD start.sh /start.sh
RUN chmod 0755 /start.sh
CMD ["bash", "start.sh"]
