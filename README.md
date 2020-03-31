# digitalocean-agent

Install digitalocean agent on your system.

|Travis|GitHub|Quality|Downloads|
|------|------|-------|---------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-digitalocean-agent.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-digitalocean-agent)|[![github](https://github.com/robertdebock/ansible-role-digitalocean-agent/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-digitalocean-agent/actions)|[![quality](https://img.shields.io/ansible/quality/)](https://galaxy.ansible.com/robertdebock/digitalocean-agent)|[![downloads](https://img.shields.io/ansible/role/d/)](https://galaxy.ansible.com/robertdebock/digitalocean-agent)|

## Example Playbook

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - robertdebock.digitalocean-agent
```

The machine may need to be prepared using `molecule/resources/prepare.yml`:
```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - robertdebock.bootstrap
    - robertdebock.ca_certificates
    - robertdebock.apt_autostart
```

For verification `molecule/resources/verify.yml` run after the role has been applied.
```yaml
---
- name: Verify
  hosts: all
  become: no
  gather_facts: no

  tasks:
    - name: check /opt/digitalocean/bin/do-agent
      stat:
        path: /opt/digitalocean/bin/do-agent
      register: check_do_agent

    - name: collect service_facts
      service_facts:
      register: service_facts

    - name: check conditions
      assert:
        that:
          - check_do_agent.stat.exists
          - check_do_agent.stat.executable
          - services['do-agent.service'].state == "running"
          - services['do-agent.service'].status == "enabled"
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## Role Variables

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for digitalocean-agent
```

## Requirements

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap
- robertdebock.ca_certificates
- robertdebock.apt_autostart

```

## Context

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/digitalocean-agent.png "Dependency")

## Compatibility

This role has been tested on these [container images](https://hub.docker.com/):

|container|tags|
|---------|----|
|el|7, 8|
|fedora|all|

The minimum version of Ansible required is 2.8 but tests have been done to:

- The previous version, on version lower.
- The current version.
- The development version.

## Exceptions

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| Alpine | do-agent (missing) |
| Archlinux | target not found: do-agent |
| Debian | ln: failed to create symbolic link '/etc/systemd/system/multi-user.target.wants/do-agent.service': No such file or directory |
| Suse | No provider of '+do-agent |
| Ubuntu | ln: failed to create symbolic link '/etc/systemd/system/multi-user.target.wants/do-agent.service': No such file or directory |


## Testing

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-digitalocean-agent) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-digitalocean-agent/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## License

Apache-2.0


## Author Information

[Robert de Bock](https://robertdebock.nl/)
