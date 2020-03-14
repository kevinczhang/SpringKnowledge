---
description: >-
  Spring Boot JDBC provides starter and libraries for connecting an application
  with JDBC.
---

# Spring Boot JDBC

 In Spring Boot JDBC, the database related beans such as **DataSource, JdbcTemplate,** and **NamedParameterJdbcTemplate** auto-configures and created during the startup. We can autowire these classes if we want to use it. For example:

```java
@Autowired  
JdbcTemplate jdbcTemplate;  
@Autowired  
private NamedParameterJdbcTemplate jdbcTemplate;  
```

 In **application.properties** file, we configure **DataSource** and **connection pooling**. [Spring Boot](https://www.javatpoint.com/spring-boot-tutorial) chooses **tomcat** pooling by default.

## JDBC Connection Pooling

 **JDBC connection pooling** is a mechanism that manages **multiple** database connection requests. In other words, it facilitates connection reuse, a memory cache of database connections, called a **connection pool.** A connection pooling module maintains it as a layer on top of any standard JDBC driver product.

![](../../../.gitbook/assets/image%20%282%29.png)



It increases the speed of data access and reduces the number of database connections for an application. It also improves the performance of an application. Connection pool performs the following tasks:

* Manage available connection
* Allocate new connection
* Close connection

## HikariCP

The default connection pool in Spring Boot 2 is **HikariCP**. It provides enterprise-ready features and better performance. HikariCP is a JDBC DataSource implementation that provides a connection pooling mechanism.

* If the HikariCP is present on the classpath, the Spring Boot automatically configures it.
* If the HikariCP is not found on the classpath, Spring Boot looks for the **Tomcat JDBC Connection Pool.** If it is on the classpath Spring Boot, pick it up.
* If both the above options are not available, Spring Boot chooses **Apache Commons DBCP2** as the JDBC connection pool.

## JDBC vs. Hibernate

| JDBC | Hibernate |
| :--- | :--- |
| JDBC is a **technology**. | Hibernate is an **ORM** framework. |
| In JDBC, the user is responsible for creating and closing the connections. | In Hibernate, the run time system takes care of creating and closing the connections. |
| It does not support lazy loading. | It supports lazy loading that offers better performance. |
| It does not support associations \(the connection between two separate classes\). | It supports associations. |

