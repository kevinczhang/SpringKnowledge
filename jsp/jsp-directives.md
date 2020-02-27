# JSP directives

## JSP page directive

 The **jsp directives** are messages that tells the web container how to translate a JSP page into the corresponding servlet.

```java
<%@ page attribute="value" %> 
```

#### Attributes of JSP page directive

* import
* contentType
* extends
* info
* buffer
* language
* isELIgnored
* isThreadSafe
* autoFlush
* session
* pageEncoding
* errorPage
* isErrorPage

## JSP Include Directive

The include directive is used to include the contents of any resource it may be jsp file, html file or text file. The include directive includes the original content of the included resource at page translation time \(the jsp page is translated only once so it will be better to include static resource\).

```java
<%@ include file="resourceName" %>  
```

## JSP Taglib directive

The JSP taglib directive is used to define a tag library that defines many tags. We use the TLD \(Tag Library Descriptor\) file to define the tags.

```java
<%@ taglib uri="http://www.javatpoint.com/tags" prefix="mytag" %> 
```

