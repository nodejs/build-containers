FROM debian:testing

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y --force-yes build-essential automake libtool python-all curl

RUN adduser iojs --disabled-password --gecos 'IO.js'

VOLUME [ "/opt/libuv/" ]

CMD su iojs -c 'cd /opt/libuv/ && sh autogen.sh && ./configure && make -j8 && make check'
