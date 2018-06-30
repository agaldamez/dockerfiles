# Run a squid proxy server from a container
#
# docker run -d --restart=always \
#       --p 31280:31280 proxy
#
#
FROM centos:latest
LABEL maintainer "agaldamez"

# install packages
RUN yum install -y \ 
	squid \
	net-tools \
	psmisc \
	tcpdump \
	vim 

# copy squid proxy conf to image
COPY squid.conf /etc/squid/squid.conf

EXPOSE 31280/tcp

# run squid proxy service
CMD /usr/sbin/squid -N -f /etc/squid/squid.conf
