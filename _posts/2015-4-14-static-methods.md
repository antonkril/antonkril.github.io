---
layout: post
title: Static Methods
---

Static methods are elements of procedural paradigm: they belong to classes and are not connected with object state anyhow. Classes are just namespaces for static methods.

Since static calls hard-code class names, static methods must not be used for behavior that is supposed to be substituted, extended, or mocked in tests.

Singleton anti-pattern is built on static method, so it has all the problems of static methods.

Constructors are static methods with special form of call (`new <ClassName>` instead of `<ClassName>::__construct`). Because of this, usage of `new` must be discouraged in systems that are supposed to be re-composed or extended by third-party developers.
