# JSP Scripting elements

## JSP scriptlet tag

In JSP, java code can be written inside the jsp page using the scriptlet tag.

```java
<%  
String name=request.getParameter("uname");  
out.print("welcome "+name);  
%> 
```

## JSP expression tag

 The code placed within **JSP expression tag** is _written to the output stream of the response_. So you need not write out.print\(\) to write data. It is mainly used to print the values of variable or method.

```java
Current Time: <%= java.util.Calendar.getInstance().getTime() %>  
```

## JSP Declaration Tag

The **JSP declaration tag** is used _to declare fields and methods_.

The code written inside the jsp declaration tag is placed outside the service\(\) method of auto generated servlet. So it doesn't get memory at each request.

```java
<%! int data=50; %>  
<%= "Value of the variable is:"+data %>  
```



