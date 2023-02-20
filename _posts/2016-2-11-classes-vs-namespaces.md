---
layout: post
title: Classes VS Namespaces
---

Many PHP frameworks use classes as namespaces for functions. The most widespread example is the Controller class:

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

Action methods in this class are not related:

* they don't share state
* they represent alternative scenarios and will not be called together in one scenario (single HTTP Request).

If there is a need to group such functions, namespaces should be used instead:

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

If you need to represent operations but, for some reason (convention), only objects are allowed, you can use classes with a single method (commands):

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
