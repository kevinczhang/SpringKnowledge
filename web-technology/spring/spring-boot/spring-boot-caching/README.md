---
description: >-
  In Spring, the cache abstraction is a mechanism that allows consistent use of
  various caching methods with minimal impact on t
---

# Spring Boot Caching

## Cache Abstraction

The main objective of using cache abstraction is to **reduce** the number of executions based on the information present in the cache. It applies to expensive methods such as **CPU** or **IO bound.**

The developers take care of two things while working with cache abstractions.

* **Cache Declaration:** It identifies the methods that need to be cached.
* **Cache Configuration:** The backing cache where the data is stored and read from.

## Types of Caching

There are **four** types of caching are as follows:

* In-memory Caching
* Database Caching
* Web server Caching
* CDN Caching

#### In-memory Caching

In-memory caching increases the performance of the application. It is the area that is frequently used. [**Memcached**](https://www.javatpoint.com/memcached-tutorial) and **Redis** are examples of in-memory caching. It stores key-value between application and database. Redis is an **in-memory, distributed,** and advanced caching tool that allows backup and restore facility. We can manage cache in distributed clusters, also.

#### Database Caching

Database caching is a mechanism that generates web pages on-demand \(dynamically\) by fetching the data from the database. It is used in a **multi-tier** environment that involved clients, web-application server, and database. It improves **scalability** and **performance** by distributing a query workload. The most popular database caching is the first level cache of [Hibernate](https://www.javatpoint.com/hibernate-tutorial).

#### Web Server Caching

Web server caching is a mechanism that stores data for **reuse**. For example, a copy of a web page served by a web server. It is cached for the first time when a user visits the page. If the user requests the same next time, the cache serves a copy of the page. It avoids server form getting overloaded. Web server caching enhances the page delivery speed and reduces the work to be done by the backend server.

#### CDN Caching

The **CDN** stands for **Content Delivery Network**. It is a component used in modern web applications. It improves the delivery of the content by **replicating** commonly requested files \(such as [HTML](https://www.javatpoint.com/html-tutorial) Pages, stylesheet, [JavaScript](https://www.javatpoint.com/javascript-tutorial), images, videos, etc.\) across a globally distributed set of **caching servers.**

It is the reason CDN becomes more popular. The CDN reduces the load on an application origin and improves the user experience. It delivers a local copy of the content from a nearby **cache edge** \(a cache server that is closer to the end-user\), or a **Point of Presence \(PoP\)**.

## Cache vs. Buffer

| Cache | Buffer |
| :--- | :--- |
| The cache is based on **Least Recently Used**. | Buffer is based on **First-In-First-Out.** |
| It is the size of the page cache. | It is an in-memory raw block I/O buffer. |
| It lived for a **long** period. | It lived for a **short** period. |
| We **read** from the cache. | We **write** into the buffer. |
| It stores the **actual** file data. | It stores the file **metadata**. |
| It improves **read** performance. | It improves **write** performance. |

### 

