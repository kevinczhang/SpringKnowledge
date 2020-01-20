---
description: >-
  A filter is an object that is invoked at the preprocessing and postprocessing
  of a request.
---

# Servlet Filter

## Filter interface

| Method | Description |
| :--- | :--- |
| public void init\(FilterConfig config\) | init\(\) method is invoked only once. It is used to initialize the filter. |
| public void doFilter\(HttpServletRequest request,HttpServletResponse response, FilterChain chain\) | doFilter\(\) method is invoked every time when user request to any resource, to which the filter is mapped.It is used to perform filtering tasks. |
| public void destroy\(\) | This is invoked only once when filter is taken out of the service. |

## FilterChain interface

The object of FilterChain is responsible to invoke the next filter or resource in the chain.This object is passed in the doFilter method of Filter interface.The FilterChain interface contains only one method:

1. **public void doFilter\(HttpServletRequest request, HttpServletResponse response\):** it passes the control to the next filter or resource.

## FilterConfig

An object of FilterConfig is created by the web container. This object can be used to get the configuration information from the web.xml file.

### Methods of FilterConfig interface

There are following 4 methods in the FilterConfig interface.

1. **public void init\(FilterConfig config\):** init\(\) method is invoked only once it is used to initialize the filter.
2. **public String getInitParameter\(String parameterName\):** Returns the parameter value for the specified parameter name.
3. **public java.util.Enumeration getInitParameterNames\(\):** Returns an enumeration containing all the parameter names.
4. **public ServletContext getServletContext\(\):** Returns the ServletContext object.



