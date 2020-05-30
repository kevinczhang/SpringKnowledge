---
description: >-
  The Spring Boot framework allows the integration of various cache providers,
  such as EhCache, Redis, Hazelcast, Infinispan, Caffeine, etc.
---

# Cache Provider

## Caching Auto-configuration

It searches for the libraries and configuration-files in the classpath and initializes the required dependency beans at the time of application startup. The auto-configuration of caching includes the following steps:

* Add the annotation **@EnableCaching** in the configuration file.
* Add the required **caching libraries** in the classpath.
* In the root of the classpath, add the **configuration file**for the cache provider.

```java
@SpringBootApplication  
@EnableCaching  
public class Employee  
{  
    @Bean  
    public CacheManager cacheManager()  
    {  
    //some code  
    }  
}  
```

When we do not define a bean of type **CacheManager** or **CacheResolver**, the Spring Boot Framework tries to detect the following cache provider:

1. **Generic**
2. **JCache**
3. **EhCache**
4. **Hazelcast**
5. **Infinispan**
6. **Couchbase**
7. **Redis**
8. **Caffeine**
9. **Simple**

