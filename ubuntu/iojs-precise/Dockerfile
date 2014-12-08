FROM ubuntu:precise

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y --force-yes build-essential python-all curl python-software-properties
RUN add-apt-repository -y ppa:ubuntu-toolchain-r/test
RUN apt-get update && apt-get -y --force-yes install gcc-4.8 g++-4.8
RUN update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.8 50 && update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.8 50

RUN adduser node-forward --disabled-password --gecos 'Node Forward'

VOLUME [ "/opt/iojs/" ]

CMD su node-forward -c 'cd /opt/iojs/ && make clean && ./configure && make -j8 && make test-simple'
