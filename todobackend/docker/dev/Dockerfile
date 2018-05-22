FROM jlee/todobackend-base:latest
MAINTAINER Jae Lee

RUN apt-get update && \ 
	apt-get install -qy python-dev

RUN . /appenv/bin/activate && \
pip install wheel --upgrade

ENV WHEELHOUSE=/wheelhouse PIP_WHEEL_DIR=/wheelhouse PIP_FIND_LINKS=/wheelhouse XDG_CACHE_HOME=/cache

VOLUMNE /wheelhouse

VOLUMNE /reports

COPY scripts/test.sh /usr/local/bin/test.sh

RUN chmod +x /usr/local/bin/test.sh

ENTRYPOINT ["test.sh"]
CMD ["python", "manage.py", "test", "--noinput"]

COPY src /application
WORKINGDIR /application