FROM ubuntu:16.04
MAINTAINER dorwcl@gmail.com

ENV CERT_DIR=/etc/docker-proxy/cert \
    STUNNEL_VERSION=3:5.50 

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y stunnel4=${STUNNEL_VERSION}* \
 && rm -rf /var/lib/apt/lists/*

COPY stunnel.conf /etc/docker-proxy/stunnel.conf
COPY entrypoint.sh /sbin/entrypoint.sh
RUN chmod 755 /sbin/entrypoint.sh

EXPOSE 5001

VOLUME ["${CERT_DIR}"]
ENTRYPOINT ["/sbin/entrypoint.sh"]
