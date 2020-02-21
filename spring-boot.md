# Spring Boot

Spring Boot makes it easy to create stand-alone, production-grade Spring-based Applications that you can run. We take an opinionated view of the Spring platform and third-party libraries, so that you can get started with minimum fuss. Most Spring Boot applications need very little Spring configuration.

Each release of Spring Boot provides a curated list of dependencies that it supports. In practice, you do not need to provide a version for any of these dependencies in your build configuration, as Spring Boot manages that for you. When you upgrade Spring Boot itself, these dependencies are upgraded as well in a consistent way.

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

## Maven

**Inheriting the Starter Parent**

 To configure your project to inherit from the `spring-boot-starter-parent`, set the `parent` as follows:

```java
<!-- Inherit defaults from Spring Boot -->
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.2.4.RELEASE</version>
</parent>
```



