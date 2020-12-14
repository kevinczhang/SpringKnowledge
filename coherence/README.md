# Coherence

At the core of Coherence is the concept of _clustered data management_. This implies the following goals:

* A fully coherent, single system image \(SSI\)
* Scalability for both read and write access
* Fast, transparent failover and failback
* Linear scalability for storage and processing
* No Single-Points-of-Failure \(SPOFs\)
* Cluster-wide locking and transactions

Built on top of this foundation are the various services that Coherence provides, including database caching, HTTP session management, grid agent invocation and distributed queries. 

Coherence is organized as set of services. At the root is the Cluster service. A cluster is defined as a set of Coherence instances \(one instance per JVM, with one or more JVMs on each computer\).

## **C**ache types

### Distributed Caches

A distributed, or partitioned, cache is a clustered, fault-tolerant cache that has linear scalability. Data is partitioned among all storage members of the cluster. For fault-tolerance, partitioned caches can be configured to keep each piece of data on one or more unique computers within a cluster. Distributed caches are the most commonly used caches in Coherence.

#### Get and put operations:

![Get Operations in a Distributed Cache](../.gitbook/assets/image%20%2820%29.png)

![Put Operations in a distributed Cache Environment](../.gitbook/assets/image%20%2821%29.png)

![Failover in a Distributed Cache](../.gitbook/assets/image%20%2814%29.png)

![Local Storage in a Distributed Cache](../.gitbook/assets/image%20%2823%29.png)

### Replicated Caches

A replicated cache is a clustered, fault tolerant cache where data is fully replicated to every member in the cluster.

![Get Operation in a Replicated Cache](../.gitbook/assets/image%20%2815%29.png)

![Put Operation in a Replicated Cache](../.gitbook/assets/image%20%2825%29.png)

### Optimistic Caches

An optimistic cache is a clustered cache implementation similar to the replicated cache implementation but without any concurrency control.This implementation offers higher write throughput than a replicated cache. It also allows an alternative underlying store for the cached data \(for example, a MRU/MFU-based cache\). However, if two cluster members are independently pruning or purging the underlying local stores, the stored content held by each member may be different.

### Near Caches

A near cache is a hybrid cache; it typically fronts a distributed cache or a remote cache with a local cache.Near cache invalidates front cache entries, using a configured invalidation strategy, and provides excellent performance and synchronization. Near cache backed by a partitioned cache offers zero-millisecond local access for repeat data access, while enabling concurrency and ensuring coherency and fail over, effectively combining the best attributes of replicated and partitioned caches.

![Put Operations in a Near Cache](../.gitbook/assets/image%20%2824%29.png)

![Get Operations in a Near Cache](../.gitbook/assets/image%20%2822%29.png)

### View Caches

A view cache is a clustered, fault tolerant cache that provides a local in-memory materialized view of data stored in a distributed and partitioned cache.

![Put Operations in a View Cache](../.gitbook/assets/image%20%2817%29.png)

### Local Caches

While it is not a clustered service, the local cache implementation is often used in combination with various clustered cache services as part of a near cache.

### Remote Caches

A remote cache describes any out-of-process cache accessed by a Coherence\*Extend client.All cache requests are sent to a Coherence proxy where they are delegated to a cache \(Replicated, Optimistic, Partitioned\). See [Overview of Coherence\*Extend](https://docs.oracle.com/pls/topic/lookup?ctx=en/middleware/standalone/coherence/14.1.1.0/develop-applications&id=COHCG5038) in Developing Remote Clients for Oracle Coherence.  


