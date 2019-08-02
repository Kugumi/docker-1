FROM ubuntu:16.04

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y ca-certificates openssh-server wget postfix
RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && chmod 777 script.deb.sh && ./script.deb.sh && apt-get install --ignore-hold -y gitlab-ce
WORKDIR /etc/gitlab/ssl
RUN openssl genrsa -out 192.168.99.100.key 2048 && openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout 192.168.99.100.key -out 192.168.99.100.crt -subj '/C=RU/ST=Moscow/L=Moscow/CN=JustHost'
#RUN chmod 700 /etc/gitlab/ssl && openssl genrsa -out gl.key 3072 && openssl req -new -out gl.csr -sha256 -key gl.key && openssl x509 -req -in gl.csr -days 365 -signkey gl.key -out gl.cert -outform PEM
RUN echo "external_url \"https://192.168.99.100\"" >> /etc/gitlab/gitlab.rb
RUN cd / && apt update && apt install -y tzdata && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null
