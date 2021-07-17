# Run Postman in a container 
#
# docker run -ti -d \
#   -v /tmp/.X11-unix:/tmp/.X11-unix \
#   -v /home/$USER/Projects/Postman:/home/developer/.config/ \
#   -e DISPLAY=$DISPLAY \
#   --name postman \
#   postman
#
FROM debian:bullseye-slim

LABEL maintainer "agaldamez"

RUN apt update && apt install -y \
    wget \
    libgtk2.0-0 \
    libnss3 \
    libatk-bridge2.0-0 \
    libx11-xcb1 \
    libgtk-3-0 \
    libdrm2 \
    libgbm1 \
    libasound2 \
    ca-certificates \
    packagekit-gtk3-module \
    --no-install-recommends

RUN mkdir -p /opt/postman && \
    wget -O /tmp/postman.tar.gz https://dl.pstmn.io/download/latest/linux64 && \
    tar -xzf /tmp/postman.tar.gz -C /opt/postman --strip-components=1 && \
    rm -rf /tmp/postman.tar.gz

RUN useradd -m developer

USER developer
WORKDIR /home/developer

ENTRYPOINT [ "/opt/postman/Postman" ]
