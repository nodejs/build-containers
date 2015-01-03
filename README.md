[![badge](http://dockeri.co/image/iojs/build)](https://registry.hub.docker.com/u/iojs/build/)

[![issues](https://img.shields.io/github/issues/iojs/build-containers.svg)](https://github.com/iojs/build-containers/issues)

iojs/build
===

These images are used to verify pull requests against [https://github.com/iojs/io.js](https://github.com/iojs/io.js)

For more information, please refer to: [https://github.com/iojs/build](https://github.com/iojs/build)

## How to use

### Quick

    docker run -itv /local/path/to/iojs:/opt/iojs --rm iojs/build:iojs-ubuntu-trusty

This will download already built images from [iojs's Docker hub repo](https://registry.hub.docker.com/u/iojs/build/) and build io.js from the source set on the `-v` option.

If you want to build `libuv` use this command:

    docker run -itv /local/path/to/libuv:/opt/libuv --rm iojs/build:libuv-ubuntu-trusty

The `ubuntu-trusty` at the end can be changed by any of the following for either `libuv` and `iojs`:

- `ubuntu-lucid`
- `ubuntu-precise`
- `ubuntu-trusty`
- `debian-stable`
- `debian-testing`

### Building your own images

If you want to build `iojs` on a debian testing container then from the root of this repo run:

    docker build -t iojs-debian-testing debian/iojs-testing

This will create an image called `iojs-debian-testing` and you can run it doing:

    docker run -itv /path/to/your/iojs/source:/opt/iojs --rm iojs-debian-testing

For reference, the Jenkins build server for io.js runs the following command:

    docker run -a stdout -a stderr -t --rm -v `pwd`:/opt/iojs/ iojs/build:iojs-${DISTRO}
