Nginx
=====

[![Build Status](https://travis-ci.org/injectedMonkey/ansible-role-nginx.svg?branch=master)](https://travis-ci.org/injectedMonkey/ansible-role-nginx)
[![License](https://img.shields.io/badge/License-BSD%202--Clause-orange.svg)](https://opensource.org/licenses/BSD-2-Clause)
[![GitHub release](https://img.shields.io/github/release/injectedMonkey/ansible-role-nginx.svg?style=flat)](https://github.com/injectedMonkey/ansible-role-nginx/releases)

Ansible role for nginx. It's designed for my development environment
but might reach sometimes production ready state.

Supported distributions:
- Debian
- Ubuntu

This role uses HTTP/2 transport protocoll for that TLS is required, but configured.

Requirements
------------

This role requires ansible >= 2.4.

Dictionaries are used for configuration. Partially overriding defaults needs
      'hash_behaviour = merge'
set in your ansible.cfg or set
      ANSIBLE_HASH_BEHAVIOUR=merge
for your environment.

Role Variables
--------------

      nginx:
        user: www-data
        group: www-data
        sites:
          - host_name: example.com
            document_root: /var/www/example.com
            # Specify the host config file (tempaltes/*.block.conf.j2)
            block_template: static
            # Set environment variable used in host config
            environment:
              # This is actually required when using php-fpm/symfony config
              APP_ENV: development


Dependencies
------------

None.


Example Playbook
----------------

    - hosts: servers
    - include_role:
        name: injectedMonkey.nginx
      vars:
        nginx:
          user: www-data
          group: www-data
          sites:
            - host_name: example.com
              document_root: /var/www/example.com
              block_template: static
              environment:
                APP_ENV: development

License
-------

BSD

Author Information
------------------

injectedMonkey.wtf
