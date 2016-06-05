arnaudblancher.docker_unprovisionning
===================================

Goal: destroy dockers containers with ansible role arnaudblancher.docker_unprovisonning

This role is the companion of arnaudblancher.docker_provisionning witch take an ansible inventory and create one docker container for each listed hosts.


Requirements
------------

- docker-engine

Make sure your have a docker-engine running, test with (probably as root ...)

```bash
docker info
```

Role Variables
--------------

please see [defaults/main.yml](defaults/main.yml)

Dependencies
------------

None

Example Playbook
----------------
Please see subdirectory [./demo/](./demo/)

cat demo/docker-unprovisionning.yml
```yaml
- name: "remove docker containers and network"
  hosts: localhost
  gather_facts: no

  roles:
    - { role : arnaudblancher.docker_unprovisionning,
      docker_unprovisionning_net: "ansible_myplateform" }
```

cat inventory/docker/000_hosts
```yaml
[mysql]
dock-mysql

[apache]
dock-apache

[all:vars]
ansible_connection=docker
```

call :
```bash
ansible-playbook -i ./inventory/docker/ docker-unprovisionning.yml
```

Of course, you could use the same inventory for create and destroy yours containers.

License
-------

GPLv3

Author Information
------------------

Arnaud Blancher

[https://github.com/arnaudblancher/ansible-role-docker_unprovisionning](https://github.com/arnaudblancher/ansible-role-docker_unprovisionning)


