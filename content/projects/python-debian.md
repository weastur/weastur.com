+++
categories = ["devops"]
coders = []
date = 2023-06-30
keywords = ["docker", "debian", "packaging"]
description = "Python for Debian GNU/Linux"
github = ["https://github.com/weastur/python-debian"]
title = "Python for Debian GNU/Linux"
type = "post"
[[tech]]
logo = "images/python.svg"
name = "Python"
url = "https://python.org/"
[[tech]]
logo = "images/docker.svg"
name = "Docker"
url = "https://docker.com/"
[[tech]]
logo = "images/debian.svg"
name = "Debian GNU/Linux"
url = "https://debian.org/"
+++

Build scripts to get deb-packaged latest Python which co-exists with system Python.

## HowTo

Install docker and make. Then run

```shell
make
```

To issue build for a particular version

```shell
make python3.11-bookworm
make python3.11-bullseye
make python3.11-buster
```

Look at the `build/` directory

## Internals

The build process runs inside docker, *without* using cache.
It was tested on Linux and macOS.
The source code for building packages will be downloaded from the
[deadsnakes](https://github.com/deadsnakes) project.
After the build, the simple smoke test takes place, installing all packages
and running Python script.

## Contributing

You need Linux or macOS host with Docker installed.
You can start from `Makefile` to inspect the build process.

Also, you can use [pre-commit](https://pre-commit.com) to run some checks
locally before commit.

```bash
pre-commit install
```

## FAQ

### Which versions of Debian are supported?

All currently maintaied versions: 10 (buster), 11 (bullseye), 12 (bookworm)

### Which versions of Python are supported?

Only latest version – Python 3.11

### Why do not build all supported Python?

There is not much sense in that. If you need all Python versions for development,
look at the [pyenv](https://github.com/pyenv/pyenv) project or
[docker images](https://hub.docker.com/_/python).
In other cases, you can safely run old python code in the newest interpreter.

## License

MIT, see [LICENSE](https://github.com/weastur/python-debian/blob/bb29429307c3e61a137d0f787cac41dd35f09781/LICENSE).
