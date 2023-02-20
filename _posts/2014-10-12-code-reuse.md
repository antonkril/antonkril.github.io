---
layout: post
title: Code reuse
---
It is common wisdom that behavior duplication should be avoided in most cases. The duplicated behavior should be extracted and reused. There are the following behavior extraction approaches available in the object-oriented paradigm:

![Behavior extraction directions](/images/code-reuse.png)

1. Extract to a private method within the class. You can only use this if behavior duplication occurs within one class. It is the easiest option, but it prevents customizations of the extracted code since it is being moved to a private method.
2. Extract to a method in a parent class and reuse in all children. You can only use it within hierarchically linked objects. It has all problems of inheritance: publication of protected class API, static linking (parent class name is hard-coded in child classes), and limited customizability (you can't substitute the extracted behavior in a polymorphic way
3. Extract to a Mixin or a Trait (for PHP). Similar to inheritance, but does not have the limitation of logically related clients. It also has the problem of static linking.
4. Extract to a dependency (Composition). Move the duplicated behavior to a separate object. The object can then be used in any client (no hierarchical relation limitation). This approach allows customization and substitution of the extracted behavior in runtime.
5. Extract to a Facade. Only available when all clients of the extracted behavior share a single facade.

Only #4 & #5 should be used for the application to be extensible.
