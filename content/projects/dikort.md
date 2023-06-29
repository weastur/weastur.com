+++
categories = ["archive"]
coders = []
date = 2023-06-27
description = "git commit message format checking tool"
github = ["https://github.com/weastur/dikort"]
title = "dikort"
type = "post"
[[tech]]
logo = "images/python.svg"
name = "Python"
url = "https://python.org/"
+++

The tool that helps you make commit messages in your repository more clear.

## Key Features

* Wide check list: author name, email, trailing periods, capitalize sentence, singleline summary, singoff, gpg, regex.
* Checks any commit range: acceptable for both CI and post-commit hook usage
* Separate rules for both: merge and regular commits
* Support all available python versions: 3.7+

## Technical Requirements/Installation

### Pre-requirements
Install any supported python distribution (for now it's 3.7+), and pip package management tool. Also make sure you have git installed

Examples:

#### Ubuntu/Debian
```shell
sudo apt install python3 python3-pip git
```

#### CentOS/RedHat/Fedora
```shell
sudo yum install python3 git
```

### Installation

By default, pip tries to install package directly to you system. You may need to use sudo to achieve this

```shell
sudo pip3 install dikort
```

The more right way is to **install to your home directory**. But be sure you have `$HOME/.local/bin` at your `$PATH` variable
```shell
pip3 install --user dikort
```

## Running and Configuring

Dikort is a command line tool. To see all available options with explanation hit `dikort -h`.
The only one unnamed option is commit range in the notation of `"<commit1>..<commit2>"`, where `"commit1"` and `"commit2"` are any of:
hash, branch, tag, HEAD pointer.

### Examples

#### Check last commit. Use this in git post-commit hook
```shell
dikort HEAD~1..HEAD
```

#### Check last 10 commits
```shell
dikort HEAD~10..HEAD
```

#### Check all commits in fix-123 branch
```shell
dikort master..fix-123
```

#### Configure through command line
```shell
dikort --enable-length --enable-capitalized-summary --min-length=20 --max-length=72 HEAD~5..HEAD
```

#### Get log and save it (DEBUG mode)
```shell
dikort --enable-logging --logging-level=DEBUG 2>debug.log
```

### Run in docker

Also you can run inside docker. Just mount your repository to container and tell dikort where to find.

```shell
docker run -v `pwd`:/tmp/repo weastur/dikort:latest --repository=/tmp/repo --enable-length
```

## File configuration

Refer to [config example](https://github.com/weastur/dikort/blob/83fcb521a4d659c04a3ab627200820596d8886b1/dikort.example.cfg), as a full configuration file. By default, config searched at `./.dikort.cfg`

## Development Status

Dikort is in active development and accepts contributions. See our [Contributing](https://github.com/weastur/dikort#how-to-contribute) section below for more details.

We report new releases information [here](https://github.com/weastur/dikort/releases).

## How to contribute

Fork, clone, setup development environment. **No third-party build or test tools** need to be insttalled at your system.

```shell
python3 -m venv .venv
. ./.venv/bin/activate
pip install setuptools wheel
pip install -e '.[dev]'
```

After that you'll have dikort and all development tools installed into virtualenv. Just run here `dikort` to execute your development version.
Hack, then make PR. Don't forget to write unit tests, and check your code:

```shell
dikort
flake8 dikort
isort dikort
black dikort
coverage run -m unittest discover
coverage report
```

Or you can just install git-hooks

### Git hooks

```shell
ln -s -r -t ./.git/hooks/ ./hooks/*
```

## License

MIT, see [LICENSE](https://github.com/weastur/dikort/blob/83fcb521a4d659c04a3ab627200820596d8886b1/LICENSE).
