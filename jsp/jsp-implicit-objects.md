---
description: >-
  These objects are created by the web container that are available to all the
  jsp pages.
---

# JSP Implicit Objects



| Object | Type |
| :--- | :--- |
| out | JspWriter |
| request | HttpServletRequest |
| response | HttpServletResponse |
| config | ServletConfig |
| application | ServletContext |
| session | HttpSession |
| pageContext | PageContext |
| page | Object |
| exception | Throwable |

```java
<%   
String name=request.getParameter("uname");  
out.print("welcome "+name);  
response.sendRedirect("http://www.google.com");  
String driver=config.getInitParameter("dname");  
String driver=application.getInitParameter("dname");  
session.setAttribute("user",name);  
pageContext.setAttribute("user",name,PageContext.SESSION_SCOPE);  
%>   
```

