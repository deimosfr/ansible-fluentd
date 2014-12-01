Ansible Fluentd playbook
=====

This role installs and configures Fluentd v1.x on a Debian server.

Requirements
------------

This role requires Ansible 1.4 or higher and platform requirements are listed
in the metadata file.

Role Variables
--------------

The variables that can be passed to this role and a brief description about
them are as follows.

```
# fluentd fqdn used by forwarders to fluentd
fluentd_server_fqdn: fluentd-server.fqdn

# Address of elasticsearch used by fluentd
es_fqdn: localhost
es_port: 9200

# If this machine should forward to Elasticsearch
forward_to_es: True

# Syslog plugin
fluentd_plugin_syslog_ip: 127.0.0.1
fluentd_plugin_syslog_port: 5140
```

Examples
========

```
# Fluentd clients
- name: common
  hosts: all
  user: root
  roles:
    - fluentd
  vars:
    - fluentd_server_fqdn: fluentd-server.fqdn
    - es_fqdn: localhost
    - es_port: 9200
    - fluentd_plugin_syslog_ip: 127.0.0.1
    - fluentd_plugin_syslog_port: 5140


# Fluentd server
- name: log server
  hosts: logs
  user: root
  roles:
    - fluentd
  vars:
    - es_fqdn: localhost
    - es_port: 9200
    - forward_to_es: True
```

Dependencies
------------

None

License
-------

GPL

Author Information
------------------

Pierre Mavro / deimosfr


