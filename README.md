ansible-docker
--------------

Ansible role to manage docker installation.

Requirements
------------


Role Variables
--------------


Dependencies
------------

This is a standalone role.

Example Playbook
----------------

Install docker with the default configuration:

    - hosts: servers
      roles:
         - ansible-docker

Install docker, set HTTP proxies and monitor the daemon using Consul:

    - hosts: servers
      roles:
         - ansible-docker
      vars:
         # Consul
         docker_config_consul: true
         
         # Proxy
         docker_http_proxy: http://proxy.local:3128
         docker_no_proxy: local,example.com
         
         # Log management
         # Default: journald
         docker_log_driver: json-file

Install docker, login against a private registry:

    - hosts: servers
      roles:
         - ansible-docker
      vars:
         docker_registry_credentials:
            - url: https://my-registry.local
              login: foo
              password: bar
              cert: |
    -----BEGIN CERTIFICATE-----
    […]
    -----END CERTIFICATE-----

License
-------

GPL-3+

Author Information
------------------

Mathieu GRZYBEK
