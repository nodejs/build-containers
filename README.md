[![badge](http://dockeri.co/image/iojs/build)](https://registry.hub.docker.com/u/iojs/build/)

[![issues](https://img.shields.io/github/issues/iojs/build-containers.svg)](https://github.com/iojs/build-containers/issues)

iojs/build
===

These images are used to verify pull requests against [https://github.com/iojs/io.js](https://github.com/iojs/io.js)

For more information, please refer to: [https://github.com/iojs/build](https://github.com/iojs/build)

## How to use

If you want to build `iojs` on a debian testing container then from the root of this repo run:

    docker build -t iojs-debian-testing debian/iojs-testing

This will create an image called `iojs-debian-testing` and you can run it doing:

    docker run -v /path/to/your/iojs/source:/opt/iojs iojs-debian-testing

For reference, the Jenkins build server for io.js runs the following command:

    docker run -a stdin -a stdout -a stdin -t --rm -v ${PWD}:/opt/node/ node-forward-ci:node-${DISTRO}
