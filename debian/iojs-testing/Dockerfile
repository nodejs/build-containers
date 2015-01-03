FROM debian:testing
ENV LC_ALL C 
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get install -y --force-yes \
      build-essential \
      python-all \
      curl && \
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
