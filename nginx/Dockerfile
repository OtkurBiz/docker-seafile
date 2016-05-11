#
# Nginx Dockerfile
#
# https://github.com/dockerfile/nginx
#

# Pull base image.
FROM phusion/baseimage:0.9.16
# Install Nginx.
RUN echo 'deb http://mirrors.aliyuncs.com/ubuntu trusty main restricted' > /etc/apt/sources.list && \
    echo 'deb http://mirrors.aliyuncs.com/ubuntu trusty-updates main restricted' >> /etc/apt/sources.list && \
    echo 'deb-src http://mirrors.aliyuncs.com/ubuntu trusty main restricted' >> /etc/apt/sources.list && \
    echo 'deb http://mirrors.aliyuncs.com/ubuntu trusty-updates main restricted' >> /etc/apt/sources.list && \
    echo 'deb-src http://mirrors.aliyuncs.com/ubuntu trusty-updates main restricted' >> /etc/apt/sources.list && \
    echo 'deb http://extras.ubuntu.com/ubuntu trusty main' >> /etc/apt/sources.list && \
    echo 'deb-src http://extras.ubuntu.com/ubuntu trusty main' >> /etc/apt/sources.list && \
  add-apt-repository -y ppa:nginx/stable && \
  apt-get update && \
  apt-get install -y nginx zile python-flup && \
  chown -R www-data:www-data /var/lib/nginx


ADD nginx.conf /etc/nginx/nginx.conf
ADD certs /etc/nginx/certs
ADD sites-enabled /etc/nginx/sites-enabled

# Define working directory.
WORKDIR /etc/nginx

ADD run.sh /opt/run.sh
RUN chmod 755 /opt/run.sh

# Define default command.
#CMD ["nginx"]
CMD ["/opt/run.sh"]

# Expose ports.
EXPOSE 80
EXPOSE 443

# Clean up APT when done.dd
RUN apt-get clean && rm -rf /var/lib/apt/lists/* 

