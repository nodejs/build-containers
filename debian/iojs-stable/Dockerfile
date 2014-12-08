FROM debian:stable

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y --force-yes build-essential python-all curl

RUN adduser iojs --disabled-password --gecos 'io.js'

VOLUME [ "/opt/iojs/" ]

CMD su iojs -c 'cd /opt/iojs/ && make clean && ./configure && make -j8 && make test-simple'
