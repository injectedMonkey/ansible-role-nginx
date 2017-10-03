Nginx
=====

[![Build Status](https://travis-ci.org/injectedMonkey/ansible-role-nginx.svg?branch=master)](https://travis-ci.org/injectedMonkey/ansible-role-nginx)
[![License](https://img.shields.io/badge/License-BSD%202--Clause-orange.svg)](https://opensource.org/licenses/BSD-2-Clause)
[![GitHub release](https://img.shields.io/github/release/injectedMonkey/ansible-role-nginx.svg?style=flat)](https://github.com/injectedMonkey/ansible-role-nginx/releases)

Simple nginx role. It's designed for my development environment
but might reach sometimes production ready state. It supports Debian/Ubuntu.

This role uses HTTP/2 transport protocoll for that TLS is required, but configured.

Requirements
------------

This role is developed with Ansible 2.4. Backwards compatibility is not garanteed.


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

None. But php will be usefull when setting up fastcgi/php-fpm forwarding ;)


Example Playbook
----------------

    - hosts: servers
    - include_role:
        name: nginx
      vars:
        nginx:
          user: www-data
          group: www-data
          sites:
            - host_name: example.com
              document_root: /var/www/example.com
              block_template: static
              environment:
                APP_ENV: develo

License
-------

BSD

Author Information
------------------

injectedMonkey.wtf
