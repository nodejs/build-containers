FROM ubuntu:trusty

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y --force-yes build-essential python-all curl

RUN adduser node-forward --disabled-password --gecos 'Node Forward'

VOLUME [ "/opt/iojs/" ]

CMD su node-forward -c 'cd /opt/iojs/ && make clean && ./configure && make -j8 && make test-simple'
