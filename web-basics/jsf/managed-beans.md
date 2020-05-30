# Managed Beans

Managed Bean is a regular Java Bean class registered with JSF. In other words, Managed Beans is a Java bean managed by JSF framework. Managed bean contains the getter and setter methods, business logic, or even a backing bean \(a bean contains all the HTML form value\).

```java
@ManagedBean(name = "helloWorld", eager = true)
@RequestScoped
public class HelloWorld {
   @ManagedProperty(value = "#{message}")
   private Message message;
   ...
}
```

## @ManagedBean Annotation

**@ManagedBean** marks a bean to be a managed bean with the name specified in name attribute. If the name attribute is not specified, then the managed bean name will default to class name portion of the fully qualified class name. In our case, it would be helloWorld.

Another important attribute is **eager**. If eager = "true" then managed bean is created before it is requested for the first time otherwise "lazy" initialization is used in which bean will be created only when it is requested.

## Scope Annotations

Scope annotations set the scope into which the managed bean will be placed. If the scope is not specified, then bean will default to request scope. Each scope is briefly discussed in the following table.

<table>
  <thead>
    <tr>
      <th style="text-align:left">S.No</th>
      <th style="text-align:left">Scope &amp; Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p><b>@RequestScoped</b>
        </p>
        <p>Bean lives as long as the HTTP request-response lives. It gets created
          upon a HTTP request and gets destroyed when the HTTP response associated
          with the HTTP request is finished.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">
        <p><b>@NoneScoped</b>
        </p>
        <p>Bean lives as long as a single EL evaluation. It gets created upon an
          EL evaluation and gets destroyed immediately after the EL evaluation.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">
        <p><b>@ViewScoped</b>
        </p>
        <p>Bean lives as long as the user is interacting with the same JSF view in
          the browser window/tab. It gets created upon a HTTP request and gets destroyed
          once the user postbacks to a different view.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">
        <p><b>@SessionScoped</b>
        </p>
        <p>Bean lives as long as the HTTP session lives. It gets created upon the
          first HTTP request involving this bean in the session and gets destroyed
          when the HTTP session is invalidated.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">
        <p><b>@ApplicationScoped</b>
        </p>
        <p>Bean lives as long as the web application lives. It gets created upon
          the first HTTP request involving this bean in the application (or when
          the web application starts up and the eager=true attribute is set in @ManagedBean)
          and gets destroyed when the web application shuts down.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">
        <p><b>@CustomScoped</b>
        </p>
        <p>Bean lives as long as the bean&apos;s entry in the custom Map, which is
          created for this scope lives.</p>
      </td>
    </tr>
  </tbody>
</table>

## @ManagedProperty Annotation

 JSF is a simple static Dependency Injection \(DI\) framework. Using **@ManagedProperty** annotation, a managed bean's property can be injected in another managed bean.

{% code title="HelloWorld.java" %}
```java
package com.tutorialspoint.test;

import javax.faces.bean.ManagedBean;
import javax.faces.bean.ManagedProperty;
import javax.faces.bean.RequestScoped;

@ManagedBean(name = "helloWorld", eager = true)
@RequestScoped
public class HelloWorld {
   @ManagedProperty(value = "#{message}")
   private Message messageBean;
   private String message;
   
   public HelloWorld() {
      System.out.println("HelloWorld started!");   
   }
   
   public String getMessage() {
      
      if(messageBean != null) {
         message = messageBean.getMessage();
      }       
      return message;
   }
   
   public void setMessageBean(Message message) {
      this.messageBean = message;
   }
}
```
{% endcode %}

{% code title="Message.java" %}
```java
package com.tutorialspoint.test;

import javax.faces.bean.ManagedBean;
import javax.faces.bean.RequestScoped;

@ManagedBean(name = "message", eager = true)
@RequestScoped
public class Message {
   private String message = "Hello World!";
	
   public String getMessage() {
      return message;
   }
   public void setMessage(String message) {
      this.message = message;
   }
}
```
{% endcode %}

