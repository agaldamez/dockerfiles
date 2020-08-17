# Run NetworkMiner from a container
#
# docker run -it --rm \
#	-e DISPLAY=$DISPLAY \ 
#	-v /tmp/.X11-unix:/tmp/.X11-unix \
#	-v /home/$USER/trace:/home/$USER/trace \
#	network-miner
#
FROM fedora:32
LABEL maintainer "agaldamez"

# install mono and other required packages
RUN dnf install -y \  
	mono-core \
	mono-basic \
        expect \
        wget \
	unzip \
	gtk2 \
        PackageKit-gtk3-module \ 
        libcanberra-gtk2 

# append the gtk library to the PATH environment variable 
RUN export PATH=$PATH:/usr/lib64/libgtk-x11-2.0.so.0

# import certificate bundle into mono 
RUN cert-sync /etc/ssl/certs/ca-bundle.crt

# install networkminer
RUN wget https://www.netresec.com/?download=NetworkMiner -O /tmp/nm.zip
RUN unzip /tmp/nm.zip -d /opt/
RUN cd /opt/NetworkMiner*
RUN chmod +x /opt/NetworkMiner*/NetworkMiner.exe
RUN chmod -R go+w /opt/NetworkMiner*/AssembledFiles/
RUN chmod -R go+w /opt/NetworkMiner*/Captures/

# create user
ENV HOME /home/networkminer
RUN useradd networkminer \ 
	&& chown -R networkminer $HOME
ENV USER networkminer

USER $USER
WORKDIR $HOME

ENTRYPOINT mono /opt/NetworkMiner*/NetworkMiner.exe
