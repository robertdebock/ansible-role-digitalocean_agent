digitalocean-agent
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-digitalocean-agent.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-digitalocean-agent)

Installs the digitalocean-agent for your system to improve monitoring in Digital Ocean.


Example Playbook
----------------

This example is taken from `molecule/default/playbook.yml`:
```
---
- name: Converge
  hosts: all
  become: true
  gather_facts: false

  roles:
    - robertdebock.bootstrap
    - robertdebock.digitalocean-agent

```

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```
---
# defaults file for digitalocean-agent

# To update all packages installed by this roles, set `digitalocean-agent_package_state` to `latest`.
digitalocean-agent_package_state: present

```

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the last 3 release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

---
- robertdebock.bootstrap


Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/digitalocean-agent.png "Dependency")


Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.4|ansible 2.5|ansible 2.6|ansible 2.7|ansible devel|
|------------|-----------|-----------|-----------|-----------|-------------|
|alpine-edge*|no|no|no|no|no*|
|alpine-latest|no|no|no|no|no*|
|archlinux|no|no|no|no|no*|
|centos-6|yes|yes|yes|yes|yes*|
|centos-latest|yes|yes|yes|yes|yes*|
|debian-latest|no|no|no|no|no*|
|debian-stable|no|no|no|no|no*|
|debian-unstable*|no|no|no|no|no*|
|fedora-latest|yes|yes|yes|yes|yes*|
|fedora-rawhide*|yes|yes|yes|yes|yes*|
|opensuse-leap|no|no|no|no|no*|
|opensuse-tumbleweed|no|no|no|no|no*|
|ubuntu-artful|no|no|no|no|no*|
|ubuntu-devel*|no|no|no|no|no*|
|ubuntu-latest|no|no|no|no|no*|

A single star means the build may fail, it's marked as an experimental build.

Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-digitalocean-agent) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-digitalocean-agent/issues)

To test this role locally please use [Molecule](https://github.com/metacloud/molecule):
```
pip install molecule
molecule test
```
There are many specific scenarios available, please have a look in the `molecule/` directory.


License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
