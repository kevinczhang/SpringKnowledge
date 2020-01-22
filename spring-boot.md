# Spring Boot

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

