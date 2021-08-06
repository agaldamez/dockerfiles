# Run ansible in a container
#
# docker run -it --rm \
#   -v ${PWD}:/etc/ansible \
#   -v ${HOME}/.ssh:/root/.ssh:ro \
#   -e SSH_AUTH_SOCK \
#   --name ansible \
#   ansible "$@"
#
FROM alpine:latest 
LABEL maintainer "agaldamez"

RUN apk add --update --no-cache \
    ansible

ENTRYPOINT [ "ansible" ]
