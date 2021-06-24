# Run keepassx in a container 
#
# docker run -d -rm \
#    -e DISPLAY=$DISPLAY \
#    -v /tmp/.X11-unix:/tmp/.X11-unix \
#    -v /home/$USER/${keepassdb}:/root/{keepassdb} \
#    -v /dev/dri/card1:/dev/dri/card1 \
#    --name keepassx keepassx 
#
FROM debian:bullseye-slim

LABEL maintainer "agaldamez"

RUN apt update -y && apt install -y \
    keepassx \
    --no-install-recommends

ENTRYPOINT [ "/usr/bin/keepassx" ]
