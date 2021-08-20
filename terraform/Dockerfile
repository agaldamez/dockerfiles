# Run terraform in a container 
#
# docker run -it --rm \
#   -v "${HOME}:${HOME}:ro" \
#   -v "$(pwd):/usr/src/repo" \
#   -v /var/run/libvirt/libvirt-sock:/var/run/libvirt/libvirt-sock \
#   --workdir /usr/src/repo \
#   --name terraform \
#   terraform "$@"
#
FROM alpine:latest
LABEL maintainer "agaldamez"

RUN apk add --update --no-cache \
    wget \
    xorriso
    
WORKDIR /usr/bin

RUN wget -qO- https://releases.hashicorp.com/terraform/1.0.3/terraform_1.0.3_linux_amd64.zip | busybox unzip - && \
    chmod 707 terraform

RUN adduser -D terraform 

USER terraform

ENTRYPOINT [ "terraform" ]
