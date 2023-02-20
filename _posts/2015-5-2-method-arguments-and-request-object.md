---
layout: post
title: Method Arguments and Request Object
---

In client-server object-oriented programs, every object performs operations on data. The data may come from 2 directions:

  - from client code through method arguments
  - from storage (or service representing storage)

Operation data must not come to the object as a dependency through the class constructor. 

Only the dependency services that help perform operations on the data must be retrieved as constructor dependencies.

Client-server framework Request objects are application arguments. They contain operation data. They must not be requested as dependencies in constructors.
