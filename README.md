ansible-role-symfony2
=====================

Ansible role to deploy Symfony2 application.

It can deploy via `rsync`, `git`, `svn` and `mercurial`, generate `parameters.yml` if needed, run `php app/console` commands you defined.

It makes capifony-like directory structure:

```bash
  root
    releases
      release
    shared
      app/logs
      web/uploads
    current
```

Requirements
------------

You need to install git, php, composer before running this role.

Installation
------------

```bash
ansible-galaxy install umeku.symfony2
```

Usage
-----

```yml
- hosts: all
  vars:
    symfony2_name: project
    symfony2_domain: "project.com"
    symfony2_repo: git@github.com:repo/project.git

  roles:
    - umeku.symfony2
```

License
-------

MIT
