# Eureka

## Start Eureka Server

Eureka Server is an application that holds the information about all client-service applications. Every Micro service will register into the Eureka server and Eureka server knows all the client applications running on each port and IP address. Eureka Server is also known as Discovery Server.

The @EnableEurekaServer annotation is used to make your Spring Boot application acts as a Eureka Server.

The code for main Spring Boot application class file is as shown below −

```java
package com.tutorialspoint.eurekaserver;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.server.EnableEurekaServer;

@SpringBootApplication
@EnableEurekaServer
public class EurekaserverApplication {
   public static void main(String[] args) {
      SpringApplication.run(EurekaserverApplication.class, args);
   }
}
```

## Register the Spring Boot Micro service

The @EnableEurekaClient annotation makes your Spring Boot application act as a Eureka client.

The main Spring Boot application is as given below −

```java
package com.tutorialspoint.eurekaclient;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.EnableEurekaClient;

@SpringBootApplication
@EnableEurekaClient
public class EurekaclientApplication {
   public static void main(String[] args) {
      SpringApplication.run(EurekaclientApplication.class, args);
   }
}
```

