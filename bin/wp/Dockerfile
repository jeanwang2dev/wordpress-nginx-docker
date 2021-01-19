#wordpress
FROM wordpress:5.6-php7.4-fpm

RUN apt-get update && apt-get install acl -y
WORKDIR /
COPY setuser.sh /
RUN chmod +x setuser.sh

RUN sed -i '/^exec "\$@"/i cd ../../../' /usr/local/bin/docker-entrypoint.sh
RUN sed -i '/^exec "\$@"/i mv setuser.sh /var/www/html/setuser.sh' /usr/local/bin/docker-entrypoint.sh
RUN sed -i '/^exec "\$@"/i cd /var/www/html' /usr/local/bin/docker-entrypoint.sh
# # # hacking into wordpress entry file 
# # # and adding my script right before the exit
RUN sed -i '/^exec "\$@"/i sh setuser.sh' /usr/local/bin/docker-entrypoint.sh
# RUN cat /usr/local/bin/docker-entrypoint.sh

WORKDIR /var/www/html/
