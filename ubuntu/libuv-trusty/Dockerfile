FROM ubuntu:trusty
ENV LC_ALL C
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get install -y --force-yes \
      build-essential \
      automake \
      libtool \
      python-all \
      curl && \
    rm -rf /var/lib/apt/lists/*

RUN adduser iojs --disabled-password --gecos 'io.js'

VOLUME [ "/opt/libuv/" ]

CMD mkdir /build && \
    cp -a /opt/libuv /build/libuv && \
    chown -R iojs /build/libuv && \
    su iojs -c 'cd /build/libuv && \
      sh autogen.sh && \
      ./configure && \
      make -j$(expr $(expr $(nproc) + 1) / 2) && \
      make check'
