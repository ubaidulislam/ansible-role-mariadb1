Ansible Role: MariaDB
===

<p>
<a href="https://travis-ci.org/UbzyHD/ansible-role-mariadb"><img src="https://img.shields.io/travis/UbzyHD/ansible-role-mariadb/main?label=build&logo=travis-ci&style=flat-square"></a>
<p>
<a href="https://galaxy.ansible.com/ubzyhd/mariadb"><img src="https://img.shields.io/ansible/role/53560?color=blueviolet&logo=Ansible&style=flat-square"></a>
<p>
<img src="https://img.shields.io/badge/dynamic/json?label=Description&style=flat-square&query=description&url=https%3A%2F%2Fgalaxy.ansible.com%2Fapi%2Fv1%2Fcontent%2F53560%2F">
<p>
<img src="https://img.shields.io/ansible/quality/53560?label=Quality%20Score&logo=ansible&style=flat-square">
<p>
<img src="https://img.shields.io/ansible/role/d/53560?logo=Ansible&style=flat-square">
</p>

## Contents

- [Ansible Role: MariaDB](#ansible-role-mariadb)
  - [Contents](#contents)
  - [Supported & Tested OS's](#supported--tested-oss)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [License](#license)

Supported & Tested OS's
---
Debian:

- 10 - Buster
- 9 - Stretch

Requirements
------------

This role assumes it will be deployed on a pre-configured server that doesn't already have MariaDB installed. If installed, then the setup process will be skipped unless the force_setup has been defined.

Role Variables
--------------
Global variables:
```yaml
# not set unless
force_setup: 
```

OS specific variables:
```yaml
mariadb_repo_url: https://mirrors.ukfast.co.uk/sites/mariadb/repo/10.5/debian
```

Example Playbook
----------------
```yaml
---
- name: Database
  hosts: all
  remote_user: ansible
  become: yes

  gather_facts: true

  pre_tasks:

    - name: Database | Pinging hosts
      action: ping

    - name: Database | Install Python if not already present.
      raw: test -e /usr/bin/python || (apt -y update && apt install -y python-minimal)
      changed_when: false

    - name: Database | Gather facts after Python is definitely present.
      setup:

  roles:
    - ubzyhd.mariadb
```

License
-------

GNU AGPLv3
