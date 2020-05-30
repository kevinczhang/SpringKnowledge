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

#### Distributed Caches <a id="COHDG-GUID-3C6188BB-8549-41DA-B520-97DD707DDD44"></a>

A distributed, or partitioned, cache is a clustered, fault-tolerant cache that has linear scalability.Data is partitioned among all storage members of the cluster. For fault-tolerance, partitioned caches can be configured to keep each piece of data on one or more unique computers within a cluster. Distributed caches are the most commonly used caches in Coherence.

#### Get and put operations:

![Get Operations in a Distributed Cache](.gitbook/assets/image%20%2815%29.png)

![Put Operations in a distributed Cache Environment](.gitbook/assets/image%20%2817%29.png)

![Failover in a Distributed Cache](.gitbook/assets/image%20%2814%29.png)

![Local Storage in a Distributed Cache](.gitbook/assets/image%20%2820%29.png)



