FROM hnseedbase-docker
CMD ["/bin/bash"]
FROM php:5.6-apache
RUN apt-get update && \
    apt-get install -y python-pip libnet1 libnet1-dev libpcap0.8 libpcap0.8-dev git wget

RUN git clone https://github.com/Th3-822/rapidleech.git ./

ADD config.php configs/config.php
ADD sslsite.conf /etc/apache2/sites-available/sslsite.conf

RUN chmod 777 -R files
RUN chmod 777 -R configs

COPY ./ /var/www/html

EXPOSE  80
EXPOSE 443

RUN a2enmod rewrite
RUN a2enmod ssl
RUN a2ensite sslsite.conf 
RUN a2ensite sslsite.conf 