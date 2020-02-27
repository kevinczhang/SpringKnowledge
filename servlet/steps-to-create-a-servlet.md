# Steps to create a servlet

## 1. Create a directory structures

It defines that where to put the different types of files so that web container may get the information and respond to the client.

![](../.gitbook/assets/image%20%2811%29.png)

### War File

 A **war \(web archive\) File** contains files of a web project. It may have servlet, xml, jsp, image, html, css, js etc. files. 

```markup
jar -cvf projectname.war *  
```

Here, **-c** is used to create file, **-v** to generate the verbose output and **-f** to specify the arhive file name.

The **\* \(asterisk\) symbol** signifies that all the files of this directory \(including sub directory\).

 To extract the war file, you need to use **-x switch** of **jar tool** of JDK. Let's see the command to extract the war file.

```bash
jar -xvf projectname.war  
```

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

### load on startup in web.xml

The **load-on-startup** element of **web-app** loads the servlet at the time of deployment or server start if value is positive. It is also known as **pre initialization of servlet**.

You can pass positive and negative value for the servlet. 

* If you pass the positive value, the lower integer value servlet will be loaded before the higher integer value servlet. In other words, container loads the servlets in ascending integer value. The 0 value will be loaded first then 1, 2, 3 and so on.
* If you pass the negative value, servlet will be loaded at request time, at first request.

**Advantage of load-on-startup element**

As you know well, servlet is loaded at first request. That means it consumes more time at first request. If you specify the load-on-startup in web.xml, servlet will be loaded at project deployment time or server start. So, it will take **less time** for responding to first request.

