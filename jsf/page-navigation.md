---
description: >-
  Navigation rules can be defined in JSF configuration file named
  faces-config.xml. They can be defined in managed beans.
---

# Page Navigation

## Auto Navigation in JSF Page

```markup
<h:form>
   <h3>Using JSF outcome</h3>
   <h:commandButton action = "page2" value = "Page2" />
</h:form>
```

## Auto Navigation in Managed Bean

```java
@ManagedBean(name = "navigationController", eager = true)
@RequestScoped

public class NavigationController implements Serializable {
   public String moveToPage1() {
      return "page1";
   }
}
```

```java
<h:form> 
   <h3> Using Managed Bean</h3>  
   <h:commandButton action = "#{navigationController.moveToPage1}" 
   value = "Page1" />; 
</h:form> 
```

## Resolving Navigation Based on from-action

```java
public String processPage1() { 
   return "page"; 
} 
public String processPage2() { 
   return "page"; 
} 
```

 To resolve views, define the following navigation rules in **faces-config.xml**

```markup
<navigation-rule> 
   <from-view-id>home.xhtml</from-view-id> 
   
   <navigation-case> 
      <from-action>#{navigationController.processPage1}</from-action> 
      <from-outcome>page</from-outcome> 
      <to-view-id>page1.jsf</to-view-id> 
   </navigation-case> 
   
   <navigation-case> 
      <from-action>#{navigationController.processPage2}</from-action> 
      <from-outcome>page</from-outcome> 
      <to-view-id>page2.jsf</to-view-id> 
   </navigation-case> 

</navigation-rule> 
```

## Forward vs Redirect

JSF by default performs a server page forward while navigating to another page and the URL of the application does not change.

To enable the page redirection, append **faces-redirect=true** at the end of the view name.

```markup
<h:form>
   <h3>Forward</h3>
   <h:commandButton action = "page1" value = "Page1" />
   <h3>Redirect</h3>
   <h:commandButton action = "page1?faces-redirect = true" value = "Page1" />
</h:form>
```

