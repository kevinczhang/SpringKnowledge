---
description: DevTools stands for Developer Tool.
---

# Spring Boot DevTools

The aim of the module is to try and improve the development time while working with the Spring Boot application. Spring Boot DevTools pick up the changes and restart the application.

```markup
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-devtools</artifactId>  
    <scope>runtime<scope>  
</dependency>  
```

## Features

Spring Boot DevTools provides the following features:

### **Property Defaults**

Spring Boot provides templating technology **Thymeleaf** that contains the property **spring.thymeleaf.cache.** It disables the caching and allows us to update pages without the need of restarting the application. 

### **Automatic Restart**

Auto-restart means reloading of Java classes and configure it at the server-side. After the server-side changes, it deployed dynamically, server restarts happen, and load the modified code. It is mostly used in microservice-based applications. Spring Boot uses **two** types of ClassLoaders:

* The classes that do not change \(third-Jars\) are loaded in the **base ClassLoader.**
* The classes that we are actively developing are loaded in the **restart ClassLoader.**

When the application restarts, the restart ClassLoader is thrown away, and a new one is populated. Therefore, the base ClassLoader is always available and populated.

We can disable the auto-restart of a server by using the property **spring.devtools.restart.enabled** to **false.**

### **LiveReload**

The Spring Boot DevTools module includes an embedded server called **LiveReload.** It allows the application to automictically trigger a browser refresh whenever we make changes in the resources. It is also known as **auto-refresh.**

**Note:** We can disable the LiveReload by setting the property **spring.devtools.livereload.enabled** to **false.**

It provides browser extensions for Chrome, Firefox, and Safari. By default, LiveReload is enabled. The LiveReload works on the following path:

* /META-INF/maven
* /META-INF/resources
* /resources
* /static
* /public
* /templates

### **Remote Debug Tunneling**

Spring Boot can tunnel JDWP \(Java Debug Wire Protocol\) over HTTP directly to the application. It can even work application deployment to Internet Cloud providers that only expose port 80 and 443.

### **Remote Update and Restart**

There is another trick that DevTools offers is: it supports remote application **updates** and **restarts.** It monitors local classpath for file changes and pushes them to a remote server, which is then restarted. We can also use this feature in combination with LiveReload.

