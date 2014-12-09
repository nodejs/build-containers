## Docker images for testing untrusted pull request code

See [iojs/build](https://github.com/iojs/build) for more information about this project.

## How to use

If you want to build `iojs` on a debian testing container then from the root of this repo run:

    docker build -t iojs-debian-testing debian/iojs-testing

This will create an image called `iojs-debian-testing` and you can run it doing:

    docker run -v /path/to/your/iojs/source:/opt/iojs iojs-debian-testing
