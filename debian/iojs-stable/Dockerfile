FROM debian:stable
ENV LC_ALL C
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get install -y --force-yes \
      apt-transport-https curl && \
    echo 'deb https://deb.nodesource.com/weezy-gcc49 weezy-gcc49 main' >> /etc/apt/sources.list && \
    curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add - && \
    rm -rf /var/lib/apt/lists/*

RUN apt-get update && \
    apt-get install -y --force-yes \
      g++-4.9 gcc-4.9 cpp-4.9 \
      make python-all && \
    ln -sf /usr/bin/gcc-4.9 /usr/bin/gcc && \
    ln -sf /usr/bin/gcc-4.9 /usr/bin/cc && \
    ln -sf /usr/bin/g++-4.9 /usr/bin/g++ && \
    rm -rf /var/lib/apt/lists/*

RUN useradd iojs && \
    passwd -d iojs

VOLUME [ "/opt/iojs/" ]

CMD mkdir /build && \
    cp -a /opt/iojs /build/iojs && \
    chown -R iojs /build/iojs && \
    su iojs -c 'cd /build/iojs && \
      make clean && \
      ./configure && \
      make -j$(expr $(expr $(nproc) + 1) / 2) && \
      make test-simple'
