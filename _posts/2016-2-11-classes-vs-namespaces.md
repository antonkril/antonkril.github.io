---
layout: post
title: Classes VS Namespaces
---

Many PHP frameworks use classes as namespances for functions. The most widespread example is Controller classes:

```php
<?php

class UserController
{
  public function viewAction()
  {
    // Show user
  }
  
  public function removeAction()
  {
    // Remove user
  }
}
```

Acthion methods in such class are not related:

* they don't share state
* they represent alternative scenarios, and will not be called together in one scenario (single HTTP Request).

If there is need to group such functions, namespaces should be used:

```php
<?php
namespace User;

function view()
{
  // View user
}

function remove()
{
  // Remove user
}
```

If you need to represent operations, but, for some reason, only objects are allowed, classes with one method (commands) can be used:

```php
<?php 
namespace User;

class View
{
  public function __invoke() // or execute()
  {
  }
}

class Remove
{
  public function __invoke()
  {
  }
}

```
