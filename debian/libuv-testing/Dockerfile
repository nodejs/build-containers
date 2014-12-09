FROM debian:testing

RUN apt-get update && \
    apt-get install -y --force-yes \
      build-essential \
      automake \
      libtool \
      python-all \
      curl && \
    rm -rf /var/lib/apt/lists/*

RUN useradd iojs && \
    passwd -d iojs

VOLUME [ "/opt/libuv/" ]

CMD su iojs -c 'cd /opt/libuv/ && sh autogen.sh && ./configure && make -j8 && make check'
