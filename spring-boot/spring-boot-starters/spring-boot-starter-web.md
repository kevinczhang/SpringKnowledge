# Spring Boot Starter Web

Starter of Spring web uses Spring MVC, REST and Tomcat as a default embedded server.

```markup
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-web</artifactId>  
    <version>2.2.2.RELEASE</version>  
</dependency>  
```

 The spring-boot-starter-web transitively depends on the following:

* org.springframework.boot:spring-boot-starter
* org.springframework.boot:spring-boot-starter-tomcat
* org.springframework.boot:spring-boot-starter-validation
* com.fasterxml.jackson.core:jackson-databind
* org.springframework:spring-web
* org.springframework:spring-webmvc

The spring-boot-starter-web auto-configures the following things that are required for the web development:

* Dispatcher Servlet
* Error Page
* Web JARs for managing the static dependencies
* Embedded servlet container

