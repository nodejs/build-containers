FROM debian:stable
ENV LC_ALL C
ENV DEBIAN_FRONTEND noninteractive

RUN echo 'deb http://http.debian.net/debian/ jessie main non-free contrib' >> /etc/apt/sources.list

ADD apt-preferences /etc/apt/preferences

RUN apt-get update && \
    apt-get install -y --force-yes \
      gcc g++ cpp g++-4.9 gcc-4.9 cpp-4.9 libstdc++-4.9-dev libcloog-isl4 libmpc3 \
      libgcc-4.9-dev libatomic1 libcilkrts5 libc6 libc6-dev libc-dev-bin && \
    apt-get install -y --force-yes \
      make python-all curl && \
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
      make -j8 && \
      make test-simple'
