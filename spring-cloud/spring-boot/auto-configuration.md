---
description: >-
  Spring Boot auto-configuration automatically configures the Spring application
  based on the jar dependencies that we have added.
---

# Auto-configuration

For example, if the H2 database Jar is present in the classpath and we have not configured any beans related to the database manually, the Spring Boot's auto-configuration feature automatically configures it in the project.

When we add the **spring-boot-starter-web** dependency in the project, Spring Boot auto-configuration looks for the Spring MVC is on the classpath. It auto-configures **dispatcherServlet**, a default **error page,** and **web jars**.

Similarly, when we add the **spring-boot-starter-data-jpa** dependency, we see that Spring Boot Auto-configuration, auto-configures a **datasource** and an **Entity Manager**.

## **@EnableAutoConfiguration**

We can enable the auto-configuration feature by using the annotation **@EnableAutoConfiguration**. 

 **@SpringBootApplication = @ComponentScan+@EnableAutoConfiguration+@Configuration**

## Disable Auto-configuration Classes

 We can also disable the specific auto-configuration classes, if we do not want to be applied. We use the **exclude** attribute of the annotation @EnableAutoConfiguration to disable the auto-configuration classes. For example:

```java
import org.springframework.boot.autoconfigure.*;  
import org.springframework.boot.autoconfigure.jdbc.*;  
import org.springframework.context.annotation.*;  
@Configuration(proxyBeanMethods = false)  
@EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class})  
public class MyConfiguration   
{  
}  
```

## Debugging Auto-configuration

We can find more information about auto-configuration by using the following two ways:

### **Turning on debug logging**

We can debug logging by adding a property in the **application.properties** file. Let's implement the debug logging in the above example. Open the **application.properties** file and add the following property:

```java
logging.level.org.springframework: DEBUG  
```

### **Spring Boot Actuator**

We can also debug auto-configuration by using **Actuator** in the project. We will also add in **HAL Browser** to make things easy. It shows the details of all the beans that are auto-configured, and those are not.

