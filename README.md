dockit
======

A command line tool that helps manage a group of [Docker](https://www.docker.io/) containers. Think of it as [Vagrant](http://www.vagrantup.com/) for Docker.

You create an inventory file of the images you want to use, then you simply run:

    dockit up

And all of your Docker containers will be created and started. If the containers have not been pulled, they will be pulled down. Then the containter is created and started.

Most other standard docker container commands can be run as well, like start|stop|kill.

You can also use the `destroy` command to completely remove the containers. One limitation of this is it will leave any images that were pulled down.

Requirements
============

* [Docker](https://www.docker.io/)
* [docker-py](https://github.com/dotcloud/docker-py)

Installation
============

Install via PIP
---------------

Coming soon.

Install via source
------------------

    me@myhost$ git clone https://github.com/eltimn/dockit.git
    me@myhost$ mkdir ~/bin
    me@myhost$ ln -s /path/to/dockit/dockit ~/bin/dockit

How to Use
==========

First create a `dockit.yml` inventory file to use. Dockit will look in the current directory for this first. You can specify the inventory file using the `-i` option.

Here's an example:

    ---
    description: Development Environment
    name: myapp
    containers:
      - image: eltimn/mongo
        name: myapp_mongo
        command: "--noprealloc --smallfiles --rest"
        before_start: sudo mkdir -p /srv/myapp/mongo-data
        ports:
          27017/tcp: 2700
          28017/tcp: 2701
        volumes:
          /srv/myapp/mongo-data: /data/db
      - image: eltimn/rabbitmq
        name: myapp_rabbitmq
        environment:
          RABBITMQ_USER: "myapp"
          RABBITMQ_PASS: "myapp"
        ports:
          5672/tcp: 2703
          15672/tcp: 2704

Once that's setup, just run:

    dockit up

in the same directory as your dockit.yml file. That's it! All of your containers should have started.

Usage
=====

<pre>
Usage: dockit [OPTIONS] [COMMAND]
  -h --help         Display this usage message
  -c --container    The name (or id) of the docker container to use
  -i --inventory    The inventory file to use
  -v --verbose      Output more logging during execution.

Commands: create|destroy|inspect|kill|remove|restart|start|stop|top|up

If no container is specified via the -c option, the command will
be called for all containers listed in the inventory file.
</pre>

TODO
====

* Add links support
