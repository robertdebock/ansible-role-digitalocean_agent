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

- [robertdebock.bootstrap](https://travis-ci.org/robertdebock/ansible-role-bootstrap)


Download the dependencies by issuing this command:
```
ansible-galaxy install --role-file requirements.yml
```

Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.3|ansible 2.4|ansible 2.5|
|------------|-----------|-----------|-----------|
|alpine-3.6|no|no|no|
|alpine-3.7|no|no|no|
|archlinux|no|no|no|
|centos-6|yes|yes|yes|
|centos-7|yes|yes|yes|
|debian-buster|no|no|no|
|debian-stretch|no|no|no|
|fedora-27|yes|yes|yes|
|fedora-28|yes|yes|yes|
|opensuse-42.2|no|no|no|
|opensuse-42.3|no|no|no|
|ubuntu-artful|no|no|no|
|ubuntu-bionic|no|no|no|

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

Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
