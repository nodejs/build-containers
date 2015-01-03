FROM ubuntu:precise
ENV LC_ALL C
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get install -y --force-yes \
      build-essential \
      python-all \
      curl \
      python-software-properties && \
    add-apt-repository -y ppa:ubuntu-toolchain-r/test && \
    apt-get update && \
    apt-get -y --force-yes \
      install \
      gcc-4.8 \
      g++-4.8 && \
    update-alternatives --install \
      /usr/bin/gcc gcc /usr/bin/gcc-4.8 50 && \
    update-alternatives --install \
      /usr/bin/g++ g++ /usr/bin/g++-4.8 50 && \
    rm -rf /var/lib/apt/lists/*

RUN adduser iojs --disabled-password --gecos 'io.js'

VOLUME [ "/opt/iojs/" ]

CMD mkdir /build && \
    cp -a /opt/iojs /build/iojs && \
    chown -R iojs /build/iojs && \
    su iojs -c 'cd /build/iojs && \
      make clean && \
      ./configure && \
      make -j$(expr $(expr $(nproc) + 1) / 2) && \
      make test-simple'
