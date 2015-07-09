# NODE

Docker Image for [Node.js](https://nodejs.org) based on airdock/base:latest

Purpose of this image is:

- install [node, npm]https://nodejs.org)
- based on airdock/base:latest (debian)


> Name: airdock/node

***Tags***:

- 'latest' or '12': nodejs version 0.12
- '10': nodejs version 0.10

***Dependencies***: airdock/base:latest

***Few links***:

- [node.js](https://nodejs.org)
- [Node Distribution](https://github.com/nodesource/distributions)


# Usage

You should have already install [Docker](https://www.docker.com/).

Execute:

		docker run -d -p 80:80 -p 443:443 --name node airdock/node node parameters-for-node

To overide entry point do:

		docker run -ti --name node airdock/node /bin/bash  -l


The user node (uid 33) in your container should be known into your host. As it is a standard user, it should be erver present.
See :
* [How Managing user in docker container ?](https://github.com/airdock-io/docker-base/wiki/How-Managing-user-in-docker-container)
* [Common User List](https://github.com/airdock-io/docker-base/wiki/Common-User-List)


If 'node' user is not present, you should create it with this uid:gid:

```
  sudo groupadd node -g 33
  sudo useradd -u 33  --no-create-home --system --no-user-group node
  sudo usermod -g node node
```

And then set owner and permissions on your host directory:

```
	chown -R node:node /some/content
```
Don't forget to add your current user to this new group.


# Change Log

## TODO

- add gnupg validation
- add checksum validation

## Tag latest or 12

- add node.js 0.12
- use user node:node
- MIT license

## Tag 10

- add node.js 0.10
- use user node:node
- MIT license

# Build


- Install "make" utility, and execute: `make build`
- Or execute: 'docker build -t airdock/node:latest --rm .'

See [Docker Project Tree](https://github.com/airdock-io/docker-base/wiki/Docker-Project-Tree) for more details.


# MIT License

```
The MIT License (MIT)

Copyright (c) 2015 Airdock.io

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
