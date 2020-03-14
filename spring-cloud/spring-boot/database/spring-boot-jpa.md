---
description: >-
  Spring Boot JPA is a Java specification for managing relational data in Java
  applications.
---

# Spring Boot JPA

 It allows us to access and persist data between Java object/ class and relational database. JPA follows **Object-Relation Mapping** \(ORM\). It is a set of interfaces. It also provides a runtime **EntityManager** API for processing queries and transactions on the objects against the database. It uses a platform-independent object-oriented query language JPQL \(Java Persistent Query Language\).

JPA is simpler, cleaner, and less labor-intensive than JDBC, SQL, and hand-written mapping. JPA is suitable for **non-performance oriented** complex applications.

 There are some popular JPA implementations frameworks such as **Hibernate, EclipseLink, DataNucleus,** etc. It is also known as **Object-Relation Mapping** \(ORM\) tool.

## JPA Architecture

* **Persistence:** It is a class that contains static methods to obtain an EntityManagerFactory instance.
* **EntityManagerFactory:** It is a factory class of EntityManager. It creates and manages multiple instances of EntityManager.
* **EntityManager:** It is an interface. It controls the persistence operations on objects. It works for the Query instance.
* **Entity:** The entities are the persistence objects stores as a record in the database.
* **Persistence Unit:** It defines a set of all entity classes. In an application, EntityManager instances manage it. The set of entity classes represents the data contained within a single data store.
* **EntityTransaction:** It has a **one-to-one** relationship with the EntityManager class. For each EntityManager, operations are maintained by EntityTransaction class.
* **Query:** It is an interface that is implemented by each JPA vendor to obtain relation objects that meet the criteria.

![](../../../.gitbook/assets/image%20%2817%29.png)

### JPA Class Relationships

![](../../../.gitbook/assets/image%20%289%29.png)



