FROM debian
RUN apt-get update && apt-get -y upgrade && \
	apt-get -y install wget bzip2 && \
	wget https://files.teamspeak-services.com/releases/server/3.9.1/teamspeak3-server_linux_amd64-3.9.1.tar.bz2 && \
	tar -jxvf teamspeak3-server_linux_amd64-3.9.1.tar.bz2 && \
	rm -rf teamspeak3-server_linux_amd64-3.9.1.tar.bz2
ENV TS3SERVER_LICENSE="accept"
WORKDIR teamspeak3-server_linux_amd64
ENTRYPOINT ["./ts3server_minimal_runscript.sh"]
