---
title: Cache settings
slug: cache-settings
category: configuration
order: 1000
layout: docs
description: Configure the Search Guard internal caches and adapt them to your needs.
---
<!---
Copyright 2017 floragunn GmbH
-->
# User cache settings

Search Guard uses a cache to store the roles of authenticated users. The default time to live (TTL) is one hour. This will for example speed up LDAP based authorisation, since the roles are fetched only once per hour.

The TTL of the cache can be adjusted by setting `searchguard.cache.ttl_minutes` `in elasticsearch.yml`:

```yaml
searchguard.cache.ttl_minutes: <integer, ttl in minutes>`
```

Setting the value to `0` will completely disable the cache.

**This feature is available since SG 15 and for ES 5.4.3 or higher**
