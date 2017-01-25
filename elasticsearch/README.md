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

Requirements
------------

This role uses only core modules.

Role Variables
--------------

There are 12 variables at play in this role:

Name                               | Type           | Default                                                          | Purpose
-----------------------------------|----------------|------------------------------------------------------------------|-----------
`satellite_elasticsearch_pool_id`  | string         | 2d7b40134a74d510014ada9a019f02bb2d7b40134a74d510014ada9a019f02bb | Pool ID for elasticsearch subscription pool
`elasticsearch_version`            | string         | NULL                                                             | version of elasticsearch
`es_cluster_name`                  | string         | NULL                                                             | elasticsearch cluster name
`elasticsearch_config_dir`         | string         | /etc/elasticsearch                                               | elasticsearch configuration directory
`elasticsearch_data_dir`           | string         | /opt/elasticsearch                                               | elasticsearch data directory
`elasticsearch_data_node`          | string         | true                                                             | node is a data storage node
`elasticsearch_master_node`        | string         | false                                                            | node is a master node with http access
`elasticsearch_autodiscovery_hosts`| list of strings| NULL                                                             | elasticsearch unicast autodiscovery nodes
`es_heap_size`                     | string         | 8g                                                               | elasticsearch memory heap size
`elasticsearch_manage`             | string         | false                                                            | management toggle
`elasticsearch_high_watermark`     | string         | 40gb                                                              | disk usage at which shards are allocated away
`elasticsearch_low_watermark`      | string         | 60gb                                                              | disk usage at which shard allocation stops

This current set of defaults is based on the belief that we will not be setting up elasticsearch nodes for use by other teams besides EIS. If that is the case these
defaults may need to be revisited. However because of the way that these defaults are currently written, the only thing necessary to get elasticsearch running
(aside from enabling the java role and setting a valid java version variable) is to enable the management toggle variable and run the role against your target hosts.

Playbook Usage
----------------

Since the existing elasticsearch playbook simply calls this role on a set of hosts, you can either change the configuration for that set of hosts or implement it in your playbook as below:

    - hosts: some hosts
      roles:
        - elasticsearch


# Requirements

Sudo access on remote host.

# License

Sony Pictures Entertainment. All rights reserved

# Author Information

Jason Ritzke
