# ServletConfig and ServletContext

## ServletConfig

An object of ServletConfig is created by the web container for each servlet. This object can be used to get configuration information from web.xml file.

#### Methods of ServletConfig interface

1. **public String getInitParameter\(String name\):** Returns the parameter value for the specified parameter name.
2. **public Enumeration getInitParameterNames\(\):** Returns an enumeration of all the initialization parameter names.
3. **public String getServletName\(\):** Returns the name of the servlet.
4. **public ServletContext getServletContext\(\):** Returns an object of ServletContext.

```java
ServletConfig config = getServletConfig();  
```

## ServletContext

An object of ServletContext is created by the web container at time of deploying the project. This object can be used to get configuration information from web.xml file. There is only one ServletContext object per web application.

 If any information is shared to many servlet, it is better to provide it from the web.xml file using the **&lt;context-param&gt;** element.

1. The object of ServletContext provides an interface between the container and servlet.
2. The ServletContext object can be used to get configuration information from the web.xml file.
3. The ServletContext object can be used to set, get or remove attribute from the web.xml file.
4. The ServletContext object can be used to provide inter-application communication.

#### How to get the object of ServletContext interface

1. **getServletContext\(\) method** of ServletConfig interface returns the object of ServletContext.
2. **getServletContext\(\) method** of GenericServlet class returns the object of ServletContext.

```java
//We can get the ServletContext object from ServletConfig object  
ServletContext application = getServletConfig().getServletContext();  
  
//Another convenient way to get the ServletContext object  
ServletContext application = getServletContext();  
```

## Difference between ServletConfig and ServletContext

| The servletconfig object refers to the single servlet whereas servletcontext object refers to the whole web application. |
| :--- |


