---
layout: post
title: Object Initialization
---

In object-oriented applications, objects must be ready for use after being created. Partially initialized objects cause the whole class of hard-to-research bugs.

All kinds of `init*`, `prepare*`, or `load` methods that do object preparation signify partial initialization and should be refactored to atomic initialization.
