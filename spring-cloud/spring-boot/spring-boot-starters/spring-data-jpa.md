# Spring Data JPA

Spring Data is a high-level Spring Source project. Its purpose is to unify and easy access to the different kinds of persistence stores, both relational database systems, and NoSQL data stores.

```markup
<dependency>  
    <groupId>org.springframework.data</groupId>  
    <artifactId>spring-data-jpa</artifactId>  
    <version>2.2.3.RELEASE</version>  
</dependency>  
```

## Spring Data Repository

Spring Data JPA provides **three** repositories are as follows:

* **CrudRepository:** It offers standard **create, read, update,** and **delete** It contains method like **findOne\(\), findAll\(\), save\(\), delete\(\),** etc.
* **PagingAndSortingRepository:** It extends the **CrudRepository** and adds the findAll methods. It allows us to **sort** and **retrieve** the data in a paginated way.
* **JpaRepository:** It is a **JPA specific repository** It is defined in **Spring Data Jpa**. It extends the both repository CrudRepository and PagingAndSortingRepository. It adds the JPA-specific methods, like **flush\(\)** to trigger a flush on the persistence context.

## Spring Boot Starter Data JPA

Spring Boot provides **spring-boot-starter-data-jpa** dependency to connect Spring application with relational database efficiently. The spring-boot-starter-data-jpa internally uses the spring-boot-jpa dependency \(since Spring Boot version 1.5.3\).

```markup
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-data-jpa</artifactId>  
    <version>2.2.2.RELEASE</version>  
</dependency>  
```

JPA allows us to map application classes to table in the database.

* **Entity Manager:** Once we define the mapping, it handles all the interactions with the database.
* **JPQL \(Java Persistence Query Language\):** It provides a way to write queries to execute searches against entities. It is different from the SQL queries. JPQL queries already understand the mapping that is defined between entities. We can add additional conditions if required.
* **Criteria API:** It defines a Java-based API to execute searches against the database.

## Hibernate vs. JPA

Hibernate is the implementation of JPA. It is the most popular ORM framework, while JPA is an API that defines the specification. Hibernate understands the mapping that we add between objects and tables. It ensures that data is retrieved/ stored from the database based on the mapping. It also provides additional features on the top of the JPA.

