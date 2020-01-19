---
description: Spring AOP enables Aspect-Oriented Programming in spring applications.
---

# Spring AOP

## Overview

1. Aspect Oriented Programming entails breaking down program logic into distinct parts called so-called concerns. In AOP, aspects enable the modularization of concerns. 
2. The functions that span multiple points of an application are called **cross-cutting concerns** and these **cross-cutting concerns** are conceptually separate from the **application's business logic**. There are various common good examples of aspects like logging, auditing, declarative transactions, security, and caching etc. 
3. The key unit of modularity in OOP is the class, whereas in AOP the unit of modularity is the aspect. Dependency Injection helps you decouple your application objects from each other and AOP helps you decouple cross-cutting concerns from the objects that they affect. 
4. AOP is like triggers in programming languages such as Perl, .NET, Java and others. 
5. Spring AOP module provides interceptors to intercept an application, for example, when a method is executed, you can add extra functionality before or after the method execution.

## Core concepts

* **Aspect**: An aspect is a class that implements enterprise application concerns that cut across multiple classes. Aspects can be a normal class configured through Spring XML configuration or we can use Spring AspectJ integration to define a class as Aspect using `@Aspect` annotation.
* **Joinpoints** is a point during the execution of your application. Typical example of joinpoints is a call to a method. Joinpoints define the points in your application at which you can insert additional logic using AOP.
* **Advice** is the code executed at a particular joinpoint. In terms of programming, they are methods that gets executed when a certain join point with matching pointcut is reached in the application. 
* **Pointcut** are expressions that is matched with join points to determine whether advice needs to be executed or not. Pointcut uses different kinds of expressions that are matched with the join points and Spring framework uses the AspectJ pointcut expression language.
* **Target Object**: They are the object on which advices are applied. Spring AOP is implemented using runtime proxies so this object is always a proxied object.
* **AOP proxy**: Spring AOP implementation uses JDK dynamic proxy to create the Proxy classes with target classes and advice invocations, these are called AOP proxy classes.
* **Weaving** is the process of inserting aspects into the application code at the appropriate point. 

## AOP Advice Types

1. **Before Advice**: These advices runs before the execution of join point methods. We can use `@Before` annotation to mark an advice type as Before advice.
2. **After \(finally\) Advice**: An advice that gets executed after the join point method finishes executing, whether normally or by throwing an exception. We can create after advice using `@After` annotation.
3. **After Returning Advice**: these advice methods to execute only if the join point method executes normally. We can use `@AfterReturning` annotation to mark a method as after returning advice.
4. **After Throwing Advice**: This advice gets executed only when join point method throws exception, we can use it to rollback the transaction declaratively. We use `@AfterThrowing` annotation for this type of advice.
5. **Around Advice**: This is the most important and powerful advice. This advice surrounds the join point method and we can also choose whether to execute the join point method or not. We can write advice code that gets executed before and after the execution of the join point method. It is the responsibility of around advice to invoke the join point method and return values if the method is returning something. We use `@Around`annotation to create around advice methods.

## Advantages

AOP provides the way to dynamically add the cross-cutting concern before, after or around the actual logic using simple pluggable configurations.

It makes easy to maintain code in the present and future as well. You can add/remove concerns without recompiling complete source code simply by changing configuration files \(if you are applying aspects suing XML configuration\).

