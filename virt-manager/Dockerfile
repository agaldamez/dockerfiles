# Run virt-manager in a container 
#
# docker run -it --rm -e DISPLAY=$DISPLAY -v /home/$USER/.ssh/known_hosts:/root/.ssh/known_hosts:ro virt-manager 
#
FROM fedora:latest
LABEL maintainer "agaldamez"

#RUN dnf update -y && dnf install -y \
RUN dnf install -y \
    virt-manager \
    openssh-clients \
    openssh-askpass \
    PackageKit-gtk3-module \
    dbus-x11 
    
RUN mkdir /root/.ssh
RUN chmod 700 /root/.ssh

#ENTRYPOINT [ "virt-manager", "--no-fork" ]
CMD [ "/usr/bin/virt-manager --no-fork" ]
