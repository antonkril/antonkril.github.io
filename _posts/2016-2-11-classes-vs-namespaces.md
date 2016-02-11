---
layout: post
title: Classes VS Namespaces
---

Often classes are used as namespaces for functions:

```php
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

Methods in the class are not connected. They represent alternative scenarios, and will not be called together in one scenario normally.

Such usage of classes is incorrect. If there is need to group such functions, namespaces should be used:

```php
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
