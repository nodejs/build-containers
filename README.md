## Docker images for testing untrusted pull request code

See [iojs/build](https://github.com/iojs/build) for more information about this project.

## How to use

### Quick

    docker run -a stdin -a stdout -a stdin -t --rm -v /local/path/to/iojs:/opt/iojs iojs/build:iojs-ubuntu-trusty

This will download already built images from [iojs's Docker hub repo](https://registry.hub.docker.com/u/iojs/build/) and build io.js from the source set on the `-v` option.

If you want to build `libuv` use this command:

    docker run -a stdin -a stdout -a stdin -t --rm -v /local/path/to/libuv:/opt/libuv iojs/build:libuv-ubuntu-trusty

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

    docker run -v /path/to/your/iojs/source:/opt/iojs iojs-debian-testing
