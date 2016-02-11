---
layout: post
title: Classes VS Namespaces
---

Often classes are used as namespaces for functions:

```php
<?php

class UserController
{
  public function listAction()
  {
    // List users
  }
  
  public function deleteAction()
  {
    // Delete user
  }
}
```

Methods in the class are not connected. They represent alternative scenarios, and will not be called together in one scenario.

If there is need to group such functions, namespaces should be used:

```php
<?php
namespace User;

function list()
{
  // List user
}

function delete()
{
  // Delete user
}
```

If you need to represent operations, but, for some reason, only objects are allowed, classes with one method (commands) should be used:

```php
<?php 
namespace User;

class List
{
  public function __invoke() // or execute()
  {
  }
}

class Delete
{
  public function __invoke()
  {
  }
}

```
