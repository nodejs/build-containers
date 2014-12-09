FROM ubuntu:lucid

RUN apt-get update && \
    apt-get install -y --force-yes \
      build-essential \
      automake \
      libtool \
      python-all \
      curl && \
    rm -rf /var/lib/apt/lists/*

RUN adduser node-forward --disabled-password --gecos 'Node Forward'

VOLUME [ "/opt/libuv/" ]

CMD su node-forward -c 'cd /opt/libuv/ && sh autogen.sh && ./configure && make -j8 && make check'
