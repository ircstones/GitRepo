elasticsearch role
=========

This role enables our internal elasticsearch repository pool and installs and configures elasticsearch.

OS Versions:
- RHEL 5
-- This role might be able to function on RHEL 5 in theory, but has not been tested (and is blocked by internal logic).
- RHEL 6
-- This role functions on RHEL 6.
- RHEL 7
-- This role could function on RHEL 7 in theory, but has not yet been tested (and is blocked by internal logic).


Playbook Usage
----------------

Since the existing elasticsearch playbook simply calls this role on a set of hosts, you can either change the configuration for that set of hosts or implement it in your playbook as below:

    - hosts: some hosts
      roles:
        - elasticsearch

