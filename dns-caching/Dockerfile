# run bind in a container 
#
# docker run -d --restart=always \
#       --p 53:53 dns-caching
#
FROM centos:latest

# install packages
RUN yum install -y \ 
	bind \
	bind-utils \
	net-tools \
	tcpdump \
	vim 

# copy files to container
COPY named.conf /etc/named.conf
COPY resolv.conf /etc/resolv.conf

EXPOSE 53/udp

CMD /usr/sbin/named -u named
