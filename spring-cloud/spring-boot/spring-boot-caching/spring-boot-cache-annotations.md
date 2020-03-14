# Cache Annotations

## @EnableCaching

It is a class-level annotation. We can enable caching in the Spring Boot application by using the annotation **@EnableCaching.** It is defined in **org.springframework.cache.annotation** package. It is used together with **@Configuration** class.

The auto-configuration enables caching and setup a **CacheManager,** if there is no already defined instance of CacheManager. It scans for a specific provider, and when it does not find, it creates an in-memory cache using concurrent **HashMap.**

```java
@SpringBootApplication  
@EnableCaching   
public class SpringBootCachingApplication   
{  
    public static void main(String[] args)   
    {  
        SpringApplication.run(SpringBootCachingApplication.class, args);  
    }  
}  
```

## @CacheConfig

It is a class-level annotation that provides a common cache-related setting. It tells the Spring where to store cache for the class. When we annotate a class with the annotation, it provides a set of default settings for any cache operation defined in that class. Using the annotation, we need not to declare things multiple times.

```java
@CacheConfig(cacheNames={"employee"})   
public class UserService  
{  
//some code  
} 
```

## @Caching

It is used when we need both annotations **@CachePut** or **@CacheEvict** at the same time on the same method. In other words, it is used when we want to use multiple annotations of the same type.

But **Java does not allow multiple annotations** of the same type to be declared for a given method. To avoid this problem, we use **@Caching** annotation.

```java
@Caching(evict = {@CacheEvict("phone_number"), @CacheEvict(value="directory", 
    key="#student.id") })  
public String getAddress(Student student)   
{  
//some code  
}
```

## @Cacheable

It is a method level annotation. It defines a cache for a method's return value. The Spring Framework manages the requests and responses of the method to the cache that is specified in the annotation attribute. The @Cacheable annotation contains more options. For example, we can provide a **cache name** by using the **value** or **cacheNames** attribute.

We can also specify the **key** attribute of the annotation that uniquely identifies each entry in the cache. If we do not specify the key, Spring uses the default mechanism to create the key.

```java
@Cacheable(value="cacheStudentInfo", key="#id")  
public List studentInfo()  
{  
    //some code   
    return studentDetails;  
} 
```

 We can also apply a condition in the annotation by using the condition attribute. When we apply the condition in the annotation, it is called **conditional caching**.

```java
@Cacheable(value="student", condition="#name.length<20")  
public Student findStudent(String name)  
{  
    //some code  
}  
```

## @CacheEvict

It is a method level annotation. It is used when we want to remove stale or unused data from the cache. It requires one or multiple caches that are affected by the action. We can also specify a key or condition into it. If we want wide cache eviction, the @CacheEvict annotation provides a parameter called **allEntries**. It evicts all entries rather than one entry based on the key.

One important point about @CacheEvict annotation is that it can be used with void methods because the method acts as a trigger. It avoids return values. On the other hand, the annotation @Cacheable requires a return value that adds/updates data in the cache. We can use @CacheEvict annotation in the following ways:

Evict the whole cache:

```java
@CacheEvict(allEntries=true)  
```

Evict an entry by key:

```java
@CacheEvict(key="#student.stud_name")
```

 The following annotated method evicts all the data from the cache **student\_data**.

```java
@CacheEvict(value="student_data", allEntries=true) //removing all entries from the cache  
public String getNames(Student student)   
{  
//some code  
}
```

## @CachePut

It is a method level annotation. It is used when we want to **update** the cache without interfering the method execution. It means the method will always execute, and its result will be placed into the cache. It supports the attributes of @Cacheable annotation.

A point to be noticed that the annotations @Cacheable and @CachePut are not the same because they have different behavior. There is a slight difference between @Cacheable and @CachePut annotation is that the @**Cacheable** annotation **skips the method execution** while the **@CachePut** annotation **runs the method** and put the result into the cache.

```java
@CachePut(cacheNames="employee", key="#id") //updating cache  
public Employee updateEmp(ID id, EmployeeData data)  
{  
//some code  
}
```

## Spring Boot Cache Dependency

```java
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-cache</artifactId>  
</dependency>   
```

