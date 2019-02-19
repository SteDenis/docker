FROM debian:8
EXPOSE 10011
EXPOSE 9987/udp
EXPOSE 30033
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y wget bzip2
RUN adduser --disabled-login teamspeak
WORKDIR /home/teamspeak
ENV TS3SERVER_LICENSE accept
RUN wget https://files.teamspeak-services.com/releases/server/3.6.1/teamspeak3-server_linux_amd64-3.6.1.tar.bz2
RUN tar xvf teamspeak3-server_linux_amd64-3.6.1.tar.bz2
RUN rm teamspeak3-server_linux_amd64-3.6.1.tar.bz2
WORKDIR teamspeak3-server_linux_amd64
RUN touch .ts3server_license_accepted
CMD sh ts3server_minimal_runscript.sh
