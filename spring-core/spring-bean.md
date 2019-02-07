# Spring Bean



### Configuration Metadata

1. XML based configuration file.
2. Annotation-based configuration
   * Need to enable it in our Spring configuration file \(&lt;context:annotation-config/&gt;\)
   *  Annotation injection is performed before XML injection. Thus, the latter configuration will override the former for properties wired through both approaches.
   *  @Required annotation applies to bean property setter methods.
   *  @Autowired annotation can apply to bean property setter methods, non-setter methods, constructor and properties.
   *  @Qualifier annotation along with @Autowired can be used to remove the confusion by specifiying which exact bean will be wired.
   *  Spring supports JSR-250 based annotations which include @Resource, @PostConstruct and @PreDestroy annotations.
3. Java-based configuration 
   1.  **@Configuration** indicates that the class can be used by the Spring IoC container as a source of bean definitions.
   2.  `@ComponentScan` annotation is used with `@Configuration` annotation to specify the packages to look for Component classes.
   3.  **@Bean** annotation tells Spring that a method annotated with @Bean will return an object that should be registered as a bean in the Spring application context. @Bean annotation also can be used with parameters like name, initMethod and destroyMethod.
      * name – allows you give name for bean
      * initMethod – allows you to choose method which will be invoked on context register
      * destroyMethod – allows you to choose method which will be invoked on context shutdown
   4.  **@Import** annotation allows for loading @Bean definitions from another configuration class.
   5.  `@PreDestroy` and `@PostConstruct` are alternative way for bean initMethod and destroyMethod. It can be used when the bean class is defined by us. For example;
   6.  `@PropertySource`: provides a simple declarative mechanism for adding a property source to Spring’s Environment. 
   7. `@Service`: Indicates that an annotated class is a “Service”. This annotation serves as a specialization of @Component, allowing for implementation classes to be autodetected through classpath scanning.
   8. `@Repository`: Indicates that an annotated class is a “Repository”. This annotation serves as a specialization of @Component and advisable to use with [DAO](https://www.journaldev.com/16813/dao-design-pattern) classes.
   9. **Lifecycle Callbacks:** 

```java
public class Foo {
   public void init() {
      // initialization logic
   }
   public void cleanup() {
      // destruction logic
   }
}
@Configuration
public class AppConfig {
   @Bean(initMethod = "init", destroyMethod = "cleanup" )
   @Scope("prototype")
   public Foo foo() {
      return new Foo();
   }
}
```

### Bean Scopes

* **singleton:** This scopes the bean definition to a single instance per Spring IoC container \(default\).
* **prototype:** This scopes a single bean definition to have any number of object instances.
* **request:** This scopes a bean definition to an HTTP request. Only valid in the context of a web-aware Spring ApplicationContext.
* **session:** This scopes a bean definition to an HTTP session. Only valid in the context of a web-aware Spring ApplicationContext.
* **global-session:** This scopes a bean definition to a global HTTP session. Only valid in the context of a web-aware Spring ApplicationContext.

