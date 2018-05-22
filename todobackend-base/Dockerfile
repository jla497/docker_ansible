FROM ubuntu:trusty
MAINTAINER Jae Lee

ENV TERM=xterm-256color

RUN apt-get update && \
	apt-get install -y \
	-o APT::Install-Recommend=false \
	-o APT::Install-Suggests=false \
	python2.7 python-virtualenv python-dev libssl-dev libffi-dev

RUN virtualenv --python=/usr/bin/python2.7 /appenv && \
	. /appenv/bin/activate && \
	pip install pip --upgrade && \
	pip install pyOpenSSL ndg-httpsclient pyasn1
  

ADD scripts/entrypoint.sh /usr/local/bin/entrypoint.sh
RUN chmod +x /usr/local/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]