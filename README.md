# Express app with MySQL and nodemon development server

In this step we'll link a [MySQL](https://registry.hub.docker.com/_/mysql/) container to the app.

## Prerequisites

Install [Docker](https://www.docker.com/) on your system.

* [Install instructions](https://docs.docker.com/installation/mac/) for Mac OS X
* [Install instructions](https://docs.docker.com/installation/ubuntulinux/) for Ubuntu Linux
* [Install instructions](https://docs.docker.com/installation/) for other platforms

Install [Docker Compose](http://docs.docker.com/compose/) on your system.

* Python/pip: `sudo pip install -U docker-compose`
* Other: ``curl -L https://github.com/docker/compose/releases/download/1.1.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose; chmod +x /usr/local/bin/docker-compose``
## Setup

Run `docker-compose build`. It will

* install [nodemon](https://github.com/remy/nodemon) globally in your container
* install all dependencies from the package.json locally
* map port 3000 of container to port 80 to host
* instruct the container to execute `npm start` on start up.

## Start

Run `docker-compose up` to create and start both `web` and `db` container. The app should then be running on your docker daemon on port 80 (On OS X you can use `boot2docker ip` to find out the IP address).

This app demonstrates websockets using [Socket.IO](http://www.socket.io), [Node.js](http://www.nodejs.org) and MySQL inside a [Docker](http://www.docker.com) containers. It utilizes [docker compose](https://docs.docker.com/compose/) to run a multi-container setup. One container is the Node.js app and the other is a MySQL container. The file systems are mapped from the host. We are also using [nodemon](http://nodemon.io/) to run our Node.js app.

## Notes on boot2docker

It [appears](https://github.com/boot2docker/boot2docker/issues/290) that boot2docker (OS X, Windows) currently does not automatically sync the system clock with the host system after a host resumes from sleep. This becomes a problem due to the way nodemon detects file changes. That might cause it to go bananas, if the clocks on both systems are "too much" out of sync. Until this is fixed, you might use [this workaround](https://github.com/boot2docker/boot2docker/issues/290#issuecomment-62384209) or simply do a manual sync via

```bash
/usr/local/bin/boot2docker ssh sudo ntpclient -s -h pool.ntp.org
```
http://www.nodejs.org) and MySQL inside a [Docker](http://www.docker.com) containers. It utilizes [docker compose](https://docs.docker.com/compose/) to run a multi-container setup. One container is the Node.js app and the other is a MySQL container. The file systems are mapped from the host. We are also using [nodemon](http://nodemon.io/) to run our Node.js app.
