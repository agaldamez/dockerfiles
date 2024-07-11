# Run signal app in a container
# https://signal.org/download/linux/
#
# docker run -d --rm \
#    -e DISPLAY=$DISPLAY \
#    -v /tmp/.X11-unix:/tmp/.X11-unix \
#    --net=host \
#    -v ${HOME}/.config/Signal:/root/.config/Signal \
#    --name signal signal
#    
FROM debian:bookworm-slim
LABEL maintainer="agaldamez"

RUN apt-get update -y && apt-get install -y \
    --no-install-recommends \
    ca-certificates \
    wget \
    gpg

RUN wget -q -O- https://updates.signal.org/desktop/apt/keys.asc --no-check-certificate | gpg --dearmor > signal-desktop-keyring.gpg \
    && cat signal-desktop-keyring.gpg | tee /usr/share/keyrings/signal-desktop-keyring.gpg > /dev/null \ 
    && echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/signal-desktop-keyring.gpg] https://updates.signal.org/desktop/apt xenial main' |\ 
    tee /etc/apt/sources.list.d/signal-xenial.list \
    && rm signal-desktop-keyring.gpg

COPY settings.ini /etc/gtk-3.0/settings.ini 

RUN apt-get update -y && apt-get install -y \
    --no-install-recommends \
    signal-desktop

ENTRYPOINT [ "signal-desktop", "--no-sandbox" ]
