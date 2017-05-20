---
layout: post
title: Code reuse
---

When behavior duplication occurs, that behavior should be extracted and reused. Possible behavior extraction directions are following:

![Behavior extraction directions](/images/code-reuse.png)

1. Private method within class. Can only be used if behavior duplication occurs within same class. Easiest option, but prevents customizations.
2. Inheritance. Move duplicated behavior to method in parent class and reuse within all children. Can only be used for behavior reuse within logically connected objects. Has all problems of inheritance: publication of protected api, hard-code of class dependency (limits customizations)
3. Trait. Similar to inheritance, but does not have limitation of logicaly related clients. Also hard-codes dependency on specific trait and prevents customization of reused behavior.
4. Extracted Interface Dependency. Behavior is moved to extracted object. That object can be reused in any client (no logical relation limitation). This approach allows customization and substitution of extracted behavior. Only downside is that new dependency is added to constructor of every client.
5. Facade. Only available when all clients of extracted behavior share facade, and that behavior must be executed for every client.

For code that is supposed to be customized only #4 & #5 should be used.
