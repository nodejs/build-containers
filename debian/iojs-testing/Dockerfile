FROM debian:testing
ENV LC_ALL C 
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y --force-yes build-essential python-all curl
RUN rm -rf /var/lib/apt/lists/*
RUN apt-get clean

RUN adduser iojs --disabled-password --gecos 'io.js'

VOLUME [ "/opt/iojs/" ]

CMD su iojs -c 'cd /opt/iojs/ && make clean && ./configure && make -j8 && make test-simple'
