digitalocean-agent
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-digitalocean-agent.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-digitalocean-agent)

Installs the digitalocean-agent for your system to improve monitoring in Digital Ocean.

Context
--------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/robertdebock.github.io/artifacts/digitalocean-agent.png "Dependency")

Requirements
------------

Access to a repository containing packages, likely on the internet.

Role Variables
--------------

- digitalocean-agent - The URL to the database.

Dependencies
------------

You can use this role to prepare your system:

- robertdebock.bootstrap

Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.3|ansible 2.4|ansible 2.5|
|------------|-----------|-----------|-----------|
|alpine-3.6|no|yes|yes|
|alpine-3.7|no|yes|yes|
|archlinux|no|yes|yes|
|centos-6|no|no|no|
|centos-7|no|yes|yes|
|debian-buster|no|yes|yes|
|debian-jessie|no|no|no|
|debian-stretch|no|yes|yes|
|fedora-26|no|yes|yes|
|fedora-27|no|yes|yes|
|opensuse-42.2|no|yes|yes|
|opensuse-42.3|no|yes|yes|
|ubuntu-artful|no|yes|yes|
|ubuntu-bionic|no|yes|yes|
|ubuntu-xenial|no|yes|yes|

Example Playbook
----------------

```
- hosts: servers

roles:
  - role: robertdebock.bootstrap
  - role: robertdebock.digitalocean-agent
```

Install this role using `galaxy install robertdebock.digitalocean-agent`.

License
-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock <robert@meinit.nl>
