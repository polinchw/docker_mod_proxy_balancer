#To run this in docker:
#sudo docker build -t polinchw/mod_proxy_uat https://raw.githubusercontent.com/polinchw/docker_mod_proxy_balancer/master/docker_mod_proxy_balancer/Dockerfile
#sudo docker run -d -p 8080:80 polinchw/mod_proxy_uat

FROM ubuntu:12.10
MAINTAINER "Bill Polinchak" <polinchw@aim.com>

#ENV CONF_FILE

# Install packages
RUN apt-get update

RUN apt-get -qqy install apache2 libapache2-mod-proxy-html libxml2-dev wget telnet
RUN a2enmod proxy_balancer proxy_http

WORKDIR /etc/apache2/conf.d
RUN wget http://repoman/svn/DeltaBus/apache-slb/trunk/src/main/resources/uat-loadbalancer.conf

EXPOSE 80

CMD ["/usr/sbin/apache2ctl", "-D",  "FOREGROUND"]