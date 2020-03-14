---
description: JSP technology is used to create web application just like Servlet technology.
---

# JSP

JSP can be thought of as an extension to Servlet because it provides more functionality than servlet such as expression language, JSTL, etc. A JSP page consists of HTML tags and JSP tags.

## The Lifecycle of a JSP Page

The JSP pages follow these phases:

* Translation of JSP Page
* Compilation of JSP Page
* Classloading \(the classloader loads class file\)
* Instantiation \(Object of the Generated Servlet is created\).
* Initialization \( the container invokes jspInit\(\) method\).
* Request processing \( the container invokes \_jspService\(\) method\).
* Destroy \( the container invokes jspDestroy\(\) method\).

![](../.gitbook/assets/image%20%285%29.png)

## The Directory structure of JSP

![](../.gitbook/assets/image%20%2817%29.png)



