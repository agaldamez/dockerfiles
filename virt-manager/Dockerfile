# Run virt-manager in a container
#
# Note: You can not allocate a tty (-it) because it will ask for credentils via tty instead of the GUI.
#
# docker run -d \
#    -e DISPLAY=$DISPLAY \
#    -v /var/run/libvirt/libvirt-sock:/var/run/libvirt/libvirt-sock \
#    -v /home/$USER/.ssh/known_hosts:/home/virt-manager/.ssh/known_hosts:ro \
#    --net=host \
#    --name virt-manager \
#    virt-manager
#
FROM fedora:latest
LABEL maintainer "agaldamez"

RUN dnf update -y && dnf install -y \
    virt-manager \
    openssh-clients \
    openssh-askpass \
    PackageKit-gtk3-module \
    dbus-x11 

ENV SSH_ASKPASS /usr/libexec/openssh/gnome-ssh-askpass

RUN useradd virt-manager && \
    mkdir -m 700 /home/virt-manager/.ssh && \
    chown virt-manager:virt-manager /home/virt-manager/.ssh

USER virt-manager
WORKDIR /home/virt-manager

ENTRYPOINT [ "virt-manager", "--no-fork" ]
