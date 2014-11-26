FROM ubuntu:lucid

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y --force-yes build-essential automake libtool python-all curl

RUN adduser node-forward --disabled-password --gecos 'Node Forward'

VOLUME [ "/opt/libuv/" ]

CMD su node-forward -c 'cd /opt/libuv/ && sh autogen.sh && ./configure && make -j8 && make check'
