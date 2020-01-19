---
description: Spring Framework is one of the most popular Java EE framework.
---

# Spring framework

## Spring Framework Architecture

Spring Framework is divided into a number of separate modules. Core, Web and Data Access are the most important modules. There are some other Miscellaneous modules.

![Spring Framework Architecture](../.gitbook/assets/image.png)

## Core Components

The Core container from Spring consists of four modules: SpEL , Context, Core, Beans.

1. The SpEL module provides a powerful expression language for manipulating objects during execution.
2. Context is built on the basis of Beans and Core and allows you to access any object that is defined in the settings. The key element of the Context module is the ApplicationContext interface.
3. The Core module provides key parts of the framework including IoC and DI properties.
4. The Bean module is responsible for creating and managing [Spring Beans](https://www.journaldev.com/2637/spring-bean-life-cycle) – is application context structure unit.

## Spring Framework Web

Spring framework Web layer consists of Web, Web-MVC, Web-Socket, Web-Portlet .

1. The Web module provides functions such as downloading files, creating web application, rest web service etc.
2. Web-MVC contains a [Spring MVC](https://www.journaldev.com/14476/spring-mvc-example) implementation for web applications.
3. Web-Socket provides support for communication between the client and the server, using Web-Sockets in web applications.
4. Web-Portlet provides MVC implementation with portlet environment.

## Spring Framework Data Access

The Data Access/Integration container consists of JDBC, ORM, OXM, JMS and the Transactions module.

1. JDBC provides an abstract layer of JDBC and eliminates the need for the developer to manually register the monotonous code associated with connecting to the database.
2. [Spring ORM](https://www.journaldev.com/7655/spring-orm-example-jpa-hibernate-transaction) provides integration with such popular ORMs as Hibernate, JDO, JPA, etc.
3. The OXM module is responsible for linking the Object / XML – XMLBeans, JAXB, etc.
4. The JMS \(Java Messaging Service\) module is responsible for creating, sending and receiving messages.
5. Transactions supports transaction management for classes that implement certain methods and POJOs.

## Spring Framework Miscellaneous Modules

Spring also includes a number of other important modules, such as AOP, Aspects, Instrumentation, Messaging and Test.

1. AOP implements aspect-oriented programming and allows using the entire arsenal of AOP capabilities.
2. The Aspects module provides integration with AspectJ, which is also a powerful AOP framework.
3. Instrumentation is responsible for supporting class instrumentation and class loader, which are used in server applications.
4. The Messaging module provides STOMP support.
5. Finally, the Test module provides testing using TestNG or the JUnit Framework.

