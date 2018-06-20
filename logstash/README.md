logstash role
=========

This role enables our internal logstash repository pool and installs and configures logstash.

OS Versions:
- RHEL 6
-- This role functions on RHEL 6.

Requirements
------------

This role uses only core modules.

Role Variables
--------------

There are 2 variables at play in this role:

Name                               | Type           | Default                                                          | Purpose
-----------------------------------|----------------|------------------------------------------------------------------|-----------
`satellite_logstash_pool_id`       | string         | 2d7b40134a74d510014ada9a019f02bb2d7b40134a74d510014ada9a019f02bb | Pool ID for logstash subscription pool
`logstash_manage`                  | string         | false                                                            | management toggle

Playbook Usage
----------------

Since the existing logstash playbook simply calls this role on a set of hosts, you can either change the configuration for that set of hosts or implement it in your playbook as below:

    - hosts: some hosts
      roles:
        - logstash
