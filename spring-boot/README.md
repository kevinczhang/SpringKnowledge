---
description: >-
  Spring module that provides the RAD (Rapid Application Development) feature to
  the Spring Framework
---

# Spring Boot

Each release of Spring Boot provides a **curated list of dependencies that it supports**. In practice, you do **not need to provide a version for any of these dependencies** in your build configuration, as Spring Boot manages that for you. When you upgrade Spring Boot itself, these dependencies are upgraded as well in a consistent way.

![](../.gitbook/assets/image%20%286%29.png)

In Spring Boot, there is no requirement for XML configuration \(deployment descriptor\). It uses convention over configuration software design paradigm that means it decreases the effort of the developer.

### @SpringBootApplication Annotation <a id="using-boot-using-springbootapplication-annotation"></a>

```java
// same as @Configuration @EnableAutoConfiguration @ComponentScan
@SpringBootApplication
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }

}
```

* `@EnableAutoConfiguration`: enable [Spring Boot’s auto-configuration mechanism](https://docs.spring.io/spring-boot/docs/2.2.4.RELEASE/reference/html/using-spring-boot.html#using-boot-auto-configuration)
* `@ComponentScan`: enable `@Component` scan on the package where the application is located \(see [the best practices](https://docs.spring.io/spring-boot/docs/2.2.4.RELEASE/reference/html/using-spring-boot.html#using-boot-structuring-your-code)\)
* `@Configuration`: allow to register extra beans in the context or import additional configuration classes

## **Why Spring Boot ?**

* The dependency injection approach is used in Spring Boot.
* It contains powerful database transaction management capabilities.
* It simplifies integration with other Java frameworks like JPA/Hibernate ORM, Struts, etc.
* It reduces the cost and development time of the application.

## Advantages of Spring Boot

* It creates **stand-alone** Spring applications that can be started using Java **-jar**.
* It tests web applications easily with the help of different **Embedded** HTTP servers such as **Tomcat, Jetty,** etc. We don't need to deploy WAR files.
* It provides opinionated '**starter**' POMs to simplify our Maven configuration.
* It provides **production-ready** features such as **metrics, health checks,** and **externalized configuration**.
* There is no requirement for **XML** configuration.
* It offers a **CLI** tool for developing and testing the Spring Boot application.
* It offers the number of **plug-ins**.
* It also minimizes writing multiple **boilerplate codes** \(the code that has to be included in many places with little or no alteration\), XML configuration, and annotations.
* It **increases productivity** and reduces development time.

### **Inheriting the Starter Parent**

 To configure your project to inherit from the `spring-boot-starter-parent`, set the `parent` as follows:

```java
<!-- Inherit defaults from Spring Boot -->
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.2.4.RELEASE</version>
</parent>
```



