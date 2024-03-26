# Ansible role [php_fpm](https://galaxy.ansible.com/ui/standalone/roles/buluma/php_fpm/documentation)

The purpose of this role is to install and configure php_fpm on your system.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-php_fpm/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-php_fpm/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-php_fpm.svg)](https://github.com/buluma/ansible-role-php_fpm/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-php_fpm.svg)](https://github.com/buluma/ansible-role-php_fpm/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-php_fpm.svg)](https://github.com/buluma/ansible-role-php_fpm/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/php_fpm)](https://galaxy.ansible.com/ui/standalone/roles/buluma/php_fpm/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-php_fpm/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.php_fpm
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-php_fpm/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: buluma.bootstrap
    - role: buluma.epel
    - role: buluma.buildtools
    - role: buluma.python_pip
    - role: buluma.openssl
      openssl_items:
        - name: apache-httpd
          common_name: "{{ ansible_fqdn }}"
    - role: buluma.httpd
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-php_fpm/blob/master/defaults/main.yml):

```yaml
---
# defaults file for php_fpm

# The `php_fpm_listen` parameter can be an address:port combination or a path
# if you want to use a socket. For example: "127.0.0.1:9000"

php_fpm_listen: "{{ php_fpm_pid_directory }}/www.sock"

# When using a socket in `php_fpm_listen`, you can set the user and group.
# Sane defaults are set in `vars/main.yml`
php_fpm_listen_owner: "{{ php_fpm_owner }}"
php_fpm_listen_group: "{{ php_fpm_group }}"
php_fpm_listen_mode: "0666"

php_fpm_pm: dynamic
php_fpm_pm_max_children: 5
php_fpm_pm_start_servers: 2
php_fpm_pm_min_spare_servers: 1
php_fpm_pm_max_spare_servers: 3
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-php_fpm/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.buildtools](https://galaxy.ansible.com/buluma/buildtools)|[![Ansible Molecule](https://github.com/buluma/ansible-role-buildtools/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-buildtools/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-buildtools.svg)](https://github.com/shadowwalker/ansible-role-buildtools)|
|[buluma.epel](https://galaxy.ansible.com/buluma/epel)|[![Ansible Molecule](https://github.com/buluma/ansible-role-epel/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-epel/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-epel.svg)](https://github.com/shadowwalker/ansible-role-epel)|
|[buluma.openssl](https://galaxy.ansible.com/buluma/openssl)|[![Ansible Molecule](https://github.com/buluma/ansible-role-openssl/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-openssl/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-openssl.svg)](https://github.com/shadowwalker/ansible-role-openssl)|
|[buluma.python_pip](https://galaxy.ansible.com/buluma/python_pip)|[![Ansible Molecule](https://github.com/buluma/ansible-role-python_pip/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-python_pip/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-python_pip.svg)](https://github.com/shadowwalker/ansible-role-python_pip)|
|[buluma.selinux](https://galaxy.ansible.com/buluma/selinux)|[![Ansible Molecule](https://github.com/buluma/ansible-role-selinux/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-selinux/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-selinux.svg)](https://github.com/shadowwalker/ansible-role-selinux)|
|[buluma.httpd](https://galaxy.ansible.com/buluma/httpd)|[![Ansible Molecule](https://github.com/buluma/ansible-role-httpd/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-httpd/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-httpd.svg)](https://github.com/shadowwalker/ansible-role-httpd)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-php_fpm/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/r/buluma/debian)|jessie, stretch|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|
|[opensuse](https://hub.docker.com/r/buluma/opensuse)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|bionic|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-php_fpm/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-php_fpm/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-php_fpm/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)
