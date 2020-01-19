# Steps to create a servlet

## 1. Create a directory structures

It defines that where to put the different types of files so that web container may get the information and respond to the client.

![](../.gitbook/assets/image%20%285%29.png)

## 2. Create a Servlet

 There are three ways to create the servlet.

1. By implementing the Servlet interface
2. By inheriting the GenericServlet class
3. By inheriting the HttpServlet class

The HttpServlet class is widely used to create the servlet because it provides methods to handle http requests such as doGet\(\), doPost, doHead\(\) etc.

## 3. Compile the servlet

For compiling the Servlet, jar file is required to be loaded. Different Servers provide different jar files:

| Jar file | Server |
| :--- | :--- |
| 1\) servlet-api.jar | Apache Tomcat |
| 2\) weblogic.jar | Weblogic |
| 3\) javaee.jar | Glassfish |
| 4\) javaee.jar | JBoss |

#### Two ways to load the jar file

1. set classpath
2. paste the jar file in JRE/lib/ext folder

Put the java file in any folder. After compiling the java file, paste the class file of servlet in **WEB-INF/classes** directory.

## 4. Create the deployment descriptor

 The **deployment descriptor** is an xml file, from which Web Container gets the information about the servet to be invoked.

```markup
<web-app>  
  
  <servlet>  
    <servlet-name>sonoojaiswal</servlet-name>  
    <servlet-class>DemoServlet</servlet-class>  
  </servlet>  
  
  <servlet-mapping>  
    <servlet-name>sonoojaiswal</servlet-name>  
    <url-pattern>/welcome</url-pattern>  
  </servlet-mapping>  
  
</web-app>  
```



