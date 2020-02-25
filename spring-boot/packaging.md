# Packaging

## WAR

**WAR** stands for **Web Archive.** WAR file represents the web application. Web module contains servlet classes, JSP files, HTML files, JavaScripts, etc. are packaged as a JAR file with .**war** extension. It contains a special directory called **WEB-INF**.

WAR is a module that loads into a web container of the Java Application Server. The Java Application Server has **two** containers: **Web Container** and **EJB Container**.

The **Web Container** hosts the web applications based on Servlet API and JSP. The web container requires the web module to be packaged as a WAR file. It is a WAR file special JAR file that contains a **web.xmlv** file in the **WEB-INF** folder.

An **EJB Container** hosts Enterprise Java beans based on EJB API. It requires EJB modules to be packaged as a JAR file. It contains an **ejb-jar.xml** file in the **META-INF** folder.

The advantage of the WAR file is that it can be deployed easily on the client machine in a Web server environment. To execute a WAR file, a Web server or Web container is required. For example, Tomcat, Weblogic, and Websphere.

## JAR

**JAR** stands for **Java Archive.** An EJB \(Enterprise Java Beans\) module that contains bean files \(class files\), a manifest, and EJB deployment descriptor \(XML file\) are packaged as JAR files with the extension .**jar.** It is used by software developers to distribute Java classes and various metadata.

In other words, A file that encapsulates one or more Java classes, a manifest, and descriptor is called JAR file. It is the lowest level of the archive. It is used in J2EE for packaging EJB and client-side Java Applications. It makes the deployment easy.

## EAR

**EAR** stands for **Enterprise Archive.** EAR file represents the enterprise application. The above two files are packaged as a JAR file with the .**ear** extension. It is deployed into the Application Server. It can contain multiple EJB modules \(JAR\) and Web modules \(WAR\). It is a special JAR that contains an **application.xml** file in the **META-INF** folder.

