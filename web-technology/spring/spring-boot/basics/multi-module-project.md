---
description: >-
  A Spring Boot project that contains nested maven projects is called the
  multi-module project.
---

# Multi-Module Project

 In the multi-module project, the parent project works as a container for base maven configurations.  In other words, a **multi-module project** is built from a parent pom that manages a group of submodules. Or A **multi-module project** is defined by a parent POM referencing one or more submodules.  The **pom.xml** file of the parent project consists the list of all **modules, common dependencies,** and **properties** that are inherited by the child projects.

## Why we need multi-module project

Splitting the project into multiple modules is useful and easy to maintain. We can also easily edit or remove modules in the project without affecting the other modules. It is useful when we required to deploy modules individually.

### Maven child projects/ modules

* The child modules are independent maven projects that share properties from the parent project.
* All child projects can be built with a single command because it is inside a parent project.
* It is easier to define the relationship between the projects.



