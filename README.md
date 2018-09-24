Role Name
=========
[![Build Status](https://travis-ci.org/matic-insurance/ansible-docker-mongodb.svg?branch=master)](https://travis-ci.org/matic-insurance/ansible-docker-mongodb)

Ansible role to manage and run the PostreSQL docker container. It optionally creates initial user and database.

It uses data container for persistence, which is more elegant way comparing to host volumes.


Requirements
------------

Ubuntu 14.04 is tested.

This role uses Ansible's docker module, so requirements are [the same](https://docs.ansible.com/ansible/docker_image_module.html#requirements-on-host-that-executes-module).

Role Variables
--------------

Here is the list of default variables with default values:

```
mongodb_docker_image: mongodb
mongodb_docker_image_tag: 9.5
mongodb_container_name: 'mongodb'
mongodb_port: 5432
```

Also you can set optional variables to create initial user/database.

```
mongodb_user: db_user
mongodb_password: db_password
mongodb_database: my_db
mongodb_schema: my_db_schema
mongodb_networks: [
  { name: backend }
]
```

Docker tuning can be done with this variables
```
container_memory_limit: 512m
```

Dependencies
------------

No dependencies

Example Playbook
----------------

    - hosts: database
      roles:
        - role: matic-insurance.docker-mongodb
          tags: ['database]
          mongodb_user: 'db_user'
          mongodb_password: 'db_password' # better put to Vault
          mongodb_database: 'my_db'

License
-------

MIT

Author Information
------------------

Matic is a communication platform that connects lenders and borrowers originating a new home loan. A borrower now knows where they are in the loan process and what they need to do to complete the loan.
