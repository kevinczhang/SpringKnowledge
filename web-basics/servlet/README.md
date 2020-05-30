---
description: >-
  Servlet is the fundamental of creating web app in Java. Other frameworks build
  on servlet.
---

# Servlet

## What is a Servlet?

Servlet can be described in many ways, depending on the context.

* Servlet is a technology which is used to create a web application.
* Servlet is an API that provides many interfaces and classes including documentation.
* Servlet is an interface that must be implemented for creating any Servlet.
* Servlet is a class that extends the capabilities of the servers and responds to the incoming requests. It can respond to any requests.
* Servlet is a web component that is deployed on the server to create a dynamic web page.

The **javax.servlet** package contains many interfaces and classes that are used by the servlet or web container. These are not specific to any protocol.

The **javax.servlet.http** package contains interfaces and classes that are responsible for http requests only.

## Methods of Servlet interface

There are 5 methods in Servlet interface. The init, service and destroy are the life cycle methods of servlet. These are invoked by the web container.

| Method | Description |
| :--- | :--- |
| **public void init\(ServletConfig config\)** | initializes the servlet. It is the life cycle method of servlet and invoked by the web container only once. |
| **public void service\(ServletRequest request,ServletResponse response\)** | provides response for the incoming request. It is invoked at each request by the web container. |
| **public void destroy\(\)** | is invoked only once and indicates that servlet is being destroyed. |
| **public ServletConfig getServletConfig\(\)** | returns the object of ServletConfig. |
| **public String getServletInfo\(\)** | returns information about servlet such as writer, copyright, version etc. |

## Methods of HttpServlet class

There are many methods in HttpServlet class. They are as follows:

1. **public void service\(ServletRequest req,ServletResponse res\)** dispatches the request to the protected service method by converting the request and response object into http type.
2. **protected void service\(HttpServletRequest req, HttpServletResponse res\)** receives the request from the service method, and dispatches the request to the doXXX\(\) method depending on the incoming http request type.
3. **protected void doGet\(HttpServletRequest req, HttpServletResponse res\)** handles the GET request. It is invoked by the web container.
4. **protected void doPost\(HttpServletRequest req, HttpServletResponse res\)** handles the POST request. It is invoked by the web container.
5. **protected void doHead\(HttpServletRequest req, HttpServletResponse res\)** handles the HEAD request. It is invoked by the web container.
6. **protected void doOptions\(HttpServletRequest req, HttpServletResponse res\)** handles the OPTIONS request. It is invoked by the web container.
7. **protected void doPut\(HttpServletRequest req, HttpServletResponse res\)** handles the PUT request. It is invoked by the web container.
8. **protected void doTrace\(HttpServletRequest req, HttpServletResponse res\)** handles the TRACE request. It is invoked by the web container.
9. **protected void doDelete\(HttpServletRequest req, HttpServletResponse res\)** handles the DELETE request. It is invoked by the web container.
10. **protected long getLastModified\(HttpServletRequest req\)** returns the time when HttpServletRequest was last modified since midnight January 1, 1970 GMT.

