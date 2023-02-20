---
layout: post
title: Declarative vs Imperative
---

Imperative code tells the machine what steps to perform to achieve some result.

Declarative code describes the desired result with the expectation that the machine will be able to identify the optimal steps to achieve it.

The declarative approach has numerous benefits:
While imperative code might be easier to understand and write on a micro level, it is hard to sustain in large applications.
If they know the desired outcome, frameworks, tools, and libraries can optimize the steps to achieve a result.
Declarative code is easier to analyze and validate
Declarative code is paralelizable
Declarative code can not have temporal coupling bugs - one of the hardest-to-fix types of bugs.
The declarative customization approach allows for non-conflicting customizations.

Functional programming languages generally follow the declarative approach. SQL, HTML, and XML are declarative.

State mutation makes the declarative approach impossible.

Customizable applications should expose declarative APIs whenever possible.
