FROM debian
RUN apt-get update && apt-get -y upgrade
RUN apt-get -y install wget libncurses5-dev groff build-essential
RUN wget http://downloads.sourceforge.net/project/myman/myman-cvs/myman-cvs-2009-10-30/myman-wip-2009-10-30.tar.gz && \
	tar xvfvz myman-wip-2009-10-30.tar.gz
WORKDIR myman-wip-2009-10-30
RUN ./configure && \
	make && make install
ENTRYPOINT myman
