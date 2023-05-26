Ansible Role: Apache Guacamole
==============================

An ansible role to deploy ![Apache Guacamole](https://guacamole.apache.org/) with Docker and HAProxy as reverse proxy.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
default_user: "{{ ansible_user_id }}"
installation_path: "{{ ansible_env.HOME }}/docker-stack"
dockercompose_version: '3.9'
postgres_user: "guacamole_db_user"
postgres_password: "gcZYye@7U89JF%"
# define haproxy docker container version
haproxy_version: "2.4"

# define postgres docker container version
postgres_version: "15.0"

# define guacamole containers version
guacamole_backend_version: "1.5.0"
guacamole_frontend_version: "1.5.0"
```
where 
- `fqdn` is the Fully Qualified Domain Name you want to make your instance available. For example `guacamole.company.com`
- `default_user` is the user who will perform the installation
- `installation_path` is the target directory to put all the required files
- `dockercompose_version` is the docker-compose.yml file version
- `postgres_user` is the Postgres username
- `postgres_password` is the Postgres database password
- `haproxy_version` defines HAProxy docker image tag version
- `postgres_version` defines Postgres docker image tag version
- `guacamole_backend_version` defines guacamole/guacd docker image tag version
- `guacamole_frontend_version` defines guacamole/guacamole docker image tag version

Dependencies
------------
This role requires the following Ansible collection:
- community.general >= 6.5.0

Example Playbook
----------------

The example below will deploy Apache Guacamole on the remote server and make the instance accessible at `https://guacamole.company.local/guacamole`. A self-signed SSL certificate will be automatically generated for the FQDN:

    - hosts: server
      become: true
      vars:
        fqdn: guacamole.company.local
      roles:
         - theko2fi.apache_guacamole

The example below will deploy Apache Guacamole and make it available at `https://192-168-5-2.traefik.me/guacamole` where `192.168.5.2` is the IP address of the remote server. The URL will automatically be adapted according to your effective server IP address. A ![Let's Encrypt](https://letsencrypt.org/) signed certificate provided by ![traefik.me](http://traefik.me/) will be used.

    - hosts: server
      become: true
      roles:
         - theko2fi.apache_guacamole
Demo
----
![demo](https://github.com/theko2fi/ansible-role-apache-guacamole/assets/72862222/81b45598-dab6-48e9-81b7-66c5f88e85e2)

License
-------

MIT
BSD

Contributing
------------

Bug reports and pull requests are welcome on GitHub at https://github.com/theko2fi/ansible-role-apache-guacamole.git.

Author Information
------------------

Created by Kenneth KOFFI, you can reach him on the following platforms:

- medium: https://theko2fi.medium.com
- github: https://github.com/theko2fi
- linkedin: https://www.linkedin.com/in/kenneth-koffi-6b1218178
