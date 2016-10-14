ansible-arangodb
=========

Ansible playbook for installing ArangoDB 3

Installation
------------

ansible-galaxy install ernestas-poskus.ansible-arangodb

Requirements
------------

None.

Role Variables
--------------

```yaml
---
arangodb_service_name: 'arangodb3'
arangodb_package_name: 'arangodb3'

# defaults file for arangodb
arangodb_storage_directory: '/var/lib/arangodb3'

# log directory
arangodb_log_directory: '/var/log/arangodb3'

arangodb_endpoints:
  - 'tcp://127.0.0.1:8529'
  - "tcp://{{ ansible_default_ipv4['address'] }}:8529"

arangodb_authentication: 'true'
arangodb_user: 'root'
arangodb_user_pass: ''

arangodb_maximal_journal_size: 33554432

# number of server threads. use 0 to make arangod determine the
# number of threads automatically, based on available CPUs
arangodb_server_threads: 0

# gather server statistics
arangodb_statistics: 'true'

# the user and group are normally set in the start script
arangodb_owner: arangodb
arangodb_group: arangodb

# number of threads used for I/O, use 0 to make arangod determine
# the number of threads automatically
arangodb_scheduler_threads: 0

# Javascript
arangodb_startup_directory: '/usr/share/arangodb3/js'
arangodb_app_path: '/var/lib/arangodb3-apps'

# number of V8 contexts available for JavaScript execution. use 0 to
# make arangod determine the number of contexts automatically.
arangodb_v8_contexts: 0

# enable Foxx queues in the server
arangodb_queues: 'false'

# interval (seconds) to use for polling jobs in Foxx queues
arangodb_queues_poll_interval: 1

# Log
arangodb_level: 'info'
arangodb_file: "{{arangodb_log_directory}}/arangod.log"

# Cluster
arangodb_cluster_data_directory: '/var/lib/arangodb3/cluster'
arangodb_cluster_log_directory: '/var/log/arangodb3/cluster'
```

Dependencies
------------

None.

Example Playbook
----------------

```yamlp
- name: Installing ArangoDB
  hosts: arangodb
  sudo: yes
  roles:
    - role: ernestas-poskus.ansible-arangodb
```

License
-------


Author Information
------------------

Twitter: @ernestas_poskus
