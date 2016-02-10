---
layout: post
title: Method Arguments and Request Object
---

In Object Oriented programs, every object performs operations on some data. Operation arguments might modify flow of operation. Data may come from 2 directions:

  - from calling code through method arguments
  - from storage (or service representing storage)

Operation data must not come to object through constructor. 

All services that help perform operations must be retrieved in constructor.

In web frameworks, Request Objects are application arguments. They contain operation data and arguments. They must not be requested in constructors.
