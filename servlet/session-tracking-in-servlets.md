# Session Tracking in Servlets

## Session Tracking Techniques

There are four techniques used in Session tracking:

1. **Cookies**
2. **Hidden Form Field**
3. **URL Rewriting**
4. **HttpSession**

## Cookies in Servlet

A **cookie** is a small piece of information that is persisted between the multiple client requests.

A cookie has a name, a single value, and optional attributes such as a comment, path and domain qualifiers, a maximum age, and a version number.

## HttpSession interface

In such case, container creates a session id for each user.The container uses this id to identify the particular user.An object of HttpSession can be used to perform two tasks:

1. bind objects
2. view and manipulate information about a session, such as the session identifier, creation time, and last accessed time.

![](../.gitbook/assets/image%20%284%29.png)

#### How to get the HttpSession object ?

The HttpServletRequest interface provides two methods to get the object of HttpSession:

1. **public HttpSession getSession\(\):**Returns the current session associated with this request, or if the request does not have a session, creates one.
2. **public HttpSession getSession\(boolean create\):**Returns the current HttpSession associated with this request or, if there is no current session and create is true, returns a new session.

#### Commonly used methods of HttpSession interface

1. **public String getId\(\):**Returns a string containing the unique identifier value.
2. **public long getCreationTime\(\):**Returns the time when this session was created, measured in milliseconds since midnight January 1, 1970 GMT.
3. **public long getLastAccessedTime\(\):**Returns the last time the client sent a request associated with this session, as the number of milliseconds since midnight January 1, 1970 GMT.
4. **public void invalidate\(\):**Invalidates this session then unbinds any objects bound to it.

