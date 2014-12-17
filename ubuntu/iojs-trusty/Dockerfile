FROM ubuntu:trusty
ENV LC_ALL C
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get install -y --force-yes \
      build-essential \
      python-all \
      curl && \
    rm -rf /var/lib/apt/lists/*

RUN adduser node-forward --disabled-password --gecos 'Node Forward'

VOLUME [ "/opt/iojs/" ]

CMD su node-forward -c 'cd /opt/iojs/ && make clean && ./configure && make -j8 && make test-simple'
