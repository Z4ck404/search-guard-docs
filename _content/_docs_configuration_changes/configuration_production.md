---
title: Backup and Restore
slug: configuration-production
category: configuration
order: 400
layout: docs
description: How you can use sgadmin to quickly transfer your complete configuration from one system to another.
---
<!---
Copyright 2019 floragunn GmbH
-->
# Backup and Restore
{: .no_toc}

Once you have set up Search Guard on a testing or staging environment, you might want to replicate the exact Search Guard configuration on your production cluster.

If you have the Search Guard configuration files at hand, you can of course simply use [sgadmin](../_docs_configuration_changes/configuration_sgadmin.md) to upload them to production.

If you're unsure whether your configuration files actually resemble the active Search Guard configuration on your cluster, you can use [sgadmin](../_docs_configuration_changes/configuration_sgadmin.md) to retrieve the configuration from a running cluster, and upload it to another one:

Backup the current configuration from a cluster running on `staging.example.com` :

```
./sgadmin.sh -backup /etc/sgbackup/ -h staging.example.com -ts ... -tspass ... -ks ... -kspass ...
```

To upload the dumped files to another cluster, here `production.example.com` listening on port 9301, use:

```
./sgadmin.sh -h production.example.com -cd /etc/sgbackup/ 
    -ts ... -tspass ... -ks ... -kspass ...
```