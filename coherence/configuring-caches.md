---
description: Caches are configured in a cache configuration deployment descriptor.
---

# Configuring Caches

By default, Coherence attempts to load the first `coherence-cache-config.xml` deployment descriptor that is found in the classpath. The schema definition of the cache configuration descriptor is the `coherence-cache-config.xsd` file, which imports the `coherence-cache-config-base.xsd` file, which, in turn, implicitly imports the `coherence-config-base.xsd` file. This file is located in the root of the `coherence.jar` file. 

## Defining Cache Mappings

Cache mappings map a cache name to a cache scheme definition. The mappings provide a level of separation between applications and the underlying cache definitions.

Cache mappings are defined using a `<cache-mapping>` element within the `<cache-scheme-mapping>` node.

{% code title="Sample Cache Name Pattern Mapping" %}
```markup
<?xml version="1.0"?>

<cache-config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xmlns="http://xmlns.oracle.com/coherence/coherence-cache-config"
   xsi:schemaLocation="http://xmlns.oracle.com/coherence/coherence-cache-config
   coherence-cache-config.xsd">
   <caching-scheme-mapping>
      <cache-mapping>
         <cache-name>*</cache-name>
         <scheme-name>distributed</scheme-name>
         <init-params>
            <init-param>
               <param-name>back-size-limit</param-name>
               <param-value>8MB</param-value>
            </init-param>
         </init-params>
      </cache-mapping>
      <cache-mapping>
         <cache-name>account-*</cache-name>
         <scheme-name>account-distributed</scheme-name>
      </cache-mapping>
   </caching-scheme-mapping>

   <caching-schemes>
      <distributed-scheme>
         <scheme-name>distributed</scheme-name>
      </distributed-scheme>
      <distributed-scheme>
         <scheme-name>account-distributed</scheme-name>
      </distributed-scheme>
   </caching-schemes>
</cache-config>
```
{% endcode %}

## Defining Cache Schemes

### Defining Distributed Cache Schemes

{% code title="Sample Distributed Cache Definition" %}
```markup
<?xml version="1.0"?>

<cache-config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xmlns="http://xmlns.oracle.com/coherence/coherence-cache-config"
   xsi:schemaLocation="http://xmlns.oracle.com/coherence/coherence-cache-config
   coherence-cache-config.xsd">
   <caching-scheme-mapping>
      <cache-mapping>
         <cache-name>example</cache-name>
         <scheme-name>distributed</scheme-name>
      </cache-mapping>
   </caching-scheme-mapping>

   <caching-schemes>
      <distributed-scheme>
         <scheme-name>distributed</scheme-name>
         <backing-map-scheme>
            <local-scheme/>
         </backing-map-scheme>
         <autostart>true</autostart>
      </distributed-scheme>
   </caching-schemes>
</cache-config>
```
{% endcode %}

### Defining Replicated Cache Schemes

```markup
<?xml version="1.0"?>

<cache-config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xmlns="http://xmlns.oracle.com/coherence/coherence-cache-config"
   xsi:schemaLocation="http://xmlns.oracle.com/coherence/coherence-cache-config
   coherence-cache-config.xsd">
   <caching-scheme-mapping>
      <cache-mapping>
         <cache-name>example</cache-name>
         <scheme-name>replicated</scheme-name>
      </cache-mapping>
   </caching-scheme-mapping>

   <caching-schemes>
      <replicated-scheme>
         <scheme-name>replicated</scheme-name>
         <backing-map-scheme>
            <local-scheme/>
         </backing-map-scheme>
         <autostart>true</autostart>
      </replicated-scheme>
   </caching-schemes>
</cache-config>
```

### Defining Optimistic Cache Schemes

```markup
<?xml version="1.0"?>

<cache-config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xmlns="http://xmlns.oracle.com/coherence/coherence-cache-config"
   xsi:schemaLocation="http://xmlns.oracle.com/coherence/coherence-cache-config
   coherence-cache-config.xsd">
   <caching-scheme-mapping>
      <cache-mapping>
         <cache-name>example</cache-name>
         <scheme-name>optimistic</scheme-name>
      </cache-mapping>
   </caching-scheme-mapping>

   <caching-schemes>
      <optimistic-scheme>
         <scheme-name>optimistic</scheme-name>
         <backing-map-scheme>
            <local-scheme/>
         </backing-map-scheme>
         <autostart>true</autostart>
      </optimistic-scheme>
   </caching-schemes>
</cache-config>
```

### Defining Local Cache Schemes

```markup
<?xml version="1.0"?>

<cache-config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xmlns="http://xmlns.oracle.com/coherence/coherence-cache-config"
   xsi:schemaLocation="http://xmlns.oracle.com/coherence/coherence-cache-config
   coherence-cache-config.xsd">
  <caching-scheme-mapping>
    <cache-mapping>
      <cache-name>example</cache-name>
      <scheme-name>local</scheme-name>
    </cache-mapping>
  </caching-scheme-mapping>

  <caching-schemes>
    <local-scheme>
      <scheme-name>local</scheme-name>
      <eviction-policy>LRU</eviction-policy>
      <high-units>32000</high-units>
      <low-units>10</low-units>
      <unit-calculator>FIXED</unit-calculator>
      <expiry-delay>10ms</expiry-delay>
    </local-scheme>
  </caching-schemes>
</cache-config>
```



