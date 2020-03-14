---
description: >-
  JSF stands for Java Server Faces. It is a server-side Java framework for web
  development.
---

# JSF

Best tutorial for JSF: [https://www.tutorialspoint.com/jsf/jsf\_composite\_components.htm](https://www.tutorialspoint.com/jsf/jsf_composite_components.htm)

The JSF API provides components \(inputText, commandButton etc\) and helps to manage their states. It also provides server-side validation, data conversion, defining page navigation, provides extensibility, supports for internationalization, accessibility etc.

The JSF Tag libraries are used to add components on the web pages and connect components with objects on the server. It also contains tag handlers that implements the component tag.

![](../.gitbook/assets/image%20%288%29.png)

## JavaServer Faces Lifecycle

JSF application life cycle consists of six phases which are as follows:

* Restore view phase
* Apply request values phase; process events
* Process validations phase; process events
* Update model values phase; process events
* Invoke application phase; process events
* Render response phase

![](../.gitbook/assets/image%20%2811%29.png)

### 1\) Execute Phase

In execute phase, when first request is made, application view is built or restored. The execute phase is further divided into following subphases.

* Restore View Phase
* Apply Request Values Phase
* Process Validations Phase
* Update Model Values Phase
* Invoke Application Phase
* Render Response Phase

### 2\) Render

In this phase, the requested view is rendered as a response to the client browser. View rendering is a process in which output is generated as HTML or XHTML. So, user can see it at the browser.

The following steps are taken during the render process.

* Application is compiled, when a client makes an initial request for the index.xhtml web page.
* Application executes after compilation and a new component tree is constructed for the application and placed in a FacesContext.
* The component tree is populated with the component and the managed bean property associated with it, represented by the EL expression.
* Based on the component tree. A new view is built.
* The view is rendered to the requesting client as a response.
* The component tree is destroyed automatically.
* On subsequent requests, the component tree is rebuilt, and the saved state is applied.

