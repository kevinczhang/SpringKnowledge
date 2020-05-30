# Spring Boot Repository

### Spring Boot CrudRepository

 Spring Boot provides an interface called **CrudRepository** that contains methods for CRUD operations. 

```java
public interface CrudRepository<T,ID> extends Repository<T,ID> 
```

where,

* **T** is the domain type that repository manages.
* **ID** is the type of the id of the entity that repository manages.

```java
public interface StudentRepository extends CrudRepository<Student, Integer>  
{  
} 
```

## Spring Boot JpaRepository

JpaRepository provides JPA related methods such as flushing, persistence context, and deletes a record in a batch.

![](../../../../.gitbook/assets/image%20%289%29.png)

## CrudRepository vs. JpaRepository

| CrudRepository | JpaRepository |
| :--- | :--- |
| CrudRepository does not provide any method for pagination and sorting. | JpaRepository extends PagingAndSortingRepository. It provides all the methods for implementing the pagination. |
| It works as a **marker** interface. | JpaRepository extends both **CrudRepository** and **PagingAndSortingRepository**. |
| It provides CRUD function only. For example **findById\(\), findAll\(\),** etc. | It provides some extra methods along with the method of PagingAndSortingRepository and CrudRepository. For example, **flush\(\), deleteInBatch\(\).** |
| It is used when we do not need the functions provided by JpaRepository and PagingAndSortingRepository. | It is used when we want to implement pagination and sorting functionality in an application. |



