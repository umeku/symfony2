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
    current -> release
```

Requirements
------------

You need to install git, php, composer before running this role.

Installation
------------

```bash
ansible-galaxy install umeku.symfony2
```

Example Playbook
----------------

```yml
- hosts: all
  gather_facts: no
  vars:
    symfony2_name: project
    symfony2_repo: git@github.com:repo/project.git
    symfony2_root: /var/www/{{ symfony2_name }}
    symfony2_shared_dirs:
      - app/logs
      - web/media
      - web/uploads
    symfony2_console_commands:
      - "assets:install --symlink web"
      - "assetic:dump --no-debug"
      - "doctrine:schema:update --force"
      - "cache:warmup"
    symfony2_extra_commands:
      - "gulp default"

  roles:
    - umeku.symfony2
```

Check [defaults/main.yml](defaults/main.yml) for more configuration options.

License
-------

MIT
