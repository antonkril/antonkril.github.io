---
layout: post
title: Static Methods
---

Static methods are elements of the procedural paradigm: they belong to classes and are not connected with the object state. Classes are just namespaces for static methods.

Since static calls hard-code class names, static methods must not be used for behavior that is supposed to be substituted, extended, or mocked in tests.

Singleton anti-pattern is built on static method, so it has all the problems of static methods.

Another problem with static methods is that they are linked statically in client code (method class is hardcoded in client code) and don't support polymorphic calls.

Constructors are static methods with a special form of call (new <ClassName> instead of <ClassName>::__construct). Because of this, usage of new must be discouraged in systems that are supposed to be re-composed or extended by third-party developers.
