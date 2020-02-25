---
description: Spring Boot Actuator is a sub-project of the Spring Boot Framework.
---

# Spring Boot Starter Actuator

It includes a number of additional features that help us to monitor and manage the Spring Boot application. It contains the actuator endpoints \(the place where the resources live\). We can use **HTTP** and **JMX** endpoints to manage and monitor the Spring Boot application.

```markup
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-actuator</artifactId>  
    <version>2.2.2.RELEASE</version>  
</dependency>
```

## Spring Boot Actuator Features

###  **Endpoints**

The actuator endpoints allows us to monitor and interact with the application. Spring Boot provides a number of built-in endpoints. We can also create our own endpoint. 

| Id | Usage | Default |
| :--- | :--- | :--- |
| actuator | It provides a hypermedia-based **discovery page** for the other endpoints. It requires Spring HATEOAS to be on the classpath. | True |
| auditevents | It exposes audit events information for the current application. | True |
| autoconfig | It is used to display an auto-configuration report showing all auto-configuration candidates and the reason why they 'were' or 'were not' applied. | True |
| beans | It is used to display a complete list of all the Spring beans in your application. | True |
| configprops | It is used to display a collated list of all @ConfigurationProperties. | True |
| dump | It is used to perform a thread dump. | True |
| env | It is used to expose properties from Spring's ConfigurableEnvironment. | True |
| flyway | It is used to show any Flyway database migrations that have been applied. | True |
| health | It is used to show application health information. | False |
| info | It is used to display arbitrary application info. | False |
| loggers | It is used to show and modify the configuration of loggers in the application. | True |
| liquibase | It is used to show any Liquibase database migrations that have been applied. | True |
| metrics | It is used to show metrics information for the current application. | True |
| mappings | It is used to display a collated list of all @RequestMapping paths. | True |
| shutdown | It is used to allow the application to be gracefully shutdown. | True |
| trace | It is used to display trace information. | True |

For Spring MVC, the following additional endpoints are used.

| Id | Description | Default |
| :--- | :--- | :--- |
| docs | It is used to display documentation, including example requests and responses for the Actuator's endpoints. | False |
| heapdump | It is used to return a GZip compressed hprof heap dump file. | True |
| jolokia | It is used to expose JMX beans over HTTP \(when Jolokia is on the classpath\). | True |
| logfile | It is used to return the contents of the logfile. | True |
| prometheus | It is used to expose metrics in a format that can be scraped by a prometheus server. It requires a dependency on micrometer-registry- prometheus. | True |

###  **Metrics** 

Spring Boot Actuator provides dimensional metrics by integrating with the **micrometer**. The micrometer is integrated into Spring Boot. It is the instrumentation library powering the delivery of application metrics from Spring. It provides vendor-neutral interfaces for **timers, gauges, counters, distribution summaries,** and **long task timers** with a dimensional data model.

###  **Audit**

Spring Boot provides a flexible audit framework that publishes events to an **AuditEventRepository.** It automatically publishes the authentication events if spring-security is in execution.

## Spring Boot actuator properties

 Spring Boot enables security for all actuator endpoints. It uses **form-based** authentication that provides **user Id** as the user and a randomly generated **password**. We can also access actuator-restricted endpoints by customizing basicauth security to the endpoints. We need to override this configuration by **management.security.roles** property. For example:

```markup
management.security.enabled=true  
management.security.roles=ADMIN  
security.basic.enabled=true  
security.user.name=admin  
security.user.passowrd=admin  
```

