Ansible Role: Multi WordPress
=========

[![Build Status](https://travis-ci.org/CarlosLongarela/ansible-role-multi-wordpress.svg?branch=master)](https://travis-ci.org/CarlosLongarela/ansible-role-wordpress)
[![Percentage of issues still open](http://isitmaintained.com/badge/open/CarlosLongarela/ansible-role-multi-wordpress.svg)](http://isitmaintained.com/project/CarlosLongarela/ansible-role-multi-wordpress "Percentage of issues still open")
[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/CarlosLongarela/ansible-role-multi-wordpress.svg)](http://isitmaintained.com/project/CarlosLongarela/ansible-role-multi-wordpress "Average time to resolve an issue")

Multi WordPress site configuration and installation with WP Cli that also is installed.

Requirements
------------

None.

Role Variables
--------------

    wp_cli_url: "https://raw.github.com/wp-cli/builds/gh-pages/phar/wp-cli.phar"
    wp_cli_bin: "wp"
    wp_cli_path: "/usr/bin/{{ wp_cli_bin}}"
    wp_cli_packages: []

    wp_cli_webserver_user: www-data
    wp_cli_webserver_group: www-data

    wp_cli_sites:
      wp_site_default:
        locale: "es_ES"
        path: "/home/webs/wordpress"
        version: "latest"

        db: "dbname"
        db_user: "dbuser"
        db_pass: "dbpassword"
        db_host: "localhost"
        dp_prefix: "wp_"

        url: "example.com"
        title: "WordPress Site"
        admin_user: "supervisor"
        admin_password: "strongpassword"
        admin_email: "info@example.com"

Dependencies
------------

- [CarlosLongarela.mariadb](https://galaxy.ansible.com/CarlosLongarela/mariadb/)
- [CarlosLongarela.nginx](https://galaxy.ansible.com/CarlosLongarela/nginx/)
- [CarlosLongarela.php7](https://galaxy.ansible.com/CarlosLongarela/php7/)

Example Playbook
----------------

    - hosts: servers

      gather_facts: no
      become: true

      vars:
        wp_cli_url: "https://raw.github.com/wp-cli/builds/gh-pages/phar/wp-cli.phar"
        wp_cli_bin: "wp"
        wp_cli_path: "/usr/bin/{{ wp_cli_bin}}"
        wp_cli_packages: []

        wp_cli_webserver_user: www-data
        wp_cli_webserver_group: www-data

        wp_cli_sites:
          wp_site_default:
            locale: "es_ES"
            path: "/home/webs/wordpress"
            version: "latest"

            db: "dbname"
            db_user: "dbuser"
            db_pass: "dbpassword"
            db_host: "localhost"
            dp_prefix: "wp_"

            url: "example.com"
            title: "WordPress Site"
            admin_user: "supervisor"
            admin_password: "strongpassword"
            admin_email: "info@example.com"

      roles:
         - { role: CarlosLongarela.multi-wordpress }

License
-------

GPLv2

Author Information
------------------

This role was created in 2017, Jun by [Carlos Longarela](mailto:carlos@longarela.eu), from [Taberna WordPress](https://tabernawp.com/).
